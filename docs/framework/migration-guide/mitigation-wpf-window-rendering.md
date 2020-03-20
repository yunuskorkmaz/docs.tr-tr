---
title: 'Azaltma: WPF Penceresi İşleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457772"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="b0b18-102">Azaltma: WPF Penceresi İşleme</span><span class="sxs-lookup"><span data-stu-id="b0b18-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="b0b18-103">Windows 8 ve üzeri üzerinde çalışan .NET Framework 4.6'da, çoklu monitör senaryosunda tek ekranın dışına uzandığında tüm pencere kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="b0b18-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="b0b18-104">Etki</span><span class="sxs-lookup"><span data-stu-id="b0b18-104">Impact</span></span>

<span data-ttu-id="b0b18-105">Genel olarak, tüm pencereyi kırpmadan birden çok monitör arasında işlemek beklenen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b0b18-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="b0b18-106">Ancak, Windows 7 ve önceki sürümlerde, pencerenin bir bölümünün ikinci monitörde işlenmesi önemli bir performans etkisi olduğundan, tek bir ekranın ötesine geçtiklerinde WPF pencereler kırpılır.</span><span class="sxs-lookup"><span data-stu-id="b0b18-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="b0b18-107">WPF pencerelerini Windows 8 ve üzeri monitörler arasında oluşturmanın kesin etkisi, çok sayıda etkene bağlı olduğundan tam olarak ölçülemez.</span><span class="sxs-lookup"><span data-stu-id="b0b18-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="b0b18-108">Bazı durumlarda, özellikle grafik yoğun uygulamaları çalıştıran ve windows straddling monitörleri olan kullanıcılar için performans üzerinde istenmeyen bir etki yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="b0b18-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="b0b18-109">Diğer durumlarda, .NET Framework sürümlerinde tutarlı bir davranış isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0b18-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="b0b18-110">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="b0b18-110">Mitigation</span></span>

<span data-ttu-id="b0b18-111">Bu değişikliği devre dışı bırakıp, tek bir ekranın ötesine uzandığında WPF penceresini kırpma önceki davranışına geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0b18-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="b0b18-112">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="b0b18-112">There are two ways to do this:</span></span>

- <span data-ttu-id="b0b18-113">`<EnableMultiMonitorDisplayClipping>` Uygulama yapılandırma dosyanızın `<appSettings>` bölümüne öğeyi ekleyerek, Windows 8 veya sonraki uygulamalarda bu davranışı devre dışı layabilir veya etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0b18-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="b0b18-114">Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işleme devre dışı katıyor:</span><span class="sxs-lookup"><span data-stu-id="b0b18-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="b0b18-115">Yapılandırma `<EnableMultiMonitorDisplayClipping>` ayarı iki değerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="b0b18-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="b0b18-116">`true`, işleme sırasında sınırları izlemek için pencerelerin kırpma etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b0b18-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="b0b18-117">`false`, işleme sırasında sınırları izlemek için pencerelerin kırpma devre dışı.</span><span class="sxs-lookup"><span data-stu-id="b0b18-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="b0b18-118"><xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> Uygulama başlangıç `true` noktasında özelliği ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="b0b18-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0b18-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0b18-119">See also</span></span>

- [<span data-ttu-id="b0b18-120">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="b0b18-120">Application compatibility</span></span>](application-compatibility.md)
