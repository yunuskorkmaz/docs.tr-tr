---
title: .NET 5 + ' da kullanımdan kalkmış Özellikler
description: .NET 5,0 ve sonraki sürümlerde eski olarak işaretlenen ve SYSLIB Derleyici uyarıları üreten API 'Ler hakkında bilgi edinin.
ms.date: 10/20/2020
ms.openlocfilehash: 336958c93e3db8f66cfbec89476a666e5e103b70
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593311"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="75f3a-103">.NET 5 ' teki kullanımdan kalkmış Özellikler</span><span class="sxs-lookup"><span data-stu-id="75f3a-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="75f3a-104">.NET 5,0 ' den itibaren, yeni olarak eski olarak işaretlenen bazı API 'Ler üzerinde iki yeni özelliği kullanır <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="75f3a-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="75f3a-105"><xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType>Özelliği derleyiciye özel bir tanılama kimliği kullanarak derleme uyarıları oluşturmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="75f3a-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="75f3a-106">Özel KIMLIK, kullanımdan çıkarma uyarısının özellikle ve birbirinden ayrı bir şekilde gizlenmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="75f3a-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="75f3a-107">.NET 5 + kullanımdan kullanım durumunda, özel tanılama KIMLIĞI için biçim `SYSLIBxxxx` .</span><span class="sxs-lookup"><span data-stu-id="75f3a-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="75f3a-108"><xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType>Özelliği, derleyicinin kullanımdan çıkarılması hakkında daha fazla bilgi edinmek için BIR URL bağlantısı içermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="75f3a-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="75f3a-109">Kullanılmayan bir API kullanımı nedeniyle derleme uyarıları veya hatalarıyla karşılaşırsanız, [başvuru](#reference) bölümünde LISTELENEN tanılama kimliği için verilen belirli bir kılavuzu izleyin.</span><span class="sxs-lookup"><span data-stu-id="75f3a-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="75f3a-110">Eski türler veya Üyeler için [standart tanılama kimliği (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) kullanılarak bu kullanımdan *kaldırılmaları uyarıları veya hataları gizlenemedi* ; `SYSLIBxxxx`bunun yerine özel tanılama kimliği değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75f3a-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="75f3a-111">Daha fazla bilgi için bkz. [uyarıları gösterme](#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="75f3a-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="75f3a-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="75f3a-112">Reference</span></span>

<span data-ttu-id="75f3a-113">Aşağıdaki tabloda, `SYSLIBxxxx` .NET 5 + ' de kullanımdan çıkarılan bir dizin verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75f3a-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="75f3a-114">Tanılama KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="75f3a-114">Diagnostic ID</span></span> | <span data-ttu-id="75f3a-115">Description</span><span class="sxs-lookup"><span data-stu-id="75f3a-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="75f3a-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="75f3a-116">SYSLIB0001</span></span>](syslib-warnings/syslib0001.md) | <span data-ttu-id="75f3a-117">UTF-7 kodlaması güvenli değil ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f3a-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="75f3a-118">Bunun yerine UTF-8 kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="75f3a-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="75f3a-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="75f3a-119">SYSLIB0002</span></span>](syslib-warnings/syslib0002.md) | <span data-ttu-id="75f3a-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> çalışma zamanı tarafından kabul edilmez ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f3a-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="75f3a-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="75f3a-121">SYSLIB0003</span></span>](syslib-warnings/syslib0003.md) | <span data-ttu-id="75f3a-122">Kod erişim güvenliği (CAS) çalışma zamanı tarafından desteklenmez veya kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="75f3a-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="75f3a-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="75f3a-123">SYSLIB0004</span></span>](syslib-warnings/syslib0004.md) | <span data-ttu-id="75f3a-124">Kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="75f3a-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="75f3a-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="75f3a-125">SYSLIB0005</span></span>](syslib-warnings/syslib0005.md) | <span data-ttu-id="75f3a-126">Genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="75f3a-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="75f3a-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="75f3a-127">SYSLIB0006</span></span>](syslib-warnings/syslib0006.md) | <span data-ttu-id="75f3a-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> desteklenmez ve atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="75f3a-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="75f3a-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="75f3a-129">SYSLIB0007</span></span>](syslib-warnings/syslib0007.md) | <span data-ttu-id="75f3a-130">Bu şifreleme algoritmasının varsayılan uygulanması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="75f3a-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="75f3a-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="75f3a-131">SYSLIB0008</span></span>](syslib-warnings/syslib0008.md) | <span data-ttu-id="75f3a-132"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>API desteklenmez ve atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="75f3a-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="75f3a-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="75f3a-133">SYSLIB0009</span></span>](syslib-warnings/syslib0009.md) | <span data-ttu-id="75f3a-134"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>Ve <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> yöntemleri desteklenmez ve throw <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="75f3a-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="75f3a-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="75f3a-135">SYSLIB0010</span></span>](syslib-warnings/syslib0010.md) | <span data-ttu-id="75f3a-136">Bazı uzaktan iletişim API 'Leri desteklenmez ve throw <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="75f3a-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="75f3a-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="75f3a-137">SYSLIB0011</span></span>](syslib-warnings/syslib0011.md) | <span data-ttu-id="75f3a-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serileştirme artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f3a-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="75f3a-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="75f3a-139">SYSLIB0012</span></span>](syslib-warnings/syslib0012.md) | <span data-ttu-id="75f3a-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> yalnızca .NET Framework uyumluluk için dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75f3a-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="75f3a-141">Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="75f3a-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="75f3a-142">Uyarıları gizleme</span><span class="sxs-lookup"><span data-stu-id="75f3a-142">Suppress warnings</span></span>

<span data-ttu-id="75f3a-143">Kullanılmayan API 'Leri kullanmanız gerekiyorsa ve `SYSLIBxxxx` tanı hata olarak gösterilmezse, koddaki veya proje dosyanızdaki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75f3a-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="75f3a-144">Kod:</span><span class="sxs-lookup"><span data-stu-id="75f3a-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="75f3a-145">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="75f3a-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="75f3a-146">Uyarıları bu şekilde gizleme yalnızca belirttiğiniz kullanımdan kaldırma uyarılarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="75f3a-146">Suppressing warnings in this way only disables the obsoletion warnings you specify.</span></span> <span data-ttu-id="75f3a-147">Farklı tanılama kimliklerine sahip kullanımdan çıkarma uyarıları dahil diğer uyarıları devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="75f3a-147">It doesn't disable any other warnings, including obsoletion warnings with different diagnostic IDs.</span></span>
