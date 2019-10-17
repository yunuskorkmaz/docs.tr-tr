---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393891"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Kimlik: UI 'nin varsayılan önyükleme sürümü değişti

ASP.NET Core 3,0 ' den başlayarak, kimlik Kullanıcı arabirimi varsayılan önyükleme sürüm 4 ' ü kullanmaktır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-0 Yöntem çağrısı, `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);` ile aynı idi

#### <a name="new-behavior"></a>Yeni davranış

@No__t-0 Yöntem çağrısı, `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);` ile aynı

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bootstrap 4 ASP.NET Core 3,0 zaman dilimi sırasında yayınlandı.

#### <a name="recommended-action"></a>Önerilen eylem

Varsayılan kimlik Kullanıcı arabirimini kullanırsanız ve bunu aşağıdaki örnekte gösterildiği gibi `Startup.ConfigureServices` ' a eklediyseniz, bu değişiklikten etkilenmiş olursunuz:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Aşağıdaki eylemlerden birini yapın:

- Uygulamanızı [geçiş kılavuzunu](https://getbootstrap.com/docs/4.0/migration)kullanarak önyükleme 4 ' ü kullanacak şekilde geçirin.
- Bootstrap 3 ' ün kullanımını zorlamak için `Startup.ConfigureServices` güncelleştirin. Örneğin:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
