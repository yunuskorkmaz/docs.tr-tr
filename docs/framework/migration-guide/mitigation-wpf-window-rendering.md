---
title: 'Azaltma: WPF Penceresi İşleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a91839ff12109b84c563dcd3fabd078f75dad9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-wpf-window-rendering"></a>Azaltma: WPF Penceresi İşleme
İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] çok İzleyici senaryosunda tek görüntüleme dışında genişletir, Windows 8 çalıştıran ve üzeri, tüm pencereyi kırpma olmadan oluşturulur.  
  
## <a name="impact"></a>Etki  
 Genel olarak, birden çok monitör kırpma olmadan genelinde tüm pencereyi işleme beklenen bir davranıştır. Ancak, Windows 7 ve önceki sürümlerde, önemli performans etkisi pencereyi ikinci monitörde bir kısmını işlemeye sahip olduğu tek bir görüntüleme genişlettiğinizde, WPF windows kırpılır.  
  
 Büyük sayıda etkene bağlı olduğundan işleme WPF windows izleyiciler Windows 8 ve üzeri arasında kesin etkisini tam olarak ölçülebilir değil. Bazı durumlarda, özellikle izleyiciler payından windows grafik yoğun uygulamalar çalıştırmak ve kullanıcılar için performans üzerindeki istenmeyen bir etkisini hala üretebilir. Diğer durumlarda, yalnızca .NET Framework sürümleri arasında tutarlı bir davranış isteyebilirsiniz.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişikliği devre dışı bırakın ve tek bir görüntüleme genişletir, WPF penceresi kırpma önceki davranışını geri. Bunu yapmak için iki yol vardır:  
  
-   Ekleyerek `<EnableMultiMonitorDisplayClipping>` öğesine `<appSettings>` bölüm uygulama yapılandırma dosyası devre dışı bırakmak veya Windows 8 veya sonraki sürümlerde çalışan uygulamalar üzerinde bu davranışı etkinleştirin. Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeye devre dışı bırakır:  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı iki değerden biri olabilir:  
  
    -   `true`, işleme sırasında sınırları izlemek için windows kırpma etkinleştirmek için.  
  
    -   `false`, işleme sırasında sınırları izlemek için windows kırpmayı devre dışı bırakmak için.  
  
-   Ayarlayarak <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğine `true` uygulama başlangıçta.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
