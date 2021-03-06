---
title: "Son değişiklik: genel bütünleştirilmiş kod önbelleği API 'Leri artık kullanılmıyor"
description: GAC ile ilgilenen API 'Lerin başarısız olduğu veya hiçbir işlem gerçekleştirdiği çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 39c7b092b06754a28723693c0147b7ec3a0b705e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257485"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="76a5f-103">Genel bütünleştirilmiş kod önbelleği API 'Leri artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="76a5f-103">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="76a5f-104">.NET Core ve .NET 5 ve sonraki sürümleri, .NET Framework mevcut olan genel derleme önbelleği (GAC) kavramını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="76a5f-104">.NET Core and .NET 5 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="76a5f-105">Bu nedenle, GAC ile ilgilenen tüm .NET Core ve .NET 5 + API 'Leri başarısız olur ya da hiçbir işlem gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="76a5f-105">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="76a5f-106">Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler eski olarak işaretlenir ve `SYSLIB0005` derleme zamanında bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76a5f-106">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="76a5f-107">Bu API 'Ler, .NET 'in gelecek bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="76a5f-107">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="76a5f-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="76a5f-108">Change description</span></span>

<span data-ttu-id="76a5f-109">Aşağıdaki API 'Ler kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="76a5f-109">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="76a5f-110">API</span><span class="sxs-lookup"><span data-stu-id="76a5f-110">API</span></span> | <span data-ttu-id="76a5f-111">İçinde kullanılmıyor olarak işaretlendi...</span><span class="sxs-lookup"><span data-stu-id="76a5f-111">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="76a5f-112">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="76a5f-112">5.0 RC1</span></span> |

<span data-ttu-id="76a5f-113">.NET Framework 2. x-4. x içinde, <xref:System.Reflection.Assembly.GlobalAssemblyCache> `true` SORGULANAN derleme GAC 'den yüklenmişse ve `false` disk üzerindeki farklı bir konumdan yüklenmişse, özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="76a5f-113">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="76a5f-114">.NET Core 2. x-3. x içinde <xref:System.Reflection.Assembly.GlobalAssemblyCache> her zaman döndürülür ve `false` GAC 'Nin .NET Core 'da mevcut olmadığını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="76a5f-114">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="76a5f-115">.NET 5 ve sonraki sürümlerde <xref:System.Reflection.Assembly.GlobalAssemblyCache> özelliği her zaman döndürülür `false` .</span><span class="sxs-lookup"><span data-stu-id="76a5f-115">In .NET 5 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="76a5f-116">Ancak, özellik alıcısı, özelliğe erişmeyi durdurmasına izin veren çağıranlar belirtmek için artık kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="76a5f-116">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="76a5f-117">Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 ve sonraki sürümlerde döndürdüğü için, çalışma zamanı davranışı hakkında belirleyici hale getirmek üzere API 'yi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="76a5f-117">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="76a5f-118">Bu yalnızca derleme zamanı değişir.</span><span class="sxs-lookup"><span data-stu-id="76a5f-118">This is a compile-time only change.</span></span> <span data-ttu-id="76a5f-119">.NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="76a5f-119">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="76a5f-120">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="76a5f-120">Reason for change</span></span>

<span data-ttu-id="76a5f-121">Genel bütünleştirilmiş kod önbelleği (GAC), .NET Core ve .NET 5 ve sonraki sürümlerde bir kavram olarak mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="76a5f-121">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5 and later versions.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="76a5f-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="76a5f-122">Version introduced</span></span>

<span data-ttu-id="76a5f-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="76a5f-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="76a5f-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="76a5f-124">Recommended action</span></span>

- <span data-ttu-id="76a5f-125">Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="76a5f-125">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="76a5f-126">"GAC 'de olmayan bir derleme" ile "bir <xref:System.Reflection.Assembly.GlobalAssemblyCache> " bütünleştirilmiş kod ") arasında seçim yapmak için değeri kullanırsanız, çalışma zamanında Flow 'un bir .NET Core veya .NET 5.0 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="76a5f-126">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="76a5f-127">Kullanılmayan API 'Leri kullanmaya devam etmeniz gerekiyorsa, `SYSLIB0005` koddaki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76a5f-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="76a5f-128">Proje dosyanızda, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakan uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76a5f-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="76a5f-129">Gizleme `SYSLIB0005` yalnızca kullanımdan kaldırma uyarısını devre dışı bırakır <xref:System.Reflection.Assembly.GlobalAssemblyCache> .</span><span class="sxs-lookup"><span data-stu-id="76a5f-129">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="76a5f-130">Başka herhangi bir uyarıyı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="76a5f-130">It does not disable any other warnings.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="76a5f-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="76a5f-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
