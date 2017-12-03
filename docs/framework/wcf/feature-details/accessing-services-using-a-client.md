---
title: "İstemci Kullanarak Hizmetlere Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 180367920eb6f900fbb6b234b94f3b3a2c7fe52f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-services-using-a-client"></a>İstemci Kullanarak Hizmetlere Erişme
İstemci uygulamaları oluşturmak gerekir, yapılandırmak ve kullanmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri ile iletişim kurmak için istemci veya kanal nesne. [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md) konu, nesneleri ve temel istemci ve kanal nesneleri oluşturmak ve bunları kullanarak söz konusu adımlar genel bakış sağlar.  
  
 Bu konu, uygulamaları ve senaryonuza bağlı olarak yararlı olabilir istemci ve kanal nesneleri istemci ile bazı sorunlar hakkında ayrıntılı bilgi sağlar.  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda davranışı ve ilgili sorunlar açıklanmaktadır:  
  
-   Kanal ve oturum yaşam süresi.  
  
-   Özel durumları işleme.  
  
-   Engelleme sorunlarını anlama.  
  
-   Kanallar etkileşimli olarak başlatılıyor.  
  
### <a name="channel-and-session-lifetimes"></a>Kanal ve oturum süreleri  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Uygulama kanalları, veri birimi ve sessionful iki kategorisi içerir.  
  
 A *veri birimi* kanalıdır tüm iletileri olduğu uncorrelated bir kanal. Bir veri birimi kanalına sahip bir giriş veya çıkış işlemi başarısız olursa, sonraki işlemi genellikle etkilenmez ve aynı kanalı yeniden kullanılabilir. Bu nedenle, veri birimi kanalları genellikle hata değil.  
  
 *Sessionful* kanalları, ancak, diğer uç bağlantısı olan kanalları değildir. Bir tarafta bir oturumdaki iletilerin her zaman diğer taraftaki aynı oturum ile ilişkili olduğunu. Ayrıca, her iki katılımcıları oturumunda başarılı olarak kabul edilmesi bu oturum için kendi konuşma gereksinimleri karşılanmadı kabul etmelisiniz. Kabul edilemez durumunda süre sonuyla kanal hata.  
  
 İstemciler, ilk işlemi çağırarak açık veya örtülü olarak açın.  
  
> [!NOTE]
>  Açıkça hatalı süre sonuyla kanalları algılamak çalışırken, ne zaman bildirilir oturum uygulama bağımlı olduğundan genellikle kullanışlı değildir. Örneğin, çünkü <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> dinlemek için varsa (devre dışı güvenilir oturumla) TCP bağlantısı oturumu ortaya çıkarır <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> olayı hizmeti veya bir ağ hatası durumunda hızla bildirilmesi büyük olasılıkla istemci üzerinde. Ancak güvenilir oturumlar (bağlamaları, belirlenen <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> etkin) küçük ağ hataları Hizmetleri'nden verenlerden için tasarlanmıştır. Oturum makul bir süre sonunda süresi, aynı bağlama kurulmaları varsa — güvenilir oturumlar için yapılandırılmış — kesinti daha uzun bir süre devam kadar arıza değil.  
  
 (Bu, uygulama katmanı kanallara kullanıma) sistem tarafından sağlanan bağlamalar en sık kullandığınız oturumlar varsayılan olarak, ancak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> desteklemez. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Oturumları doğru kullanımı  
 Oturumları tüm ileti exchange tam ise ve her iki başarılı kabul olmadığını bilmek için bir yol sağlar. Çağrı yapan uygulamanın kanal açın, kullanmak ve bir try bloğunun kanalı önerilir. Bir oturum kanalı açıksa ve <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> yöntemi bir kez çağrılır ve bu çağrı başarılı bir şekilde döndürür, ardından oturumu başarılı oldu. Başarılı bu durumda, belirtilen bağlama tüm teslim garanti anlamına gelir karşılanmadı ve diğer taraftaki çağrılmayan <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> çağırmadan önce kanalda <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 Aşağıdaki bölümde, bu istemci yaklaşım ilişkin bir örnek sağlar.  
  
### <a name="handling-exceptions"></a>Özel Durumları İşleme  
 İstemci uygulamalarında özel durumları işleme basittir. Bir kanal açılan, kullanılan try bloğunun içine kapalı ise, bir özel durum sürece sonra konuşma, başarılı oldu. Genellikle, bir özel durum, konuşma iptal edilir.  
  
