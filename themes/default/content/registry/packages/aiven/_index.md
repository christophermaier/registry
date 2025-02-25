---
title: Aiven
meta_desc: Provides an overview of the Aiven Provider for Pulumi.
layout: overview
---

The Aiven provider for Pulumi can be used to provision any of the cloud resources available in [Aiven](https://aiven.io/).
The Aiven provider must be configured with credentials to deploy and update resources in Aiven.

## Example

{{< chooser language "javascript,typescript,python,go,csharp" >}}

{{% choosable language javascript %}}

```javascript
const aiven = require("@pulumi/aiven")

const service = new aiven.Service("my-new-service", {
    project: "my-project",
    cloudName: "google-europe-west1",
    plan:"startup-4",
    serviceName: "my-service",
    serviceType: "grafana",
});
```

{{% /choosable %}}
{{% choosable language typescript %}}

```typescript
import * as aiven from "@pulumi/aiven";

const service = new aiven.Service("my-new-service", {
    project: "my-project",
    cloudName: "google-europe-west1",
    plan:"startup-4",
    serviceName: "my-service",
    serviceType: "grafana",
});
```

{{% /choosable %}}
{{% choosable language python %}}

```python
import pulumi_aiven as aiven

service = aiven.Service("my-service",
  project="my-project",
  cloud_name="google-europe-west1",
  plan="startup-4",
  service_name="my-service",
  service_type="grafana",
)
```

{{% /choosable %}}
{{% choosable language go %}}

```go
import (
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
	aiven "github.com/pulumi/pulumi-aiven/sdk/v4/go/aiven"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		service, err := aiven.NewService(ctx, "test", &aiven.ServiceArgs{
			Project:     pulumi.String("my-project"),
			CloudName:   pulumi.String("google-europe-west1"),
			Plan:        pulumi.String("startup-4"),
			ServiceName: pulumi.String("my-service"),
			ServiceType: pulumi.String("grafana"),
		})
		if err != nil {
			return err
		}

		return nil
	})
}

```

{{% /choosable %}}
{{% choosable language csharp %}}

```csharp
using System.Collections.Generic;
using System.Threading.Tasks;
using Pulumi;
using Pulumi.Aiven;

class Program
{
    static Task Main() =>
        Deployment.Run(() => {
            var service = new Servicev1("test", new Servicev1Args
            {
                Project = "my-project",
                CloudName = "google-europe-west1",
                Plan = "startup-4",
                ServiceName = "my-service",
                ServiceType = "grafana",
            });
        });
}
```

{{% /choosable %}}

{{< /chooser >}}
