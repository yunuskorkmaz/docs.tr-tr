---
title: Mayı WPF Pencere Işleme
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789794"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="4ea01-102">Mayı WPF Pencere Işleme</span><span class="sxs-lookup"><span data-stu-id="4ea01-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="4ea01-103">Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="4ea01-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="4ea01-104">Etki</span><span class="sxs-lookup"><span data-stu-id="4ea01-104">Impact</span></span>

<span data-ttu-id="4ea01-105">Genel olarak, bir pencerenin tamamını kırpmadan birden çok monitörde işlemek beklenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="4ea01-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="4ea01-106">Bununla birlikte, Windows 7 ve önceki sürümlerde WPF pencereleri, ikinci monitörde pencerenin bir kısmını işlemek önemli bir performans etkisi sağladığından, tek bir ekranı genişlediklerinde kırpılır.</span><span class="sxs-lookup"><span data-stu-id="4ea01-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="4ea01-107">WPF pencerelerini Windows 8 ve üzeri sürümlerde izlemenin kesin etkileri, çok sayıda etkene bağlı olduğundan tam olarak nicelik yapamaz.</span><span class="sxs-lookup"><span data-stu-id="4ea01-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="4ea01-108">Bazı durumlarda, özellikle grafik yoğun uygulamalar çalıştıran ve Windows tarafından ayarlanan izleyiciler bulunan kullanıcılar için performans üzerinde istenmeyen bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ea01-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="4ea01-109">Diğer durumlarda, .NET Framework sürümler arasında tutarlı bir davranış de isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea01-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="4ea01-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="4ea01-110">Mitigation</span></span>

<span data-ttu-id="4ea01-111">Bu değişikliği devre dışı bırakabilir ve tek bir görüntüleme ötesinde bir WPF penceresinin kırpılması için önceki davranışa geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="4ea01-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="4ea01-112">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="4ea01-112">There are two ways to do this:</span></span>

- <span data-ttu-id="4ea01-113">Uygulama yapılandırma dosyanızın `<EnableMultiMonitorDisplayClipping>` `<appSettings>` bölümüne öğesi eklenerek, Windows 8 veya üzeri sürümlerde çalışan uygulamalarda bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea01-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="4ea01-114">Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeyi devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="4ea01-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="4ea01-115">`<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı iki değerden birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="4ea01-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="4ea01-116">`true`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4ea01-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="4ea01-117">`false`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="4ea01-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="4ea01-118">Uygulama başlangıcında <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğini olarak `true` ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="4ea01-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ea01-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea01-119">See also</span></span>

- [<span data-ttu-id="4ea01-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="4ea01-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
