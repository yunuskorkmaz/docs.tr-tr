---
ms.openlocfilehash: 35041a035041fd4ad5402e1bc0dd137a74d4f949
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434911"
---
### <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="d84eb-101">Uzaktan iletişim API 'Leri artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="d84eb-101">Remoting APIs are obsolete</span></span>

<span data-ttu-id="d84eb-102">Remoting ile ilgili bazı API 'Ler kullanılmıyor olarak işaretlenir ve `SYSLIB0010` derleme zamanında bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d84eb-102">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="d84eb-103">Bu API 'Ler, .NET 'in gelecek bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d84eb-103">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d84eb-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d84eb-104">Change description</span></span>

<span data-ttu-id="d84eb-105">Aşağıdaki uzaktan iletişim API 'Leri kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="d84eb-105">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="d84eb-106">API</span><span class="sxs-lookup"><span data-stu-id="d84eb-106">API</span></span> | <span data-ttu-id="d84eb-107">İçinde kullanılmıyor olarak işaretlendi...</span><span class="sxs-lookup"><span data-stu-id="d84eb-107">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d84eb-108">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="d84eb-108">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d84eb-109">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="d84eb-109">5.0 RC1</span></span> |

<span data-ttu-id="d84eb-110">.NET Framework 2. x-4. x içinde, <xref:System.MarshalByRefObject.GetLifetimeService> ve <xref:System.MarshalByRefObject.InitializeLifetimeService> yöntemleri .NET uzaktan iletişim ile ilgili örneklerin ömrünü denetler.</span><span class="sxs-lookup"><span data-stu-id="d84eb-110">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="d84eb-111">.NET Core 2. x-3. x içinde, bu yöntemler her zaman çalışma zamanında oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="d84eb-111">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="d84eb-112">.NET 5,0 ve sonraki sürümlerinde, <xref:System.MarshalByRefObject.GetLifetimeService> ve <xref:System.MarshalByRefObject.InitializeLifetimeService> yöntemleri uyarı olarak kullanımdan kalkmıştır, ancak çalışma zamanında bir oluşturma işlemine devam eder <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="d84eb-112">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="d84eb-113">Bu yalnızca derleme zamanı değişir.</span><span class="sxs-lookup"><span data-stu-id="d84eb-113">This is a compile-time only change.</span></span> <span data-ttu-id="d84eb-114">.NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="d84eb-114">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d84eb-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d84eb-115">Reason for change</span></span>

<span data-ttu-id="d84eb-116">[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) , eski bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="d84eb-116">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="d84eb-117">Başka bir işlemdeki (potansiyel olarak farklı bir makinede bile) bir nesnenin örneğini oluşturma ve bu nesneyle normal, işlem içi bir .NET nesne örneği gibi etkileşim kurma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d84eb-117">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="d84eb-118">.NET uzaktan iletişim altyapısı yalnızca .NET Framework 2. x-4. x içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d84eb-118">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="d84eb-119">.NET Core ve .NET 5,0 ve üzeri sürümlerde .NET uzaktan iletişim desteği yoktur ve uzaktan iletişim API 'Leri yok ya da bu çalışma zamanları üzerinde her zaman özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d84eb-119">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="d84eb-120">Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için, Remoting ile ilgili seçili API 'Leri kullanımdan çıkaracağız.</span><span class="sxs-lookup"><span data-stu-id="d84eb-120">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="d84eb-121">Bu API 'Ler tamamen .NET 'in gelecek bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d84eb-121">These APIs may be removed entirely in a future version of .NET.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d84eb-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d84eb-122">Version introduced</span></span>

<span data-ttu-id="d84eb-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d84eb-123">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d84eb-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d84eb-124">Recommended action</span></span>

- <span data-ttu-id="d84eb-125">Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d84eb-125">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="d84eb-126">Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-126">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="d84eb-127">Kullanılmayan API 'Leri kullanmaya devam etmeniz gerekiyorsa, `SYSLIB0010` koddaki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d84eb-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="d84eb-128">Proje dosyanızda, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakan uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d84eb-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="d84eb-129">Gizleme `SYSLIB0010` yalnızca uzak API kullanımdan kaldırma uyarılarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d84eb-129">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="d84eb-130">Başka herhangi bir uyarıyı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d84eb-130">It does not disable any other warnings.</span></span> <span data-ttu-id="d84eb-131">Ayrıca, her zaman atma için sürekli kodlanmış çalışma zamanı davranışını değiştirmez <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="d84eb-131">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="d84eb-132">Kategori</span><span class="sxs-lookup"><span data-stu-id="d84eb-132">Category</span></span>

<span data-ttu-id="d84eb-133">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="d84eb-133">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d84eb-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d84eb-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
