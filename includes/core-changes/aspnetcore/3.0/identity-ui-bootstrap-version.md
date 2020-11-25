---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032795"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Kimlik: UI 'nin varsayılan önyükleme sürümü değişti

ASP.NET Core 3,0 ' den başlayarak, kimlik Kullanıcı arabirimi varsayılan önyükleme sürüm 4 ' ü kullanmaktır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`Yöntem çağrısı,`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Yeni davranış

`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`Yöntem çağrısı,`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bootstrap 4 ASP.NET Core 3,0 zaman dilimi sırasında yayınlandı.

#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan kimlik Kullanıcı arabirimini kullanırsanız ve `Startup.ConfigureServices` Aşağıdaki örnekte gösterildiği gibi içine eklediyseniz, bu değişiklikten etkilenmiş olursunuz:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Aşağıdaki eylemlerden birini uygulayın:

- Uygulamanızı [geçiş kılavuzunu](https://getbootstrap.com/docs/4.0/migration)kullanarak önyükleme 4 ' ü kullanacak şekilde geçirin.
- `Startup.ConfigureServices`Bootstrap 3 ' ün kullanımını zorlamak için güncelleştirme. Örnek:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
