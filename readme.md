### 231121
## heatmap 그리는 방법
```
import matplotlib.pyplot as plt
import numpy as np

arr = np.random.standard_normal((10, 10))
print(np.max(arr))

plt.matshow(arr, vmin = np.min(arr), vmax = np.max(arr))
plt.title("test")
plt.xlabel("x", fontsize = 14)
plt.ylabel("y", fontsize = 14)
plt.xticks(np.arange(0.5, 10, 1), ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"])
plt.yticks(np.arange(0.5, 10, 1), ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j"])
plt.colorbar(shrink=0.8, aspect=10)

plt.savefig("heatmap.png")
```
#### ![image](https://github.com/Shin-jongwhan/python_matplotlib/assets/62974484/4b01d802-2f4b-4bfb-bf12-8c77ba538658)
### <br/>

### 다른 예시
### 아래 같은 경우 label 의 이름이 너무 길어서 bbox_inches='tight' 로 자동 조정하게 해주었다. default size 가 지정되지만, 사이즈가 안 맞으면 자동 조정
```
...        # 데이터 가져오는 부분 생략
    plt.figure(figsize = (15,15), dpi=80)    # default size
    plt.matshow(lsMatrix, vmin = np.min(lsMatrix), vmax = np.max(lsMatrix))
    plt.title("cpg_rate")
    #plt.xlabel("sample", fontsize = 14)
    #plt.ylabel("sample", fontsize = 14)
    plt.xticks(np.arange(0.5, len(lsMatrix), 1), lsSample, rotation = 90, fontsize = 10)
    plt.yticks(np.arange(0.5, len(lsMatrix), 1), lsSample, fontsize = 10)
    plt.colorbar(shrink=0.8, aspect=10)
    plt.savefig("{0}/report/samples/cpg_rate_heatmap.png".format(sAnal_dir), bbox_inches='tight',dpi=100)
```
#### ![image](https://github.com/Shin-jongwhan/python_matplotlib/assets/62974484/021f36e3-0e5f-45f8-b746-179c1be69022)
### <br/><br/><br/>

## venn diagram 그리는 방법
### 참고 사이트
- https://blog.naver.com/breezehome50/222353836898
### 다음과 같이 초기화를 해주어야 한다. 아래 예시는 5개의 원이 있는 것이고, 각 영역에 해당하면 1, 해당 안 하면 0 으로 나타내주게 된다.
```
import matplotlib.pyplot as plt
import venn

dicVenn_diagram = dict.fromkeys(list(map(lambda x : "".join(x), list(itertools.product(["0", "1"], repeat = 5)))), 0)       # if repeat is 5, it's like {'00000': 0, '00001': 0, '00010': 0, '00011': 0, '00100': 0, '00101': 0, '00110': 0, '00111': 0, '01000': 0, '01001': 0, '01010': 0, '01011': 0, '01100': 0, '01101': 0, '01110': 0, '01111': 0, '10000': 0, '10001': 0, '10010': 0, '10011': 0, '10100': 0, '10101': 0, '10110': 0, '10111': 0, '11000': 0, '11001': 0, '11010': 0, '11011': 0, '11100': 0, '11101': 0, '11110': 0, '11111': 0}

...

# 해당 영역에 해당하는 경우 dicVenn_diagram 에 추가해준다.
ls = list(map(lambda x : int(x) if int(x) == 0 else 1, ls))     # convert to int to contion
ls = list(map(lambda x : str(x), ls))       # convert to str to join
dicVenn_diagram["".join(ls)] += 1

...

# lsVenn_CX_report_label 은 따로 ["a", "b" ...] 으로 만들어주면 된다.
venn.venn3(dicVenn_diagram, names = lsVenn_CX_report_label)
```
### 그럼 이렇게 나온다.
#### ![image](https://github.com/Shin-jongwhan/python_matplotlib/assets/62974484/8983e44b-7ac1-4a65-97f2-080f2259a483)
