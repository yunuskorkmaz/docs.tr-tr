---
title: Windows Hizmet Uygulamasında Barındırma
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: cb952cfcd670a790033fbec70de00a4db2541237
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555854"
---
# <a name="hosting-in-a-windows-service-application"></a>Windows Hizmet Uygulamasında Barındırma
Windows Hizmetleri (eski adıyla Windows NT Hizmetleri), uzun süre çalışan bir çalıştırılabilirte canlı olması gereken uygulamalara özellikle uygun bir işlem modeli sağlar ve herhangi bir kullanıcı arabirimi formu görüntülemez. Bir Windows hizmet uygulamasının işlem ömrü, Windows hizmeti uygulamalarını başlatabilmenizi, durdurmanızı ve duraklatmanızı sağlayan hizmet Denetim Yöneticisi (SCM) tarafından yönetilir. Bir Windows hizmeti işlemini bilgisayar başlatıldığında otomatik olarak başlayacak şekilde yapılandırabilirsiniz. Bu, "Always On" uygulamaları için uygun bir barındırma ortamı yapar. Windows hizmeti uygulamaları hakkında daha fazla bilgi için bkz. [Windows hizmeti uygulamaları](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Uzun süre çalışan Windows Communication Foundation (WCF) hizmetlerini barındıran uygulamalar, Windows hizmetleriyle birçok özelliği paylaşır. WCF hizmetleri özellikle kullanıcıyla etkileşime girmeyecek ve bu nedenle herhangi bir kullanıcı arabirimi formu uygulamayan uzun süreli sunucu yürütülebilirlerdir. Bu nedenle, bir Windows hizmeti uygulaması içindeki WCF hizmetleri barındırma, güçlü, uzun süreli ve WCF uygulamaları oluşturmaya yönelik bir seçenektir.  
  
 WCF geliştiricilerinin genellikle Windows hizmet uygulamasının içinde veya Internet Information Services (IIS) ya da Windows Işlem etkinleştirme hizmeti (WAS) barındırma ortamının içinde WCF uygulamalarının barındırılmasına karar vermelidir. Aşağıdaki koşullarda Windows hizmeti uygulamaları kullanmayı göz önünde bulundurmanız gerekir:  
  
- Uygulamanız için açık etkinleştirme gerekir. Örneğin, ilk gelen iletiye yanıt olarak sunucu başlatıldığında uygulamanızın otomatik olarak başlatılması yerine, uygulamanız otomatik olarak başlaması gerektiğinde Windows hizmetlerini kullanmanız gerekir.  
  
- Uygulamanızı barındıran işlem başlatıldığında çalışmaya devam etmelidir. Başlatıldıktan sonra, hizmet Denetim Yöneticisi kullanılarak bir sunucu yöneticisi tarafından açıkça kapatılmadığı sürece bir Windows hizmeti işlemi çalışır durumda kalır. IIS 'de barındırılan uygulamalar, sistem kaynaklarının en iyi şekilde kullanılması için dinamik olarak başlatılabilir ve durdurulmuş olabilir. Barındırma sürecinin kullanım ömrü boyunca açık denetim gerektiren uygulamalar IIS veya WAS yerine Windows hizmetlerini kullanmalıdır.  
  
- WCF hizmetinizin Windows Server 2003 ' de çalışması ve HTTP dışındaki aktarımları kullanması gerekir. Windows Server 2003 ' de, IIS 6,0 barındırma ortamı yalnızca HTTP iletişimi ile kısıtlıdır. Windows hizmeti uygulamaları bu kısıtlamaya tabi değildir ve net. TCP, net. pipe ve net. MSMQ dahil olmak üzere herhangi bir aktarım WCF desteği kullanabilir.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Bir Windows hizmet uygulamasının içinde WCF barındırmak için  
  
1. Bir Windows hizmet uygulaması oluşturun. Ad alanındaki sınıfları kullanarak yönetilen kodda Windows hizmeti uygulamalarını yazabilirsiniz <xref:System.ServiceProcess> . Bu uygulama, öğesinden devralan bir sınıf içermelidir <xref:System.ServiceProcess.ServiceBase> .  
  
2. WCF hizmetlerinin ömrünü Windows hizmet uygulamasının kullanım ömrü ile ilişkilendirin. Genellikle, bir Windows hizmet uygulamasında barındırılan WCF hizmetlerinin barındırma hizmeti başlatıldığında etkin hale gelmesini, barındırma hizmeti durdurulduğunda iletileri dinlemeyi durdurmanız ve WCF hizmeti bir hatayla karşılaştığında barındırma işlemini kapatmanız gerekir. Bu, aşağıdaki gibi gerçekleştirilebilir:  
  
    - <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>Bir veya daha fazla örneğini açmak için geçersiz kılın <xref:System.ServiceModel.ServiceHost> . Tek bir Windows hizmeti uygulaması, bir grup olarak başlatılan ve durduran birden çok WCF hizmetini barındırabilir.  
  
    - <xref:System.ServiceProcess.ServiceBase.OnStop%2A> <xref:System.ServiceModel.Channels.CommunicationObject.Closed> <xref:System.ServiceModel.ServiceHost> Sırasında başlatılan HERHANGI bir çalışan WCF hizmetini çağırmak için geçersiz kılın <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> .  
  
    - Olayına abone olun <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> ve bir <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceProcess.ServiceController> hata durumunda Windows hizmeti uygulamasını kapatmak için sınıfını kullanın.  
  
     WCF hizmetlerini barındıran Windows hizmeti uygulamaları, WCF kullanmayan Windows hizmeti uygulamalarıyla aynı şekilde dağıtılır ve yönetilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess>
- [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Windows Hizmet Konağı](../samples/windows-service-host.md)
- [Hizmet Uygulaması Programlama Mimarisi](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
