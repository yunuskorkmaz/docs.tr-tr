---
title: Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: 36c35fe0590ad9fc728641313d4175a432d7ccaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951572"
---
# <a name="web-hosting-a-queued-application"></a>Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
Windows Işlem etkinleştirme hizmeti (WAS), Windows Communication Foundation (WCF) hizmetlerini barındıran uygulamalar içeren çalışan işlemlerinin etkinleştirilmesini ve ömrünü yönetir. WAS işlem modeli http sunucusu için IIS 6,0 işlem modelini genelleştirir ve HTTP 'nin bağımlılığını ortadan kaldırır. Bu, WCF hizmetlerinin, ileti tabanlı etkinleştirmeyi destekleyen ve belirli bir bilgisayarda çok sayıda uygulamayı barındırma olanağı sunan bir barındırma ortamında net. MSMQ ve MSMQ. formatname gibi HTTP ve HTTP olmayan protokolleri kullanmasına izin verir.  
  
 , Uygulama tarafından kullanılan kuyruklardan birine bir veya daha fazla ileti yerleştirildiğinde sıraya alınmış uygulamayı etkinleştiren bir Message Queuing (MSMQ) etkinleştirme hizmeti içermektedir. MSMQ etkinleştirme hizmeti, varsayılan olarak otomatik olarak başlatılan bir NT hizmetidir.  
  
 WAS ve avantajları hakkında daha fazla bilgi için bkz. [Windows Işlem etkinleştirme hizmeti 'Nde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). MSMQ hakkında daha fazla bilgi için bkz. [kuyruklara genel bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>WAS içinde sıra adresleme  
 WAS uygulamalarında Tekdüzen Kaynak tanımlayıcısı (URI) adresleri var. Uygulama adresleri iki bölümden oluşur: temel URI öneki ve uygulamaya özgü, göreli adres (yol). Bu iki bölüm, birlikte katıldığında bir uygulamanın dış adresini sağlar. Temel URI öneki site bağlamalarından oluşturulur ve site altındaki tüm uygulamalar (örneğin, "net. MSMQ:/localhost", "MSMQ. FormatName:/localhost" veya "net. TCP:/localhost") için kullanılır. Uygulama adresleri bundan sonra uygulamaya özel yol parçaları ("/applicationOne" gibi) alınarak oluşturulur ve bunları tam uygulama URI 'sine (örneğin, "net. MSMQ://localhost/applicationOne") ulaşmak için temel URI önekine ekler.  
  
 MSMQ etkinleştirme hizmeti, MSMQ etkinleştirme hizmeti 'nin ileti izlemesi gereken kuyrukla eşleşmesi için uygulama URI 'sini kullanır. MSMQ etkinleştirme hizmeti başlatıldığında, ' den almak üzere yapılandırıldığı bilgisayardaki tüm genel ve özel kuyrukları numaralandırır ve bunları iletiler için izler. MSMQ etkinleştirme hizmeti her 10 dakikada bir izlemek için kuyrukların listesini yeniler. Kuyrukta bir ileti bulunduğunda, etkinleştirme hizmeti, kuyruk adıyla net. MSMQ bağlamasının en uzun eşleşen uygulama URI 'siyle eşleşir ve uygulamayı etkinleştirir.  
  
> [!NOTE]
> Etkinleştirilen uygulamanın, sıra adının ön ekiyle eşleşmesi (en uzun eşleşme) gerekir.  
  
 Örneğin, bir kuyruk adı: msmqWebHost/orderProcessing/service. svc. Uygulama 1 ' de bir Service. svc ile bir sanal dizin/msmqWebHost/orderProcessing varsa ve uygulama 2 ' de bir orderProcessing. svc içeren bir sanal dizin/msmqWebHost varsa, uygulama 1 etkinleştirilir. Uygulama 1 silinirse, uygulama 2 etkinleştirilir.  
  
> [!NOTE]
> Bir kuyruk oluşturulduğunda, kendisine gönderilen iletiler, MSMQ etkinleştirme hizmeti sıra listesini yenileene kadar bir uygulamayı etkinleştirmez. Bu, en çok, sıranın oluşturulduğu zamandan itibaren 10 dakikadır. Etkinleştirme hizmetinin yeniden başlatılması kuyruk listesini de yeniler.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Özel ve genel sıraların adresleme üzerindeki etkisi  
 MSMQ etkinleştirme hizmeti özel ve genel sıra izleme arasında ayrım yapmaz. Bu nedenle, aynı ada sahip ortak ve özel kuyruklara sahip olamaz. Bunu yaparsanız, Web 'de barındırılan bir uygulama kuyruklardan birinden okuma için etkinleştirilebilir.  
  
### <a name="queue-configuration-for-activation"></a>Etkinleştirme için kuyruk yapılandırması  
 MSMQ etkinleştirme hizmeti ağ HIZMETI olarak çalışır. Uygulamaları etkinleştirmek için kuyrukları izleyen hizmettir. Kuyruktaki uygulamaları etkinleştirmek için, sıranın erişim denetim listesinde (ACL) iletilere gözatmak üzere ağ HIZMETI erişimi sağlaması gerekir.  
  
### <a name="poison-messaging"></a>Zarar Iletileri  
 WCF 'de zarar iletisi işleme kanal tarafından işlenir ve bu, yalnızca bir iletinin kirlediğinin ve Kullanıcı yapılandırmasına göre bir değerlendirme seçtiği anlamına gelir. Sonuç olarak, kuyrukta tek bir ileti vardır. Web 'de barındırılan uygulama ardışık olarak iptal edilir ve ileti yeniden deneme kuyruğuna taşınır. Yeniden deneme döngüsünün dikte edildiği bir noktada, yeniden denemek için ileti yeniden deneme sırasından ana sıraya taşınır. Ancak bu, sıraya alınan kanalın etkin olmasını gerektirir. Uygulama WAS tarafından geri dönüştürüldüğünde, sıraya alınmış uygulamayı etkinleştirmek için ana sıraya başka bir ileti gelene kadar ileti yeniden deneme sırasında kalır. Bu durumda geçici çözüm olarak, uygulamayı yeniden etkinleştirmek için yeniden deneme kuyruğundan iletiyi tekrar ana sıraya taşıyın.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Alt sıra ve sistem kuyruğu desteklenmediği uyarısıyla  
 WAS ile barındırılan bir uygulama, sistem sırasındaki, sistem genelinde atılacak ileti sırası veya zarar alt sıraları gibi alt kuyruklar gibi iletiler temel alınarak etkinleştirilemez. Bu, ürünün bu sürümü için bir kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
