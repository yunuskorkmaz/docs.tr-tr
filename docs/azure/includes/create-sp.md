---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: c3746ff92838ac97d8158a0daf0b1a1de07ae024
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071985"
---
.NET uygulamanızın ,.NET için Azure Yönetim Kitaplıklarını kullanabilmek için Azure aboneliğinizde kaynak okumak ve oluşturmak için izinlere ihtiyacı vardır. Bir hizmet ilkesi oluşturun ve bu erişimi sağlamak için uygulamanızı kimlik bilgileriyle çalışacak şekilde yapılandırın. Hizmet sorumluları, yalnızca uygulamanızın çalışması için gereken ayrıcalıkları verdiğiniz kimlikle ilişkili etkileşimli olmayan bir hesap oluşturmanızı sağlar.

İlk olarak, [Azure Bulut BulutU'ya](https://shell.azure.com/bash)giriş yapın. Hizmet sorumlusunun oluşturulmasını istediğiniz aboneliği şu anda kullandığınızı doğrulayın.

```azurecli-interactive
az account show
```

Abonelik bilgileriniz görüntülenir.

```json
{
  "environmentName": "AzureCloud",
  "id": "15dbcfa8-4b93-4c9a-881c-6189d39f04d4",
  "isDefault": true,
  "name": "my-subscription",
  "state": "Enabled",
  "tenantId": "43413cc1-5886-4711-9804-8cfea3d1c3ee",
  "user": {
    "cloudShellID": true,
    "name": "jane@contoso.com",
    "type": "user"
  }
}
```

Doğru aboneliğe giriş yapmadıysanız, yazarak `az account set -s <name or ID of subscription>`doğru aboneliği seçin.

Aşağıdaki komutla hizmet atasını oluşturun:

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

Hizmet temel bilgileri JSON olarak görüntülenir.

```json
{
  "clientId": "b52dd125-9272-4b21-9862-0be667bdf6dc",
  "clientSecret": "ebc6e170-72b2-4b6f-9de2-99410964d2d0",
  "subscriptionId": "ffa52f27-be12-4cad-b1ea-c2c241b6cceb",
  "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

JSON çıktısını daha sonra kullanılmak üzere bir metin düzenleyicisine kopyalayıp yapıştırın.
