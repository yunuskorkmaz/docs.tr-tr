---
title: "NETSDK1071: ' ' için bir PackageReference {0} , bir sürümünü belirtti `{1}` ."
description: Bir PackageReference 'ın, bir sürümü olan Framework ile birlikte bulunan bir metapackage sorununu çözme.
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 852232cba04bb93a17872280e10848c2896991ae
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445804"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a>NETSDK1071: çerçeveye dahil edilecek bir metapackage öğesine açıkça sürümlü PackageReference.

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100 SDK ve sonraki sürümleri

.NET SDK, uyarı NETSDK1071 ' ı kullanırken, bir PackageReference içinde belirtilen bir metapackage sürümü ile bir TargetFramework özelliği aracılığıyla örtük olarak başvurulmuş şekilde, bu metapackage sürümü arasında bir sürüm çakışması olabileceğini önerir:

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

TargetFramework, metapackage 'in bir sürümüne otomatik olarak ait olduğundan, sürümler farklı olmaları gerekir.

Bunu çözmek için:

1. .NET Core veya .NET Standard hedeflenirken, `Microsoft.NETCore.App` proje dosyanıza veya proje dosyanızda açık başvuruların önlenmesini göz önünde bulundurun `NETStandard.Library` .
2. .NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, `<RuntimeFrameworkVersion>` doğrudan metapackage 'e başvurmak yerine özelliğini kullanın. Örnek olarak, [bağımsız dağıtımlar](../../deploying/index.md#publish-self-contained) kullanıyorsanız ve 1.0.0 LTS çalışma zamanının belirli bir yaması olması halinde bu durum oluşabilir.
3. .NET Standard hedeflenirken belirli bir sürümüne ihtiyacınız varsa `NetStandard.Library` , `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve bunu ihtiyacınız olan sürüme ayarlayabilirsiniz.
4. .NET Framework projelerine veya ya da eplicitly başvuruları ekleme veya güncelleştirme `Microsoft.NETCore.App` `NETSTandard.Library` . NuGet, `NETStandard.Library` .NET Standard tabanlı bir NuGet paketi kullanırken ihtiyacınız olan herhangi bir sürümü otomatik olarak kurar.
5. `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` .NET Core 2.1 + için bir sürüm belirtmeyin, .NET Core SDK otomatik olarak uygun sürümü seçer. (Note: Bu, yalnızca proje de kullanılıyorsa .NET Core 2,1 hedeflenirken geçerlidir `Microsoft.NET.Sdk.Web` . Bu sorun .NET Core 2,2 SDK 'sında çözüldü.)
6. Uyarının devre dışı olmasını istiyorsanız, devre dışı bırakabilirsiniz:

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
