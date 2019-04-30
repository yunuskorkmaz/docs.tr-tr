---
title: İstemci Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: a94864563491b5bd2d50a6df59858f4b7235fd75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696229"
---
# <a name="accessing-services-using-a-client"></a>İstemci Kullanarak Hizmetlere Erişme
İstemci uygulamaları oluşturmak, yapılandırmak ve WCF istemci veya kanal nesneleri Hizmetleri ile iletişim kurmak için kullanmanız gerekir. [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md) konu nesneleri ve adımlarını temel istemci ve kanal nesneleri oluşturma ve bunları kullanarak genel bir bakış sağlar.  
  
 Bu konu, uygulamaları ve kendi senaryonuza bağlı olarak yararlı olabilecek istemci ve kanal nesneleri istemci ile bazı sorunlar hakkında ayrıntılı bilgi sağlar.  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, davranışı ve ilgili sorunları açıklar:  
  
- Kanal ve oturum yaşam süresi yok.  
  
- Özel durum işleme.  
  
- Engelleme sorunları anlama.  
  
- Kanalları etkileşimli olarak başlatılıyor.  
  
### <a name="channel-and-session-lifetimes"></a>Kanal ve oturum süreleri  
 Windows Communication Foundation (WCF) uygulamaları Kanallar, veri birimi ve sessionful iki kategorisi içerir.  
  
 A *veri birimi* tüm iletileri olduğu uncorrelated bir kanal kanalıdır. Bir veri birimi kanalına sahip bir giriş veya çıkış işlem başarısız olursa, sonraki işlemi genellikle etkilenmez ve aynı kanalı yeniden kullanılabilir. Bu nedenle, veri birimi kanalları genellikle hata değil.  
  
 *Sessionful* Kanallar, ancak başka bir uç noktası bağlantısı kanallarla değildir. Bir tarafta bir oturumda ileti her zaman diğer tarafta aynı oturumu ile ilişkilendirilir. Ayrıca, her iki katılımcıları bir oturumda, konuşma gereksinimlerini o oturum başarılı olarak değerlendirilmesi karşılanmadı kabul etmelisiniz. Kullanıcının kabul etmesi olamaz, oturum kanalı hata.  
  
 İstemciler, ilk işlem çağırarak açıkça veya dolaylı olarak açın.  
  
