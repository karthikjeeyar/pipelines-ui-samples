# pipelines-ui-samples
Contains samples of tasks and pipelineruns to enable UI features 


**Vulnerabilities:**

CVE errors will be displayed in the pipelineRun listview and in the details page, when the pipelinerun contains a results that ends with `SCAN_OUTPUT` string.

Format: `<any_prefix>_SCAN_OUTPUT`

examples: `SCAN_OUTPUT`, `MY_ACS_SCAN_OUTPUT`

PipelineRun:

```
   status:
     results:
       -  name: 'MY_SCAN_OUTPUT'
          value:
            '{"vulnerabilities":{"critical": 0,"high": 9,"medium": 2,"low": 13,"unknown": 0},"unpatched_vulnerabilities": {"critical": 0,"high": 1,"medium": 0,"low":1}}'
```

![image](https://github.com/karthikjeeyar/pipelines-ui-samples/assets/9964343/93553de4-a731-4a31-84bb-53bec9daefb9)

---

**View SBOM:**   
---

Download SBOM and SBOM section will be displayed in the PipelineRun details page, when a taskrun and pipelinerun contains the below outlined results and annotations in taskrun.


![image](https://github.com/karthikjeeyar/pipelines-ui-samples/assets/9964343/8bee502c-4c72-4b6f-8a27-d5f6d022e5c8)


PipelineRun: [Required] 
---
```
status:
    results:
        - name: 'IMAGE_URL'
          value: 'quay.io/repo/image'
```



TaskRun: [Required] 
---
```
metadata:
 annotations: 
    task.output.location: results
    task.results.format: application/text
    task.results.type: external-link  # Optional: This will redirect to external page
    task.results.key: LINK_TO_SBOM
spec: …
status: 
    results:
 name: 'LINK_TO_SBOM'
 type: 'string'
 value: 'quay.io/repo/image:build-8e536-1692702836'

```


_Note: Absence of this annotation will redirect the users to SBOM task run logs page._

```    
task.results.type: external-link  # This will redirect to external page
```
External SBOM redirection link               vs        Internal SBOM redirection link (to task run logs page)
![image](https://github.com/karthikjeeyar/pipelines-ui-samples/assets/9964343/f0dae741-2c8d-4a9a-989c-98f883c3a554)

---
