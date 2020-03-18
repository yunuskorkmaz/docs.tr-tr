---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393891"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Kimlik: UI Varsayılan Bootstrap sürümü değiştirildi

Core 3.0ASP.NETdan başlayarak, Identity UI varsayılan olarak Bootstrap'ın sürüm 4'ü kullanmaz.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Yöntem `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` çağrısı aynıydı`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Yeni davranış

Yöntem `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` çağrısı aynıdır`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bootstrap 4 Core 3.0 ASP.NET zaman dilimi sırasında piyasaya sürüldü.

#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan Kimlik UI'sini kullanırsanız ve aşağıdaki örnekte gösterildiği `Startup.ConfigureServices` gibi eklediyseniz, bu değişiklikten etkilenirsiniz:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Aşağıdaki eylemlerden birini uygulayın:

- [Geçiş kılavuzunu](https://getbootstrap.com/docs/4.0/migration)kullanarak Bootstrap 4'u kullanmak için uygulamanızı geçirin.
- Bootstrap 3 kullanımını zorlamak için güncelleştirin. `Startup.ConfigureServices` Örnek:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
