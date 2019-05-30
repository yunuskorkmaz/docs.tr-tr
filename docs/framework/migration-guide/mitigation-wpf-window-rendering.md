---
title: 'Azaltma: WPF penceresi işleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf951ecb955a6597757387de1119267ebc58fdc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301458"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="638b1-102">Azaltma: WPF penceresi işleme</span><span class="sxs-lookup"><span data-stu-id="638b1-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="638b1-103">Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir.</span><span class="sxs-lookup"><span data-stu-id="638b1-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="638b1-104">Etki</span><span class="sxs-lookup"><span data-stu-id="638b1-104">Impact</span></span>

<span data-ttu-id="638b1-105">Genel olarak, bir pencerenin tamamını kırpma olmadan birden çok monitör genelinde işleme beklenen bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="638b1-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="638b1-106">Ancak, Windows 7 ve önceki sürümleri, önemli performans etkisi pencereyi ikinci monitörde bir kısmını işlemeye sahip olduğu tek bir görüntü genişlettiğinizde, WPF windows kırpılır.</span><span class="sxs-lookup"><span data-stu-id="638b1-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="638b1-107">Büyük bir dizi faktöre bağlı olduğundan işleme WPF windows, Windows 8 ve üzeri izleyiciler arasında kesin etkisini tam olarak ölçülebilir değil.</span><span class="sxs-lookup"><span data-stu-id="638b1-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="638b1-108">Bazı durumlarda, performans, özellikle izleyiciler payından windows grafik kullanımı yoğun uygulamalar çalıştırmak ve kullanıcılar için istenmeyen bir etkisi hala üretebilir.</span><span class="sxs-lookup"><span data-stu-id="638b1-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="638b1-109">Diğer durumlarda, .NET Framework sürümleri arasında tutarlı bir davranış yalnızca isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="638b1-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="638b1-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="638b1-110">Mitigation</span></span>

<span data-ttu-id="638b1-111">Bu değişiklik devre dışı bırakabilir ve tek bir görüntü genişletir, bir WPF penceresi kırpma, önceki davranışı geri döndür.</span><span class="sxs-lookup"><span data-stu-id="638b1-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="638b1-112">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="638b1-112">There are two ways to do this:</span></span>

- <span data-ttu-id="638b1-113">Ekleyerek `<EnableMultiMonitorDisplayClipping>` öğesine `<appSettings>` bölümü, uygulama yapılandırma dosyasını, devre dışı bırakın veya Windows 8 veya üzeri çalıştıran uygulamalarda bu davranışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="638b1-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="638b1-114">Örneğin, aşağıdaki yapılandırma bölümüne kırpma olmadan işleme devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="638b1-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="638b1-115">`<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı, iki değerden birini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="638b1-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="638b1-116">`true`, kırpma sınırları işleme sırasında izlemek için Windows etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="638b1-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="638b1-117">`false`, işleme sırasında sınırları izlemek için Windows kırpmayı devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="638b1-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="638b1-118">Ayarlayarak <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğini `true` uygulamanın başlangıcında.</span><span class="sxs-lookup"><span data-stu-id="638b1-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="638b1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="638b1-119">See also</span></span>

- [<span data-ttu-id="638b1-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="638b1-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