> [!NOTE]
>  Kullanımı `using` deyimi (`Using` içinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) önerilmez. Bunun nedeni, sonuna `using` deyimi hakkında bilmeniz gereken diğer özel durumlar maskeleyebilirsiniz özel durumlara neden olabilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Using deyimi sorunlarını önleme](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 Try/catch bloğu kullanarak önerilen istemci desen aşağıdaki kod örneğinde gösterir ve `using` deyimi.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Değeri denetleme <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> özelliği bir yarış durumu ve yeniden veya bir kanal kapatmak karar vermek için önerilmez.  
  
 Bunlar kapatıldığında özel durumlar oluşursa bile veri birimi kanalları hiç hata. Ayrıca, güvenli bir konuşma genellikle kullanarak kimlik doğrulaması başarısız çift yönlü olmayan istemciler throw bir <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Ancak istemci kimlik doğrulaması güvenli bir konuşma kullanarak çift yönlü istemci başarısız olursa, alır bir <xref:System.TimeoutException?displayProperty=nameWithType> yerine.  
  
 Uygulama düzeyinde hata bilgileri ile çalışma hakkında daha ayrıntılı bilgi için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Özel durumlar beklenen](../../../../docs/framework/wcf/samples/expected-exceptions.md) beklenen özel durumlar açıklar ve bunları nasıl ele alınacağını gösterir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Kanallar geliştirirken hataları işlemek için bkz: nasıl [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>İstemci engelleme ve performans  
 Bir uygulama zaman uyumlu olarak çağırdığında bir istek-yanıt işlemi, dönüş değeri alınana kadar istemci blokları veya bir özel durum (gibi bir <xref:System.TimeoutException?displayProperty=nameWithType>) oluşturulur. Bu davranış, yerel davranışına benzer. Ne zaman bir uygulamayı eşzamanlı olarak çağıran bir işlem üzerinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci nesnesi veya kanal, istemci döndürmez kadar kanal katmanını ağa veya bir özel durum kadar veri yazabilirsiniz. Tek yönlü ileti değişim deseni ederken (bir işlemle işaretleyerek belirtilen <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> kümesine `true`) bağlama ve ne ileti zaten silinmiş bağlı olarak daha iyi yanıt, tek yönlü işlemleri da engeller, bazı istemciler yapabilirsiniz gönderdi. Yalnızca ileti exchange hakkında daha fazla ve az tek yönlü işlemleridir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tek yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Büyük veri öbekleri hangi ileti değişim deseni olsun işleme istemci yavaşlatabilir. Bu sorunların nasıl ele alınacağını anlamak için bkz: [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Bir işlem tamamlanırken uygulamanız daha fazla iş yapmanız gerekir, bir zaman uyumsuz yöntem çifti hizmet sözleşmesi arabirimi, oluşturmanız gerekir, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygular. Bunu yapmanın en kolay yolu kullanmaktır `/async` anahtarının [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bir örnek için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]İstemci performansı artırma bkz [orta katman istemci uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Kullanıcının kimlik bilgilerini dinamik olarak seçmesini etkinleştirme  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Arabirimi kullanıcının kimlik bilgileri ile bir kanal oluşturulduğu zaman aşımı zamanlayıcılar önce seçmesini sağlayan bir kullanıcı arabirimini görüntülemek uygulamaları etkinleştirir.  
  
 Uygulama geliştiricilerinin yapabilir eklenen bir kullanmak <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> iki yolla. İstemci uygulaması ya da çağırabilirsiniz <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (veya zaman uyumsuz bir sürüm) kanal açmadan önce ( *açık* yaklaşım) veya ilk işlem çağırma ( *örtük*yaklaşım).  
  
 Örtük yaklaşım kullanıyorsanız, uygulamanın ilk işlemi üzerinde çağırmalıdır bir <xref:System.ServiceModel.ClientBase%601> veya <xref:System.ServiceModel.IClientChannel> uzantısı. İlk işlemi dışında her şey çağrılar içeriyorsa, özel durum oluşur.  
  
 Açık bir yaklaşım kullanıyorsanız, uygulamanın sırayla aşağıdaki adımları uygulamanız gerekir:  
  
1.  Ya da çağrısı <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (veya zaman uyumsuz bir sürüm).  
  
2.  Başlatıcılar döndürüldüğünde ya da çağrısı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.IClientChannel> nesne veya <xref:System.ServiceModel.IClientChannel> döndürülen nesne <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> özelliği.  
  
3.  Operations çağırın.  
  
 Üretim kaliteli uygulamaları açık yaklaşım'nu benimseme kullanıcı arabirimi işlemini denetleyen önerilir.  
  
 Kullanıcı arabirimi başlatıcıları örtük yaklaşım kullanan uygulamalar çağırma, ancak uygulamanın kullanıcısı bağlama gönderme zaman aşımı süresi içinde yanıt vermiyorsa, kullanıcı arabirimi döndürdüğünde özel durum oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çift yönlü hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)  
 [Nasıl yapılır: Erişim Hizmetleri tek yönlü ve istek-yanıt sözleşmeleri](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Nasıl yapılır: WSE 3.0 Erişim hizmeti](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)  
 [Nasıl yapılır: çağrı hizmet işlemlerini zaman uyumsuz olarak](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Orta katman istemci uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