> [!NOTE]
>  Açıkça hatalı oturumdaki kanallar algılanmaya çalışılırken, ne zaman size bildirilir oturuma uygulama bağlı olduğundan genellikle kullanışlı değildir. Örneğin, çünkü <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> dinlemek için TCP bağlantısı oturumu (devre dışı güvenilir oturum ile) yüzeyler <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> hizmet veya bir ağ hatası durumunda hızlı bir şekilde bildirilmesi büyük olasılıkla istemci olayı. Ancak güvenilir oturumlar (burada bağlamalar tarafından kurulan <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> etkin) küçük ağ hataları hizmetlerinden sorunlardan uzak tutmak için tasarlanmıştır. Oturum zamanı, aynı bağlama makul bir süre içinde kurulmaları durumunda — güvenilir oturumlar için yapılandırılmış — uzun bir süre kesintiye devam kadar hata değil.  
  
 (Bu uygulama katmanına kanallara kullanıma sunma) sistem tarafından sağlanan bağlamalar çoğunu varsayılan olarak, oturumları kullanın ancak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> desteklemez. Daha fazla bilgi için [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Oturumlarının doğru kullanımı  
 Oturumlarının tüm ileti alışverişi tamamlandıktan ve her iki tarafında da başarılı kabul öğrenmek için bir yol sağlar. Çağıran uygulama kanal açın, kullanmak ve bir try bloğu içinde kanalı önerilir. Bir oturum kanalı açıksa ve <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> yöntemi bir kez çağrılır ve o çağrının başarıyla döndürür, ardından oturumu başarılı oldu. Başarılı bu durumda, belirtilen bağlama tüm teslimi garanti anlamına gelir karşılanmadı ve diğer tarafı çağrılmayan <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> çağırmadan önce kanalda <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 Aşağıdaki bölümde bu istemci yaklaşımın bir örneği olarak sağlanır.  
  
### <a name="handling-exceptions"></a>Özel Durumları İşleme  
 İstemci uygulamalarında özel durumları işleme oldukça basittir. Bir kanalı açıldı, kullanıldığı ve bir try bloğu içinde kapalı değilse bir özel durum sürece ardından konuşma, başarılı oldu. Genellikle, bir özel durum oluşturulursa konuşma iptal edildi.  
  
> [!NOTE]
>  Kullanım `using` deyimi (`Using` Visual Basic'te) önerilmez. Bunun nedeni, sonuna `using` deyimi hakkında bilmeniz gereken diğer özel durumları maskeleyebilir özel durumlara neden olabilir. Daha fazla bilgi için [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 Aşağıdaki kod örneği bir try/catch bloğu kullanarak önerilen istemci desenini gösterir ve `using` deyimi.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Değerini kontrol <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> özelliği bir yarış durumu ve yeniden kullanabilir veya bir kanalı belirlemek için önerilmez.  
  
 Veri birimi kanalları, hiçbir zaman kapatıldığında, bunlar özel durum oluşsa bile hata. Ayrıca, genellikle bir güvenli konuşma kullanarak kimlik doğrulaması için başarısız olmayan yönlü istemciler durum bir <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Ancak bir güvenli konuşma kullanarak çift yönlü istemci kimlik doğrulaması başarısız olursa istemci alır bir <xref:System.TimeoutException?displayProperty=nameWithType> yerine.  
  
 Uygulama düzeyinde hata bilgileri ile çalışma hakkında daha ayrıntılı bilgi için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) beklenen özel durumlar açıklar ve bunların nasıl ele alınacağını gösterir. Geliştirme kanalları, hataları işleme hakkında daha fazla bilgi için bkz [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>İstemci engelleme ve performans  
 Bir uygulama zaman uyumlu olarak çağırdığında bir istek-yanıt işleminde, dönüş değeri alınana kadar istemci blokları veya bir özel durum (gibi bir <xref:System.TimeoutException?displayProperty=nameWithType>) oluşturulur. Bu davranış, yerel davranışına benzer. Bir uygulamayı WCF istemci nesnesi veya kanal üzerinde bir işlem zaman uyumlu olarak çağırdığında, ağ veya bir özel durum kadar kanal katmanını veri yazabilirsiniz kadar istemci döndürmez. Tek yönlü ileti değişim deseni ederken (bir işlem ile işaretleyerek belirtilen <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> kümesine `true`) bağlama ve hangi ileti zaten silinmiş bağlı olarak daha hızlı yanıt, tek yönlü işlem da engeller, bazı istemciler yapabilirsiniz gönderilir. Yalnızca ileti exchange hakkında daha fazla ve en az tek yönlü işlemlerdir. Daha fazla bilgi için [One-Way Hizmetleri](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Büyük veri öbekleri hangi ileti değişim deseni ne olursa olsun işleme istemci yavaşlatabilir. Bu sorunların nasıl ele alınacağını anlamak için bkz: [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Bir işlem tamamlanırken uygulamanızı daha fazla iş yapmanız gereken, zaman uyumsuz yöntem çifti WCF istemci uygulayan hizmet sözleşme arabirimi oluşturmanız gerekir. Bunu yapmanın en kolay yolu kullanmaktır `/async` açın [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bir örnek için bkz [nasıl yapılır: Hizmet işlemlerini zaman uyumsuz çağırma](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 İstemci performansı artırma hakkında daha fazla bilgi için bkz. [orta katman istemci uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Kullanıcı kimlik bilgileri dinamik olarak seçmek etkinleştirme  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Arabirimi kullanıcının kimlik bilgileri ile bir kanalı oluşturulduğu zaman aşımı zamanlayıcılar önce seçmesini sağlayan bir kullanıcı arabirimini görüntülemek uygulamalar sağlar.  
  
 Uygulama geliştiricileri yapabilir eklenen bir kullanın <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> iki yolla. İstemci uygulaması da çağırabilir <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (veya zaman uyumsuz bir sürümü) kanal açmadan önce ( *açık* yaklaşım) veya ilk işlem çağırma ( *örtük*yaklaşım).  
  
 Örtük yaklaşımı kullanarak, uygulamanın ilk işlem üzerinde çağırmalıdır bir <xref:System.ServiceModel.ClientBase%601> veya <xref:System.ServiceModel.IClientChannel> uzantısı. İlk işlemin dışında her şey çağırırsa, bir özel durum oluşturulur.  
  
 Uygulama açık yaklaşımı kullanarak, aşağıdaki adımları sırayla gerçekleştirmeniz gerekir:  
  
1. Çağırın ya da <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (veya zaman uyumsuz bir sürümü).  
  
2. Başlatıcılar döndürüldüğünde çağırın ya da <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodunda <xref:System.ServiceModel.IClientChannel> nesne veya <xref:System.ServiceModel.IClientChannel> döndürülen nesne <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> özelliği.  
  
3. İşlemleri çağırın.  
  
 Üretim kalitesindeki uygulamaları açık bir yaklaşım benimseyerek kullanıcı arabirimi işlemini denetleyen önerilir.  
  
 Örtük bir yaklaşım kullanan uygulamaları kullanıcı arabirimi başlatıcılar çağırmak, ancak uygulamanın kullanıcı bağlama gönderme zaman aşımı süresi içinde yanıt vermezse, kullanıcı arabirimi döndürdüğünde bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Nasıl yapılır: Erişim Hizmetleri tek yönlü ve istek-yanıt sözleşmeleriyle](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nasıl yapılır: WSE 3.0 Erişim hizmeti](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Nasıl yapılır: Hizmet işlemlerini zaman uyumsuz olarak çağırma](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Orta Katman İstemci Uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
