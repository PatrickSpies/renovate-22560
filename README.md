# helmfile: support dependencies of a release

[renovatebot/renovate#22560](https://github.com/renovatebot/renovate/discussions/22560)

Install and run renovate.

## Current result
Renovate detects only 1 dependency:
```json
 INFO: Dependency extraction complete (repository=renovate-22560, baseBranch=main)
       "stats": {
         "managers": {"helmfile": {"fileCount": 1, "depCount": 1}},
         "total": {"fileCount": 1, "depCount": 1}
       }
```
```json
{
	"helmfile": [
		{
			"datasource": "helm",
			"deps": [
				{
					"currentValue": "1.0.0",
					"currentVersion": "1.0.0",
					"depName": "serviceaccount",
					"fixedVersion": "1.0.0",
					"packageName": "serviceaccount",
					"registryUrl": "https://ameijer.github.io/k8s-as-helm",
					"registryUrls": [
						"https://ameijer.github.io/k8s-as-helm/"
					],
					"sourceUrl": "https://github.com/ameijer/k8s-as-helm",
					"versioning": "helm",
					"warnings": [],
					"updates": []
				}
			],
			"packageFile": "helmfile.yaml"
		}
	]
}
```

## Expected result
Renovate should detect both dependencies, e.g.:
```json
 INFO: Dependency extraction complete (repository=renovate-22560, baseBranch=main)
       "stats": {
         "managers": {"helmfile": {"fileCount": 1, "depCount": 2}},
         "total": {"fileCount": 1, "depCount": 2}
       }
```
```json
{
	"helmfile": [
		{
			"datasource": "helm",
			"deps": [
				{
					"currentValue": "1.0.0",
					"currentVersion": "1.0.0",
					"depName": "serviceaccount",
					"fixedVersion": "1.0.0",
					"packageName": "serviceaccount",
					"registryUrl": "https://ameijer.github.io/k8s-as-helm",
					"registryUrls": [
						"https://ameijer.github.io/k8s-as-helm/"
					],
					"sourceUrl": "https://github.com/ameijer/k8s-as-helm",
					"versioning": "helm",
					"warnings": [],
					"updates": []
				},
				{
					"currentValue": "1.0.0",
					"currentVersion": "1.0.0",
					"depName": "clusterrolebinding",
					"fixedVersion": "1.0.0",
					"packageName": "clusterrolebinding",
					"registryUrl": "https://ameijer.github.io/k8s-as-helm",
					"registryUrls": [
						"https://ameijer.github.io/k8s-as-helm/"
					],
					"sourceUrl": "https://github.com/ameijer/k8s-as-helm",
					"versioning": "helm",
					"warnings": [],
					"updates": []
				}
			],
			"packageFile": "helmfile.yaml"
		}
	]
}
```