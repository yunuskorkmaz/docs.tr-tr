---
ms.openlocfilehash: 959d8cb6d3e52916f6777054f3e9b327dc8edb4e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434974"
---
### <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="e62ae-101">Genel bütünleştirilmiş kod önbelleği API 'Leri artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="e62ae-101">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="e62ae-102">.NET Core ve .NET 5,0 ve sonraki sürümleri, .NET Framework bulunan genel derleme önbelleği (GAC) kavramını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e62ae-102">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="e62ae-103">Bu nedenle, GAC ile ilgilenen tüm .NET Core ve .NET 5 + API 'Leri başarısız olur ya da hiçbir işlem gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e62ae-103">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="e62ae-104">Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler eski olarak işaretlenir ve `SYSLIB0005` derleme zamanında bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e62ae-104">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="e62ae-105">Bu API 'Ler, .NET 'in gelecek bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e62ae-105">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e62ae-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e62ae-106">Change description</span></span>

<span data-ttu-id="e62ae-107">Aşağıdaki API 'Ler kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="e62ae-107">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="e62ae-108">API</span><span class="sxs-lookup"><span data-stu-id="e62ae-108">API</span></span> | <span data-ttu-id="e62ae-109">İçinde kullanılmıyor olarak işaretlendi...</span><span class="sxs-lookup"><span data-stu-id="e62ae-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="e62ae-110">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="e62ae-110">5.0 RC1</span></span> |

<span data-ttu-id="e62ae-111">.NET Framework 2. x-4. x içinde, <xref:System.Reflection.Assembly.GlobalAssemblyCache> `true` SORGULANAN derleme GAC 'den yüklenmişse ve `false` disk üzerindeki farklı bir konumdan yüklenmişse, özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="e62ae-111">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="e62ae-112">.NET Core 2. x-3. x içinde <xref:System.Reflection.Assembly.GlobalAssemblyCache> her zaman döndürülür ve `false` GAC 'Nin .NET Core 'da mevcut olmadığını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="e62ae-112">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e62ae-113">.NET 5,0 ve sonraki sürümlerinde, <xref:System.Reflection.Assembly.GlobalAssemblyCache> özelliği her zaman döndürülür `false` .</span><span class="sxs-lookup"><span data-stu-id="e62ae-113">In .NET 5.0 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="e62ae-114">Ancak, özellik alıcısı, özelliğe erişmeyi durdurmasına izin veren çağıranlar belirtmek için artık kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e62ae-114">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="e62ae-115">Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5,0 ve sonraki sürümlerde döndürdüğü için, çalışma zamanı davranışı hakkında belirleyici hale getirmek üzere API 'yi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e62ae-115">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5.0 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e62ae-116">Bu yalnızca derleme zamanı değişir.</span><span class="sxs-lookup"><span data-stu-id="e62ae-116">This is a compile-time only change.</span></span> <span data-ttu-id="e62ae-117">.NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e62ae-117">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e62ae-118">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e62ae-118">Reason for change</span></span>

<span data-ttu-id="e62ae-119">Genel bütünleştirilmiş kod önbelleği (GAC), .NET Core ve .NET 5,0 ve sonraki sürümlerde bir kavram olarak mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="e62ae-119">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5.0 and later versions.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e62ae-120">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e62ae-120">Version introduced</span></span>

<span data-ttu-id="e62ae-121">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e62ae-121">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e62ae-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e62ae-122">Recommended action</span></span>

- <span data-ttu-id="e62ae-123">Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e62ae-123">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="e62ae-124">"GAC 'de olmayan bir derleme" ile "bir <xref:System.Reflection.Assembly.GlobalAssemblyCache> " bütünleştirilmiş kod ") arasında seçim yapmak için değeri kullanırsanız, çalışma zamanında Flow 'un bir .NET Core veya .NET 5.0 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="e62ae-124">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="e62ae-125">Kullanılmayan API 'Leri kullanmaya devam etmeniz gerekiyorsa, `SYSLIB0005` koddaki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e62ae-125">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="e62ae-126">Proje dosyanızda, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakan uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e62ae-126">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="e62ae-127">Gizleme `SYSLIB0005` yalnızca kullanımdan kaldırma uyarısını devre dışı bırakır <xref:System.Reflection.Assembly.GlobalAssemblyCache> .</span><span class="sxs-lookup"><span data-stu-id="e62ae-127">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="e62ae-128">Başka herhangi bir uyarıyı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e62ae-128">It does not disable any other warnings.</span></span>

#### <a name="category"></a><span data-ttu-id="e62ae-129">Kategori</span><span class="sxs-lookup"><span data-stu-id="e62ae-129">Category</span></span>

<span data-ttu-id="e62ae-130">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="e62ae-130">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e62ae-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e62ae-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
