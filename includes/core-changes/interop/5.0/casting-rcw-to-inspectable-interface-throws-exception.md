---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438055"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="4cb36-101">Bir arabirime RCW atama `InterfaceIsIInspectable` PlatformNotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="4cb36-101">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="4cb36-102">Çalışma zamanı çağrılabilir sarmalayıcı (RCW) ' i şu şekilde işaretlenen bir arabirime atama, <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> bir oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="4cb36-102">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="4cb36-103">Bu değişiklik, [.net 'Ten WinRT desteğinin kaldırılmasına](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)yönelik bir izdir.</span><span class="sxs-lookup"><span data-stu-id="4cb36-103">This change is a follow up to the [removal of WinRT support from .NET](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4cb36-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4cb36-104">Version introduced</span></span>

<span data-ttu-id="4cb36-105">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="4cb36-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="4cb36-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4cb36-106">Change description</span></span>

<span data-ttu-id="4cb36-107">.NET 5,0 Preview 6 ' dan önceki .NET sürümlerinde, bir RCW 'yı beklenen şekilde işaretlenen bir arabirime atama <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> .</span><span class="sxs-lookup"><span data-stu-id="4cb36-107">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="4cb36-108">.NET 5,0 önizlemeleri 6-8 ve RC1 'de, bir RCW 'ı bir arabirime başarıyla çevirebilirsiniz <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> .</span><span class="sxs-lookup"><span data-stu-id="4cb36-108">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="4cb36-109">Ancak, çalışma zamanındaki temeldeki destek [.net 5,0 Preview 6 ' da kaldırıldığından](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net), arabirim üzerinde Yöntemler yürüttüğünüzde erişim ihlalleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cb36-109">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

<span data-ttu-id="4cb36-110">.NET 5,0 RC2 ve sonraki sürümlerinde, bir RCW 'yı olarak işaretlenen bir arabirime atama, <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> atama zamanında oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="4cb36-110">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4cb36-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4cb36-111">Reason for change</span></span>

<span data-ttu-id="4cb36-112">Desteği <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> [önceki bir .NET 5,0 önizlemesinde kaldırılmıştır](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="4cb36-112">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span> <span data-ttu-id="4cb36-113">Ancak, bir arabirime atama <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> yanlışlıkla daha fazla baktık.</span><span class="sxs-lookup"><span data-stu-id="4cb36-113">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="4cb36-114">Çalışma zamanındaki temel alınan destek artık mevcut olmadığından, bir oluşturma düzgün bir <xref:System.PlatformNotSupportedException> hata yolu sunar.</span><span class="sxs-lookup"><span data-stu-id="4cb36-114">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="4cb36-115">Özel durum oluşturmak, bu özelliğin artık desteklenmediğini daha fazla bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4cb36-115">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4cb36-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4cb36-116">Recommended action</span></span>

- <span data-ttu-id="4cb36-117">Arabirimi bir Windows çalışma zamanı meta verileri (WinMD) dosyasında tanımlayabiliyorsanız bunun yerine C#/wınrt aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4cb36-117">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="4cb36-118">Aksi takdirde, arabirimini yerine olarak işaretleyin <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ve bu yöntemlerin arayüzünün başına üç sözde giriş ekleyin <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> .</span><span class="sxs-lookup"><span data-stu-id="4cb36-118">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="4cb36-119">Aşağıdaki kod parçacığı bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cb36-119">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a><span data-ttu-id="4cb36-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="4cb36-120">Category</span></span>

<span data-ttu-id="4cb36-121">Interop</span><span class="sxs-lookup"><span data-stu-id="4cb36-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4cb36-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4cb36-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->
