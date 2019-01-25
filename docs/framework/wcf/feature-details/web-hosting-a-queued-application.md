---
title: Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: 957a97c263f44302b66b6fb57b8330f63a178fa1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700214"
---
# <a name="web-hosting-a-queued-application"></a>Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
Windows İşlem Etkinleştirme Hizmeti (WAS) etkinleştirme ve uygulamaları Windows Communication Foundation (WCF) hizmetlerini barındırmak içeren çalışan işlemleri yaşam süresini yönetir. WAS işlem modelini genelleştirir [!INCLUDE[iis601](../../../../includes/iis601-md.md)] HTTP sunucusu, HTTP bağımlılığını kaldırarak işlem modeli. Bu, hem HTTP hem de net.msmq ve ileti tabanlı etkinleştirme destekleyen ve belirli bir bilgisayardaki uygulamaları, çok sayıda konak imkanı barındırma ortamında msmq.formatname gibi HTTP olmayan protokolleri kullanmak WCF hizmetleri sağlar.  
  
 OLAN bir veya daha fazla ileti bir uygulama tarafından kullanılan kuyrukların yerleştirildiğinde, kuyruğa alınmış bir uygulamayı etkinleştirir bir Message Queuing (MSMQ) etkinleştirmesi hizmeti içerir. MSMQ Etkinleştirme hizmeti varsayılan olarak otomatik olarak başlatılan bir NT hizmetidir.  
  
 WAS ve aboneliğin avantajları hakkında daha fazla bilgi için bkz. [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). MSMQ hakkında daha fazla bilgi için bkz: [kuyruklar genel bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Kuyruk WAS içinde adresleme  
 Uygulamaları Tekdüzen Kaynak Tanımlayıcısı (URI) adreslerine sahip oldu. Uygulama adresine sahip iki bölümden: bir taban URI öneki ve uygulamaya özgü, göreli (yol) adresi. Bu iki bölümden birlikte katıldığında bir uygulama için dış adresini sağlayın. Taban URI öneki site bağlamayı oluşturulur ve örneğin, "net.msmq://localhost", "msmq.formatname://localhost" veya "NET.TCP://localhost" site altındaki tüm uygulamalar için kullanılır. Uygulama adresleri ardından uzamayan uygulamaya özgü yolu parçaları yararlanarak (örneğin "/ applicationOne") ve bunları temel URI'nin sonuna ekleme önek tam uygulamayı URI, örneğin, gelmesi "net.msmq://localhost/applicationOne".  
  
 MSMQ Etkinleştirme hizmeti, MSMQ Etkinleştirme hizmeti iletileri de izlemeniz gerekir sıranın eşleştirmek için uygulama URI'sini kullanır. MSMQ Etkinleştirme hizmeti başladığında alacak şekilde yapılandırılır ve bunları iletileri izler, bilgisayardaki tüm ortak ve özel sıralarda numaralandırır. 10 dakikada MSMQ Etkinleştirme hizmeti izlemek için kuyruk listesini yeniler. Kuyrukta bir ileti bulunduğunda, Etkinleştirme hizmeti net.msmq bağlama için eşleşen en uzun uygulama URI'sini için kuyruk adı ile eşleşen ve uygulamayı etkinleştirir.  
  
> [!NOTE]
>  Etkinleştirilmekte olan uygulama (en uzun eşleşme) kuyruk adı ön eki eşleşmesi gerekir.  
  
 Örneğin, bir kuyruk adıdır: msmqWebHost/orderProcessing/service.svc. Bir sanal dizin /msmqWebHost/orderProcessing altındaki bir service.svc ile uygulama 1 olan ve uygulama 2 altındaki bir orderProcessing.svc ile bir sanal dizin /msmqWebHost varsa, uygulama 1 etkinleştirilir. Uygulama 1 silinirse, uygulama 2 etkin hale gelir.  
  
> [!NOTE]
>  Bir kuyruk oluşturduğunuzda, kendisine gönderilen tüm iletileri MSMQ Etkinleştirme hizmeti, en fazla 10 dakika Sıranın oluşturulduğu zamandan ise kuyruğu listenin yenilenene kadar uygulama etkinleştirmeyin. Etkinleştirme hizmeti yeniden başlatmayı yanı sıra listesini yeniler.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Özel ve genel sıralar adresleme üzerinde etkisi  
 MSMQ Etkinleştirme hizmeti özel ve genel kuyruk izleme arasında ayrım yapmaz. Bu nedenle, genel ve özel sıralar ile aynı ada sahip olamaz. Bunu yaparsanız, Web barındırılan bir uygulamanın kuyrukları birinden okuma etkin.  
  
### <a name="queue-configuration-for-activation"></a>Etkinleştirme için sıraya yapılandırma  
 MSMQ Etkinleştirme hizmeti, ağ hizmeti olarak çalışır. Bu uygulamaları etkinleştirmek için kuyrukları izleyen hizmettir. Ağ hizmeti, erişim denetim listesi (ACL) iletiler için Özet erişimi için bu kuyruğu'ndan uygulamaları etkinleştirmek kuyruk sağlamanız gerekir.  
  
### <a name="poison-messaging"></a>Zehirli ileti  
 Zehirli ileti işleme WCF'de ileti zarar ancak kullanıcı yapılandırmasını temel alan bir değerlendirme seçer yalnızca algıladığı kanal tarafından işlenir. Sonuç olarak, kuyrukta tek bir ileti yok. Art arda gelen kez Web barındırılan uygulamayı durdurur ve yeniden kuyruğa ileti taşınır. Yeniden deneme döngüsü gecikme tarafından dikte bir noktada, ileti yeniden deneme kuyruktan ana kuyruğa yeniden denemek için taşınır. Ancak, bu kuyruğa alınmış kanal etkin olmasını gerektirir. Uygulama tarafından WAS geri dönüştürüldü, başka bir ileti sıraya alınan uygulamayı etkinleştirmek için ana kuyruğa gelene kadar ileti yeniden deneme kuyruğunda kalır. Geçici çözüm bu durumda yapılacak el ile yeniden deneme kuyruktan geri uygulamayı yeniden etkinleştirmek için ana kuyruğa taşımaktır.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Subqueue ve sistem sırası uyarı  
 WAS barındırılan bir uygulama, sistem genelinde atılacak veya zehirli alt kuyruklar gibi alt kuyruk gibi bir sistem kuyruğundaki iletileri göre etkinleştirilemiyor. Ürünün bu sürümü için bir sınırlama budur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
