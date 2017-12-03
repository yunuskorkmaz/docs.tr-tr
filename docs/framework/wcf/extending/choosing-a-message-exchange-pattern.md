---
title: "Bir İleti Değişim Deseni seçin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab9a894ad57a5324d466e0eb94e49e2cf6104a19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="choosing-a-message-exchange-pattern"></a>Bir İleti Değişim Deseni seçin
Özel bir taşıma yazma ilk adımı, karar vermektir *ileti exchange desenleri* (veya MEPs) geliştirme kanalı gereklidir. Bu konuda seçenekleri açıklar ve çeşitli gereksinimleri açıklanır. Bu ilk bölümünde açıklanan kanal geliştirme görev listesindeki bir görevdir [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Altı ileti Exchange desenleri  
 Aralarından seçim yapabileceğiniz üç MEPs vardır:  
  
-   Veri birimi (<xref:System.ServiceModel.Channels.IInputChannel> ve <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Veri birimi MEP kullanırken, bir istemci kullanarak bir ileti gönderir bir *yangın ve unut* exchange. A yangın ve exchange başarılı teslimat bant dışı onay gerektiren bir tane olduğunu unutmayın. İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmete erişmek. Gönderme işlemi istemci sonunda başarıyla tamamlarsa, uzak uç noktada bir ileti aldı garanti etmez. Veri birimi üzerine kurallarınızı oluşturabilirsiniz Mesajlaşma için temel yapı bloğu aynıdır — güvenilir protokolleri ve güvenli iletişim kuralları da dahil olmak üzere. İstemci veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IOutputChannel> arabirimi ve hizmet veri birimi kanallar uygulamak <xref:System.ServiceModel.Channels.IInputChannel> arabirimi.  
  
-   İstek-yanıt (<xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     Bu MEP bir ileti gönderilir ve bir yanıt aldı. Desen istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrıları örnekler uzaktan yordam çağrısı (RPC) ve tarayıcı GET istekleri. Bu desen yarı çift yönlü da bilinir. Bu MEP, istemci kanalları uygulamak <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygulamak <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Çift yönlü (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Çift yönlü MEP bir rastgele bir istemci tarafından gönderilen ve herhangi bir sırada alınan ileti sayısı için sağlar. Çift yönlü MEP bir telefon konuşması gibi konuşulan her sözcüğün bir ileti olduğu. Her iki tarafında da gönderebilir ve bu MEP alabilir, istemci ve hizmet kanalları tarafından uygulanan arabirimi çünkü <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Bir ileti değişim deseni seçin](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Üç temel ileti exchange desenleri. Yukarıdan aşağıya doğru: veri birimi, istek-yanıt ve çift yönlü.  
  
 Her bu MEPs da destekleyebilir *oturumları*. Bir oturum (ve uyarlamasını <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> türü <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) karşılık gelen bir kanalda alınıp gönderilen tüm iletiler. İstek-yanıt düzeni istek ve yanıt bağıntısı tek başına iki ileti oturum aynıdır. Buna karşılık, oturumlar destekleyen istek-yanıt düzeni bu kanalda tüm istek/yanıt çiftleri birbiriyle ilişkili anlamına gelir. Bu, içinden seçim yapabileceğiniz altı MEPs toplam sunar:  
  
-   Veri birimi  
  
-   İstek-yanıt  
  
-   Çift Yönlü  
  
-   Veri birimi oturumu  
  
-   İstek-yanıt oturumu  
  
-   Oturumları ile çift yönlü  
  
> [!NOTE]
>  UDP kendiliğinden yangın olduğundan ve protokolü unuttunuz UDP taşıma için desteklenen tek MEP veri birimi, ' dir.  
  
## <a name="sessions-and-sessionful-channels"></a>Oturumlar ve Sessionful kanalları  
 Ağ dünyada bağlantı yönelimli protokolleri (örneğin, TCP) ve bağlantı daha az protokolleri (örneğin, UDP) vardır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir bağlantı gibi mantıksal soyutlama anlamına gelir terim oturumu kullanır. Süre sonuyla WCF protokolleri bağlantı odaklı ağ protokolleri benzer ve oturumsuz WCF protokolleri bağlantı daha az ağ protokolleri benzer.  
  
 Kanal nesne modelinde, her mantıksal oturum süre sonuyla kanal örneği bildirimleri. Bu nedenle istemci tarafından oluşturulan ve hizmette kabul her yeni oturumun her tarafında yeni bir süre sonuyla kanal karşılık gelir. Aşağıdaki diyagramda gösterildiği, oturumsuz kanalları yapısını üst ve alt, süre sonuyla kanalları yapısı.  
  
 ![Bir ileti değişim deseni seçin](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Bir istemci yeni bir süre sonuyla kanalı oluşturur ve bir ileti gönderir. Hizmet tarafı kanal dinleyicisi şu iletiyi alıyor ve böylece yeni bir süre sonuyla kanalı oluşturur ve uygulamaya (AcceptChannel kanal dinleyicisi çağırma uygulama yanıt) aktarır yeni bir oturuma ait olduğunu algılar. Uygulama daha sonra bu iletiyi ve aynı süre sonuyla kanal üzerinden aynı oturumda gönderilen tüm sonraki iletiler alır.  
  
 Başka bir istemci (veya aynı istemci) yeni bir sessionful oluşturur ve bir ileti gönderir. Kanal dinleyicisi, bu iletiyi yeni bir oturumda ve yeni bir süre sonuyla kanalı oluşturur ve işlem yinelenir algılar.  
  
 Oturumlar, hiçbir bağıntı kanalları ve oturumlar arasında yoktur. Bu nedenle kanal dinleyicisi alınan iletilerin tümünü uygulamaya teslim edilir yalnızca bir kanalı oluşturur. İleti sırası korumak için hiçbir oturumunda olduğundan sıralama hiçbir ileti yoktur. Yukarıdaki grafikte üst kısmını oturumsuz ileti değişimi gösterir.  
  
## <a name="starting-and-terminating-sessions"></a>Başlangıç ve oturumları sonlandırma  
 Oturumları, istemci üzerinde yeni bir süre sonuyla kanal oluşturarak başlatılır. Hizmet yeni bir oturumda gönderilen bir ileti alındığında bunlar hizmeti başlatılır. Benzer şekilde, oturum kapatma veya bir süre sonuyla kanal durduruluyor sonlandırılır.  
  
 Özel durum <xref:System.ServiceModel.Channels.IDuplexSessionChannel> hem ileti alma ve gönderme bir çift yönlü, süre sonuyla iletişim deseni için kullanılır. Sütunlardan ileti gönderilmesini durdurmak istiyor ancak iletileri bu nedenle kullanırken almaya devam istemeniz mümkündür <xref:System.ServiceModel.Channels.IDuplexSessionChannel> daha fazla ileti göndermez ancak giriş oturum tutmak belirten çıkış Oturumu Kapat olanak sağlayan bir mekanizması iletileri almaya devam etmenize izin vererek açıldı.  
  
 Genel olarak, giden tarafında ve gelen tarafında değil oturumları kapatılır. Diğer bir deyişle, böylece düzgün bir şekilde oturum sonlandırma süre sonuyla çıkış kanalları kapatılabilir. Bir süre sonuyla çıktı kanalı kapatma neden olan uygulama arama için null döndürmek karşılık gelen süre sonuyla Giriş kanalı <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Ancak süre sonuyla giriş kanalları sürece kapatılmalıdır değil <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel> oturumu zaten kapatılmış gösteren null döndürür. Varsa <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sahip kapatılırken beklenmeyen iletileri alabilirsiniz için null döndürdü değil, bir süre sonuyla Giriş kanalı kapatma bir özel durum. Bir alıcı gönderen yapmadan önce bir oturumu sonlandır isterse çağırmalıdır <xref:System.ServiceModel.ICommunicationObject.Abort%2A> giriş kanalında, beklenmedik şekilde sonlandırır oturumu.  
  
## <a name="writing-sessionful-channels"></a>Yazma Sessionful kanalları  
 Bir süre sonuyla kanal yazarı, kanal oturumları sağlamak için yapmanız gerekir birkaç nokta vardır. Gönderen tarafında kanalınızı gerekir:  
  
-   Her yeni kanal için yeni bir oturum oluşturun ve benzersiz bir dize olan bir yeni bir oturum kimliği ile ilişkilendirin. Veya yeni bir oturum, aşağıda süre sonuyla kanal yığınında almak.  
  
-   Bu kanalı kullanılarak gönderilen her ileti için kanalınızı (aksine, aşağıdaki katmandan alma), oturum oluşturduysanız ileti oturumla ilişkilendirmeniz gerekir. Protokol kanallar için bu genellikle bir SOAP üstbilgi ekleyerek yapılır. Taşıma kanalları için bu genellikle yeni bir taşıma bağlantısı oluşturma veya oturum bilgilerini çerçeveleme Protokolü ekleyerek yapılır.  
  
-   Bu kanalı kullanılarak gönderilen her ileti için yukarıda belirtilen teslimat garantileriyle sağlamanız gerekir. Oturum sağlamak için aşağıdaki kanalda FQDN'yi kullanıyorsanız, bu kanala teslimat garantileriyle de sağlanır. Oturumu kendiniz sağlıyorsanız, protokolünün bir parçası bu garanti yapması gerekir. Genel olarak, iki tarafta da WCF varsayar Protokolü kanalı yazıyorsanız TCP taşıma veya güvenilir Mesajlaşma kanalı gerektirir ve bir oturum sağlamak için herhangi birini kullanan.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> olduğundan, kanalda adlı, belirtilen zaman aşımı veya varsayılan kullanarak oturumu kapatmak için gerekli olan iş gerçekleştirin. Bu çağırmak kadar kolaydır, <xref:System.ServiceModel.ICommunicationObject.Close%2A> (yalnızca oturum ondan aldığınız isteyip) veya özel bir SOAP iletisi gönderme veya bir taşıma bağlantısını kapatma aşağıda kanalda.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Abort%2A> olduğundan, kanalda çağrıldı, oturumu aniden g/ç yapmadan sona erdirmek. Bu, hiçbir şey yapılması olduğu anlamına gelebilir veya bir ağ bağlantısı veya başka bir kaynağa durduruluyor gerektirebilir.  
  
 Alma tarafında kanalınızı gerekir:  
  
-   Gelen her ileti için kanal dinleyicisi ait oturum algılaması gerekir. Bu oturumda ilk ileti ise, kanal dinleyicisi yeni bir kanal oluşturmalı ve bu çağrısı döndürmek <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. Aksi takdirde kanal dinleyicisi oturuma karşılık gelen ve bu kanal üzerinden ileti ileten varolan kanal bulmanız gerekir.  
  
-   Sağlıyorsa, kanalınızı (birlikte gerekli teslimat garantileriyle) oturum alış tarafı yeniden sıralamak iletileri gibi bazı eylemleri gerçekleştirmek ya da bildirimleri göndermek için gerekli.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A> olduğundan, kanalda çağrıldı, oturumu kapatmak için gerekli olan iş belirtilen zaman aşımı veya varsayılan gerçekleştirin. Süresi dolacak şekilde Kapat zaman aşımı için beklenirken bir ileti kanalı alırsa, bu özel durumları neden olabilir. Throw böylece bir ileti aldığında kanal kapanış durumda olacaktır olmasıdır.  
  
-   Zaman <xref:System.ServiceModel.ICommunicationObject.Abort%2A> olduğundan, kanalda çağrıldı, oturumu aniden g/ç yapmadan sona erdirmek. Yeniden, hiçbir şey yapılması olduğu anlamına gelebilir veya bir ağ bağlantısı veya başka bir kaynağa durduruluyor gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md)
