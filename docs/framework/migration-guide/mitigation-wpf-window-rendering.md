---
title: 'Azaltma: WPF Penceresi İşleme'
description: Windows 8 veya üzeri sürümlerde çalışan .NET Framework 4,6 ' de WPF pencere işleme etkisi ve hafifletme hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475339"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="96dd4-103">Azaltma: WPF Penceresi İşleme</span><span class="sxs-lookup"><span data-stu-id="96dd4-103">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="96dd4-104">Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="96dd4-104">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="96dd4-105">Etki</span><span class="sxs-lookup"><span data-stu-id="96dd4-105">Impact</span></span>

<span data-ttu-id="96dd4-106">Genel olarak, bir pencerenin tamamını kırpmadan birden çok monitörde işlemek beklenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="96dd4-106">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="96dd4-107">Bununla birlikte, Windows 7 ve önceki sürümlerde WPF pencereleri, ikinci monitörde pencerenin bir kısmını işlemek önemli bir performans etkisi sağladığından, tek bir ekranı genişlediklerinde kırpılır.</span><span class="sxs-lookup"><span data-stu-id="96dd4-107">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="96dd4-108">WPF pencerelerini Windows 8 ve üzeri sürümlerde izlemenin kesin etkileri, çok sayıda etkene bağlı olduğundan tam olarak nicelik yapamaz.</span><span class="sxs-lookup"><span data-stu-id="96dd4-108">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="96dd4-109">Bazı durumlarda, özellikle grafik yoğun uygulamalar çalıştıran ve Windows tarafından ayarlanan izleyiciler bulunan kullanıcılar için performans üzerinde istenmeyen bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="96dd4-109">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="96dd4-110">Diğer durumlarda, .NET Framework sürümler arasında tutarlı bir davranış de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96dd4-110">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="96dd4-111">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="96dd4-111">Mitigation</span></span>

<span data-ttu-id="96dd4-112">Bu değişikliği devre dışı bırakabilir ve tek bir görüntüleme ötesinde bir WPF penceresinin kırpılması için önceki davranışa geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="96dd4-112">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="96dd4-113">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="96dd4-113">There are two ways to do this:</span></span>

- <span data-ttu-id="96dd4-114">`<EnableMultiMonitorDisplayClipping>` `<appSettings>` Uygulama yapılandırma dosyanızın bölümüne öğesi eklenerek, Windows 8 veya üzeri sürümlerde çalışan uygulamalarda bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96dd4-114">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="96dd4-115">Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeyi devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="96dd4-115">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="96dd4-116">`<EnableMultiMonitorDisplayClipping>`Yapılandırma ayarı iki değerden birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="96dd4-116">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="96dd4-117">`true`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="96dd4-117">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="96dd4-118">`false`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="96dd4-118">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="96dd4-119"><xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A>Uygulama başlangıcında özelliğini olarak ayarlayarak `true` .</span><span class="sxs-lookup"><span data-stu-id="96dd4-119">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="96dd4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96dd4-120">See also</span></span>

- [<span data-ttu-id="96dd4-121">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="96dd4-121">Application compatibility</span></span>](application-compatibility.md)
