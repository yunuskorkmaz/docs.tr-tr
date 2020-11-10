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
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="ca992-103">NETSDK1071: çerçeveye dahil edilecek bir metapackage öğesine açıkça sürümlü PackageReference.</span><span class="sxs-lookup"><span data-stu-id="ca992-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="ca992-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="ca992-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="ca992-105">.NET SDK, uyarı NETSDK1071 ' ı kullanırken, bir PackageReference içinde belirtilen bir metapackage sürümü ile bir TargetFramework özelliği aracılığıyla örtük olarak başvurulmuş şekilde, bu metapackage sürümü arasında bir sürüm çakışması olabileceğini önerir:</span><span class="sxs-lookup"><span data-stu-id="ca992-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="ca992-106">TargetFramework, metapackage 'in bir sürümüne otomatik olarak ait olduğundan, sürümler farklı olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca992-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="ca992-107">Bunu çözmek için:</span><span class="sxs-lookup"><span data-stu-id="ca992-107">To resolve this:</span></span>

1. <span data-ttu-id="ca992-108">.NET Core veya .NET Standard hedeflenirken, `Microsoft.NETCore.App` proje dosyanıza veya proje dosyanızda açık başvuruların önlenmesini göz önünde bulundurun `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="ca992-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="ca992-109">.NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, `<RuntimeFrameworkVersion>` doğrudan metapackage 'e başvurmak yerine özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca992-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="ca992-110">Örnek olarak, [bağımsız dağıtımlar](../../deploying/index.md#publish-self-contained) kullanıyorsanız ve 1.0.0 LTS çalışma zamanının belirli bir yaması olması halinde bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ca992-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="ca992-111">.NET Standard hedeflenirken belirli bir sürümüne ihtiyacınız varsa `NetStandard.Library` , `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve bunu ihtiyacınız olan sürüme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca992-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="ca992-112">.NET Framework projelerine veya ya da eplicitly başvuruları ekleme veya güncelleştirme `Microsoft.NETCore.App` `NETSTandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="ca992-112">Don't eplicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="ca992-113">NuGet, `NETStandard.Library` .NET Standard tabanlı bir NuGet paketi kullanırken ihtiyacınız olan herhangi bir sürümü otomatik olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="ca992-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="ca992-114">`Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` .NET Core 2.1 + için bir sürüm belirtmeyin, .NET Core SDK otomatik olarak uygun sürümü seçer.</span><span class="sxs-lookup"><span data-stu-id="ca992-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="ca992-115">(Note: Bu, yalnızca proje de kullanılıyorsa .NET Core 2,1 hedeflenirken geçerlidir `Microsoft.NET.Sdk.Web` .</span><span class="sxs-lookup"><span data-stu-id="ca992-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="ca992-116">Bu sorun .NET Core 2,2 SDK 'sında çözüldü.)</span><span class="sxs-lookup"><span data-stu-id="ca992-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="ca992-117">Uyarının devre dışı olmasını istiyorsanız, devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca992-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
