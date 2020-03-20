---
title: Analitik İzlemeyi Dinamik Olarak Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674952"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Analitik İzlemeyi Dinamik Olarak Etkinleştirme
Windows işletim sistemiyle birlikte gönderi yapan araçları kullanarak, Windows için Olay İzleme (ETW) kullanarak dinamik olarak izleme yi etkinleştirebilir veya devre dışı kullanabilirsiniz. Tüm [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Windows Communication Foundation (WCF) hizmetleri için, uygulamanın Web.config dosyasını değiştirmeden veya hizmeti yeniden başlatmadan analitik izleme etkinleştirilebilir ve dinamik olarak devre dışı bırakılır. Bu, izleme olaylarını yayıp bırakan uygulamanın rahatsız edilmeden kalmasını sağlar.  
  
 WCF izleme seçenekleri benzer şekilde yapılandırılabilir. Örneğin, uygulamayı rahatsız etmeden önem düzeyini **Hatadan** **Bilgiye** değiştirebilirsiniz. Bu aşağıdaki araçlar kullanılarak yapılabilir:  
  
- **Logman** – Verileri yapılandırmak, denetlemek ve sorgulamak için bir komut satırı aracıdır. Daha fazla bilgi için [Logman Create Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10)) ve [Logman Update Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10))'e bakın.  
  
- **EventViewer** - İzleme sonuçlarını görüntülemek için Windows grafik yönetim aracı. Daha fazla bilgi için Windows ve [Olay Görüntüleyicisi](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)) [için WCF Hizmetleri ve Olay İzleme'ye](../../samples/wcf-services-and-event-tracing-for-windows.md) bakın.  
  
- **Perfmon** – Sayaçları ve izlemenin performans üzerindeki etkilerini izlemek için sayaçları kullanan Windows grafik yönetim aracı. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11))  
  
### <a name="keywords"></a>Anahtar sözcükler  
 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> Sınıfı kullanırken,.NET Framework izleme iletileri genellikle önem düzeyine (örneğin, Hata, Uyarı ve Bilgi) göre filtrelenir. ETW önem düzeyi kavramını destekler, ancak anahtar kelimeler kullanarak yeni, esnek bir filtre mekanizması sunar. Anahtar kelimeler, olayları izlemenin bu olayın ne anlama geldiğini anlama sınaizin verdiği rasgele metinsel değerlerdir.  
  
 WCF analitik izleme için, her izleme olayının iki tür anahtar kelime türü vardır. İlk olarak, her olayın bir veya daha fazla senaryo anahtar kelimeleri vardır. Bu anahtar kelimeler, bu olayın desteklemek için tasarlandığı senaryoları gösterir. Her biri aşağıdaki tabloda gösterildiği gibi belirli bir amaç için tasarlanmış üç senaryo anahtar kelime vardır. Anahtar kelimeler kullanarak filtreleme, WCF hizmetini rahatsız etmeden dinamik olarak değiştirilebilir. Bu, geçerli izleme senaryonuzu ve topladığınız izleme bilgilerinin miktarını dinamik olarak değiştirebileceğiniz anlamına gelir. Örneğin, İzleme Olayı `HealthMonitoring` `Troubleshooting` parçalı'nı değiştirebilir ve artırabilirsiniz.  
  
|Anahtar kelime|Açıklama|  
|-------------|-----------------|  
|`HealthMonitoring`|Çok hafif, hizmetinizin etkinliğini izlemenize olanak tanıyan en az izleme.|  
|`EndToEndMonitoring`|İleti akışının izlenmesini desteklemek için kullanılan olaylar.|  
|`Troubleshooting`|WCF'nin genişletilebilirlik noktaları etrafında daha ayrıntılı olaylar.|  
  
 İkinci anahtar kelime grubu ,NET Framework'ün hangi bileşeninin olayı yaydığı tanımlanır.  
  
|Anahtar kelime|Açıklama|  
|-------------|-----------------|  
|`UserEvents`|.NET Framework tarafından değil, kullanıcı kodu tarafından yayılan olaylar.|  
|`ServiceModel`|WCF çalışma zamanı tarafından yayılan olaylar.|  
|`ServiceHost`|Hizmet barındırıcısı tarafından yayılan olaylar.|  
|`WCFMessageLogging`|WCF ileti günlüğe kaydetme olayları.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri ve Windows için Olay İzleme](../../samples/wcf-services-and-event-tracing-for-windows.md)
