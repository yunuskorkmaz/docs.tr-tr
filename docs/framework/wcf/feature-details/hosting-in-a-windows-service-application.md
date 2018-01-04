---
title: "Windows Hizmet Uygulamasında Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1a39162097c21f20c0dd04f3911442602871436
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-a-windows-service-application"></a>Windows Hizmet Uygulamasında Barındırma
(Daha önce Windows NT Hizmetleri bilinen) Windows hizmetleri sağlayan bir işlem modeli özellikle uzun süre çalışan yürütülebilir dosya içinde bulunmalıdır ve herhangi bir kullanıcı arabirimi biçimi gösterme uygulamalar için uygundur. Hizmet uygulaması başlangıç olanak tanıyan, hizmet denetimi yöneticisi tarafından (SCM), yönetilen bir Windows işlem ömrü durdurun ve Windows hizmeti uygulamalarını duraklatma. Bir Windows hizmet işlemi "her zaman açık" uygulamalar için uygun bir barındırma ortamı kolaylaştırarak bilgisayar başlatıldığında otomatik olarak başlayacak şekilde yapılandırabilirsiniz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows hizmet uygulamaları, bkz: [Windows hizmet uygulamaları](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Uzun süre çalışan barındıran uygulamalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, Windows Hizmetleri ile birçok özelliği paylaşımı. Özellikle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetlerdir doğrudan kullanıcıyla etkileşim değil ve bu nedenle herhangi bir kullanıcı arabirimi biçimi uygulamak uzun süre çalışan sunucu yürütülebilir. Bu nedenle, barındırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services Windows hizmeti uygulaması içinde güçlü, uzun süreli oluşturmak için bir seçenek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
 Genellikle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geliştiriciler mi barındırmak karar gerekir kendi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir Windows hizmet uygulaması içinde veya Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) bir barındırma ortamı içinde uygulama. Windows hizmet uygulamaları aşağıdaki koşullarda kullanmayı düşünmeniz gerekir:  
  
-   Uygulamanızın açık etkinleştirme gerektirir. Örneğin, dinamik olarak ilk gelen iletisine yanıt olarak başlatılmakta yerine sunucu başlatıldığında yapılacak uygulamanızı otomatik olarak başlamalıdır olduğunda Windows Hizmetleri kullanmanız gerekir.  
  
-   Uygulamanızı barındıran işlemin başlatıldığında çalışan kalmalıdır. Başladıktan sonra bir Windows hizmet işlemi sürece çalışmaya devam açıkça Kapatma Hizmet Denetim Yöneticisi'ni kullanarak bir sunucu yöneticisi tarafından. IIS ya da WAS içinde barındırılan uygulamalar başlatıldı ve sistem kaynakları en iyi kullanılmasını sağlamak için dinamik olarak durduruldu. Kendi barındırma işlemi ömrü üzerinde açık denetim gerektiren uygulamalar, IIS ya da WAS yerine Windows Hizmetleri kullanmanız gerekir.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmeti Windows Server 2003'te çalıştırın ve HTTP dışında taşımaları kullanın. Windows Server 2003'te [!INCLUDE[iis601](../../../../includes/iis601-md.md)] barındırma ortamı yalnızca HTTP iletişimi için kısıtlanmış. Windows hizmet uygulamaları bu kısıtlama tabi değildir ve herhangi bir aktarım kullanabilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] net.tcp net.pipe ve net.msmq çeşitli destekler.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Windows hizmet uygulaması içinde WCF barındırmak için  
  
1.  Windows hizmet uygulaması oluşturun. Windows hizmet uygulamaları sınıflarda kullanarak yönetilen kod yazabilirsiniz <xref:System.ServiceProcess> ad alanı. Bu uygulama öğesinden devralınan bir sınıf içermelidir <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Ömrü bağlantı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows ömrü Hizmetleri hizmet uygulaması. Genellikle, istediğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetler bir Windows hizmet uygulamasında barındırma hizmeti başlatıldığında etkinleşir barındırılan, Dur barındırma hizmeti durdurulduğunda iletiler için dinleme ve ne zaman işlem barındırma aşağı bilgisayarı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet hatayla karşılaşıyor. Bu şekilde gerçekleştirilebilir:  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> bir veya daha fazla örneğini açmayı <xref:System.ServiceModel.ServiceHost>. Tek bir Windows hizmeti uygulama birden çok barındırabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] başlatma ve durdurma grup olarak hizmetler.  
  
    -   Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStop%2A> çağırmak için <xref:System.ServiceModel.Channels.CommunicationObject.Closed> üzerinde <xref:System.ServiceModel.ServiceHost> tüm çalışan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sırasında başlatılan Hizmetleri <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Abone <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> olayı <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceProcess.ServiceController> hata durumunda Windows hizmet uygulaması kapatmak üzere sınıfı.  
  
     Windows hizmet uygulamaları barındıran [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri dağıtılan ve hale Windows hizmet uygulamaları kullanımı gibi aynı şekilde yönetilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceProcess>  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Nasıl yapılır: Yönetilen Bir Windows Hizmetinde Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Windows Hizmet Konağı](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Hizmet Uygulaması Programlama Mimarisi](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
