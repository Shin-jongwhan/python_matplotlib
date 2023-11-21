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
...
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

