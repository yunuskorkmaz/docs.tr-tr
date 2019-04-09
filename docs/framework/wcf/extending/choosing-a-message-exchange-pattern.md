---
title: Bir İleti Değişim Deseni seçin
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 98788fb89fc68dc1220d9bf8d9ad89df5ca69e6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157806"
---
# <a name="choosing-a-message-exchange-pattern"></a>Bir İleti Değişim Deseni seçin
Özel bir taşıma yazma ilk adımı, karar vermektir *ileti exchange desenleri* (veya MEPs) geliştirdiğiniz kanal için gereklidir. Bu konu, kullanılabilir seçenekleri açıklar ve çeşitli anlatılmaktadır. Bu kanal geliştirme görev listesinde açıklanan ilk görevdir [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Altı ileti Exchange desenleri  
 Aralarından seçim yapabileceğiniz üç MEPs vardır:  
  
-   Veri birimi (<xref:System.ServiceModel.Channels.IInputChannel> ve <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Bir veri birimi MEP kullanırken, bir istemci kullanarak bir ileti gönderen bir *Başlat ve unut* exchange. Bir Başlat ve unut değişimi, başarılı bir teslimat bant dışı onay gerektiren bir. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmet ulaşın. İstemci sonunda gönderme işlemi başarıyla tamamlarsa, uzak uç noktada bir ileti aldı garanti etmez. Bunun üstünde kurallarınızı oluştururken veri birimi Mesajlaşma için temel yapı taşı olan — güvenilir protokolleri ve güvenli protokolleri dahil. İstemci veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IOutputChannel> arabirimi ve hizmet veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IInputChannel> arabirimi.  
  
-   İstek-yanıt (<xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     Bu MEP bir ileti gönderilir ve bir yanıt aldı. Desen, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekleri: uzaktan yordam çağrısı (RPC) ve tarayıcı GET istekleri. Bu düzen, yarı çift yönlü da bilinir. Bu MEP içinde istemci kanalları uygulamak <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygulamak <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Çift yönlü (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Çift yönlü MEP tercihe bağlı sayıda istemci tarafından gönderilen ve alınan herhangi bir sırada iletileri sağlar. Çift yönlü MEP bir telefon konuşması gibi burada konuşulan her bir sözcüğün bir ileti numarasıdır. Her iki tarafında da gönderebilir ve alabilir bu MEP, istemci ve hizmet kanalları tarafından uygulanan arabirimi çünkü <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Bir ileti değişim deseni seçme](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Üç temel ileti exchange desenleri. Yukarıdan aşağıya doğru: veri birimi, çift yönlü ve istek-yanıt.  
  
 Her biri bu MEPs de destekleyebilir *oturumları*. Bir oturum (ve uygulaması <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> türü <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) bir kanalı üzerinden alınan ve gönderilen tüm iletilerin ilişkilendirir. İstek-yanıt desen istek ve yanıt bağıntılı olan bir tek başına iki ileti oturumu aynıdır. Buna karşılık, bu kanal üzerindeki tüm istek/yanıt çifti birbiriyle ilişkilendirilir oturumları destekleyen istek-yanıt deseni gösterir. Bu, aralarından seçim yapabileceğiniz altı MEPs toplam sağlar:  
  
-   Veri birimi  
  
-   İstek-yanıt  
  
-   Çift Yönlü  
  
-   Veri birimi ile oturumları  
  
-   İstek-yanıt oturumları içeren  
  
-   Oturumlarının ile çift yönlü  
  
> [!NOTE]
>  UDP kendiliğinden yangın olduğu ve unut protokolü UDP taşıma için desteklenen tek MEP veri birimi, olmasıdır.  
  
## <a name="sessions-and-sessionful-channels"></a>Oturumlarının ve Sessionful kanallar  
 Ağ dünyasında, bağlantıya dayalı protokolleri (örneğin, TCP) ve bağlantı olmayan protokolleri (örneğin, UDP) vardır. WCF bağlantı benzeri mantıksal soyutlama auto'yu terimi oturumu kullanır. Kapatamaması WCF protokolleri bağlantıya dayalı ağ protokolleri için benzer ve oturumsuz WCF protokoller, bağlantı daha az ağ protokolleri için benzerdir.  
  
 Kanal nesne modelinde bir oturum kanalı bir örneği olarak her bir mantıksal oturum bildirimleri. Bu nedenle istemci tarafından oluşturulmuş ve hizmette kabul her yeni oturumu yeni bir oturum kanalı her iki taraftaki karşılık gelir. Aşağıdaki diyagramda gösterildiği, oturumsuz kanalları yapısını üst ve alt oturumdaki kanallar yapısı.  
  
 ![Bir ileti değişim deseni seçme](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Bir istemci, yeni bir oturum kanalı oluşturur ve bir ileti gönderir. Hizmet tarafında, kanal dinleyicisi şu iletiyi alıyor ve yeni bir oturum kanalı oluşturur ve uygulamaya (yanıtta AcceptChannel kanal dinleyicisi üzerinde arama uygulaması) uygulamalı şekilde yeni bir oturuma ait olduğunu algılar. Uygulama daha sonra bu iletiyi ve aynı oturumda aynı oturum kanalı üzerinden gönderilen tüm sonraki iletiler alır.  
  
 Başka bir istemci (veya aynı istemci) yeni sessionful oluşturur ve bir ileti gönderir. Kanal dinleyicisi bu iletiyi yeni bir oturumda ve yeni bir oturum kanalı oluşturur ve işlem yinelenir algılar.  
  
 Oturumlarının Kanallar ve oturumları arasında ile hiçbir bağıntısı yoktur. Bu nedenle kanal dinleyicisi alınan iletilerin tümünü uygulamaya teslim edilir yalnızca bir kanal oluşturur. İleti, ileti sırası korumak hiçbir oturumunda olduğundan sıralama yoktur. Önceki grafiğin üst kısmını oturumsuz ileti değişimi gösterir.  
  
## <a name="starting-and-terminating-sessions"></a>Başlangıç ve oturumları sonlandırma  
 Oturumları, istemci üzerinde yeni bir oturum kanalı oluşturarak başlatılır. Hizmet, yeni bir oturumda gönderildiği bir ileti aldığında, hizmette başlatılır. Benzer şekilde, oturum kapatma veya bir oturum kanalı durduruluyor sonlandırılır.  
  
 Özel durum <xref:System.ServiceModel.Channels.IDuplexSessionChannel> hem ileti alma ve gönderme bir çift yönlü, kapatamaması iletişim deseni için kullanılır. Gönderme durdurur ancak kullanırken, bu nedenle iletileri alacak şekilde devam etmek bir tarafı isteyeceksiniz mümkündür <xref:System.ServiceModel.Channels.IDuplexSessionChannel> daha fazla ileti göndermez ancak giriş oturumu tutmak belirten çıkış Oturumu Kapat olanak sağlayan bir mekanizma yoktur. açılan ileti almak devam etmenize imkan sağlar.  
  
 Genel olarak, giden tarafında ve gelen tarafında değil oturumları kapatılır. Diğer bir deyişle, böylece düzgün bir şekilde oturumunu sona erdirme kapatamaması çıkış kanalları kapatılabilir. Neden olan uygulama arama için null döndürmek karşılık gelen oturum Giriş kanalı kapatamaması çıkış kanal kapatma <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Bununla birlikte giriş oturumdaki kanallar sürece kapatılmalıdır değil <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel> oturumu zaten kapatıldı gösteren null döndürür. Varsa <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sahip kapatılırken beklenmeyen iletileri alabilirsiniz çünkü null döndürdü değil, bir oturum Giriş kanalı kapatma bir özel durum oluşturabilir. Gönderen önce oturumu sonlandırmak bir alıcı isterse çağırmalıdır <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Giriş kanalı aniden sonlandıran oturumu.  
  
## <a name="writing-sessionful-channels"></a>Yazma Sessionful kanallar  
 Bir oturum kanalı yazarı kanalınızı oturumları sağlamak için yapmanız gereken birkaç nokta vardır. Gönderme tarafında kanalınızı gerekir:  
  
-   Her yeni bir kanal için yeni bir oturum oluşturun ve benzersiz bir dize olan yeni bir oturum kimliğiyle ilişkilendirin. Veya yeni bir oturum aşağıdaki oturum kanalı yığınında almak.  
  
-   Bu kanalı kullanılarak gönderilen her ileti için kanalınızı (aksine, aşağıdaki katman almakla), oturum oluşturduysanız ileti oturumla ilişkilendirmeniz gerekir. Protokol kanallar için bu genellikle bir SOAP üst bilgisi ekleyerek gerçekleştirilir. Aktarım kanallar için bu genellikle yeni bir aktarım bağlantısı oluşturma veya oturum bilgilerini çerçeveleme protokole ekleyerek gerçekleştirilir.  
  
-   Bu kanalı kullanılarak gönderilen her ileti için yukarıda belirtilen teslimat garantileriyle sağlamanız gerekir. Kanal altına oturumu vermenizi bağlı, bu kanal ayrıca teslimat garantileriyle sağlar. Oturumu kendiniz sağlıyorsanız protokolünüzü kapsamında bu garanti uygulamak gerekir. Genel olarak, her iki kenarı da WCF varsayar bir protokolü kanalı yazıyorsanız TCP taşıma ya da güvenilir bir Mesajlaşma kanalı gerektirir ve bir oturumu sağlamak için bunlardan birini kullanan olabilirsiniz.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> olduğundan, kanalınızda adlı, belirtilen zaman aşımı veya varsayılan kullanarak oturumu kapatmak için gerekli iş gerçekleştirin. Bu arama olarak basit olabilir <xref:System.ServiceModel.ICommunicationObject.Close%2A> aşağıda (yalnızca oturum buradan elde ettiğiniz isteyip) veya özel bir SOAP ileti gönderme veya bir aktarım bağlantısı kapatma kanal.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Abort%2A> olduğundan, kanalda çağrıldı, oturumu aniden g/ç işlemi yapmadan sonlandır. Bu, hiçbir şey yapmadan anlamına gelebilir veya bir ağ bağlantısı veya başka bir kaynak durduruluyor gerektirebilir.  
  
 Alma tarafında kanalınızı gerekir:  
  
-   Gelen her ileti için kanal dinleyicisi ait oturum algılaması gerekir. Bu oturumdaki ilk iletiyi ise, kanal dinleyicisi gereken yeni bir kanal oluşturmak ve çağrıdan dönüş <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. Aksi takdirde kanal dinleyicisi oturuma karşılık gelir ve kanal üzerinden ileti teslim varolan kanalın bulmanız gerekir.  
  
-   Kanalınızı (birlikte gerekli teslimat garantileriyle) oturumu sağlıyorsa sıralamasını iletileri gibi bazı eylemleri veya bildirimleri göndermek için alma tarafında gerekebilir.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A> olduğundan, kanalda çağrıldı, oturumu kapatmak için gerekli iş belirtilen zaman aşımı veya varsayılan gerçekleştirin. Süresi dolacak şekilde Kapat zaman aşımı için beklenirken bir ileti kanalı alırsa, bu özel durumların neden olabilir. Throw için ileti aldığında kanal kapatma durumda olacaktır olmasıdır.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Abort%2A> olduğundan, kanalda çağrıldı, oturumu aniden g/ç işlemi yapmadan sonlandır. Yeniden birşey anlamına gelebilir veya bir ağ bağlantısı veya başka bir kaynak durduruluyor gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kanal Modeli Genel Bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md)
