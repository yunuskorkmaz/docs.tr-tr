---
title: "Azaltma: WPF Penceresi İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 032d07b75b96809ff71c7735a267a7351ad25dda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="639e4-102">Azaltma: WPF Penceresi İşleme</span><span class="sxs-lookup"><span data-stu-id="639e4-102">Mitigation: WPF Window Rendering</span></span>
<span data-ttu-id="639e4-103">İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] çok İzleyici senaryosunda tek görüntüleme dışında genişletir, Windows 8 çalıştıran ve üzeri, tüm pencereyi kırpma olmadan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="639e4-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="639e4-104">Etki</span><span class="sxs-lookup"><span data-stu-id="639e4-104">Impact</span></span>  
 <span data-ttu-id="639e4-105">Genel olarak, birden çok monitör kırpma olmadan genelinde tüm pencereyi işleme beklenen bir davranıştır.</span><span class="sxs-lookup"><span data-stu-id="639e4-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="639e4-106">Ancak, Windows 7 ve önceki sürümlerde, önemli performans etkisi pencereyi ikinci monitörde bir kısmını işlemeye sahip olduğu tek bir görüntüleme genişlettiğinizde, WPF windows kırpılır.</span><span class="sxs-lookup"><span data-stu-id="639e4-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>  
  
 <span data-ttu-id="639e4-107">Büyük sayıda etkene bağlı olduğundan işleme WPF windows izleyiciler Windows 8 ve üzeri arasında kesin etkisini tam olarak ölçülebilir değil.</span><span class="sxs-lookup"><span data-stu-id="639e4-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="639e4-108">Bazı durumlarda, özellikle izleyiciler payından windows grafik yoğun uygulamalar çalıştırmak ve kullanıcılar için performans üzerindeki istenmeyen bir etkisini hala üretebilir.</span><span class="sxs-lookup"><span data-stu-id="639e4-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="639e4-109">Diğer durumlarda, yalnızca .NET Framework sürümleri arasında tutarlı bir davranış isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="639e4-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="639e4-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="639e4-110">Mitigation</span></span>  
 <span data-ttu-id="639e4-111">Bu değişikliği devre dışı bırakın ve tek bir görüntüleme genişletir, WPF penceresi kırpma önceki davranışını geri.</span><span class="sxs-lookup"><span data-stu-id="639e4-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="639e4-112">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="639e4-112">There are two ways to do this:</span></span>  
  
-   <span data-ttu-id="639e4-113">Ekleyerek `<EnableMultiMonitorDisplayClipping>` öğesine `<appSettings>` bölüm uygulama yapılandırma dosyası devre dışı bırakmak veya Windows 8 veya sonraki sürümlerde çalışan uygulamalar üzerinde bu davranışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="639e4-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="639e4-114">Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeye devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="639e4-114">For example, the following configuration section disables rendering without clipping:</span></span>  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     <span data-ttu-id="639e4-115">`<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı iki değerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="639e4-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>  
  
    -   <span data-ttu-id="639e4-116">`true`, işleme sırasında sınırları izlemek için windows kırpma etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="639e4-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>  
  
    -   <span data-ttu-id="639e4-117">`false`, işleme sırasında sınırları izlemek için windows kırpmayı devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="639e4-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>  
  
-   <span data-ttu-id="639e4-118">Ayarlayarak <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğine `true` uygulama başlangıçta.</span><span class="sxs-lookup"><span data-stu-id="639e4-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639e4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="639e4-119">See Also</span></span>  
 [<span data-ttu-id="639e4-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="639e4-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
