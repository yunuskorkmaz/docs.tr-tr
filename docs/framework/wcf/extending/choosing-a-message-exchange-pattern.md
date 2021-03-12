---
description: 'Hakkında daha fazla bilgi edinin: Ileti değişim modelini seçme'
title: Bir İleti Değişim Deseni seçin
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: c0849ddb16596ebd6e064bb39f0727ac51642eb7
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605366"
---
# <a name="choosing-a-message-exchange-pattern"></a>Bir İleti Değişim Deseni seçin

Özel bir aktarım yazarken ilk adım, geliştirmekte olduğunuz kanal için hangi *ileti Exchange desenlerinin* (veya MEPs) gerekli olduğuna karar vermeye yöneliktir. Bu konu başlığı altında sunulan seçenekler açıklanmakta ve çeşitli gereksinimler ele alınmaktadır. Bu, [kanalların geliştirilmesi](developing-channels.md)bölümünde açıklanan Kanal geliştirme görev listesindeki ilk görevdir.  
  
## <a name="six-message-exchange-patterns"></a>Altı Ileti değişimi desenleri  

 Aralarından seçim yapabileceğiniz üç/PS vardır:  
  
- Veri birimi ( <xref:System.ServiceModel.Channels.IInputChannel> ve <xref:System.ServiceModel.Channels.IOutputChannel> )  
  
     Bir veri birimi MEP kullanırken, istemci bir ateş kullanarak bir ileti gönderir *ve Exchange 'i unutur* . Bir ateş ve unutur, başarılı teslimin bant dışı onayını gerektiren bir adım. İleti iletimde kaybolmuş olabilir ve hizmete hiçbir şekilde ulaşamamalıdır. Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak uç noktanın iletiyi aldığını garanti etmez. Bu veri birimi, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz gibi, mesajlaşma için temel bir yapı taşıdır. İstemci veri birimi kanalları arabirimini <xref:System.ServiceModel.Channels.IOutputChannel> uygulayan arabirimi ve hizmet veri birimi kanallarını uygular <xref:System.ServiceModel.Channels.IInputChannel> .  
  
- Request-Response ( <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel> )  
  
     Bu MEP 'de bir ileti gönderilir ve bir yanıt alındı. Bu model, istek-yanıt çiftlerinden oluşur. İstek-yanıt çağrılarına örnek olarak uzak yordam çağrıları (RPC) ve tarayıcı GET istekleri verilebilir. Bu model, yarı çift yönlü olarak da bilinir. Bu MEP 'de, istemci kanalları <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygular <xref:System.ServiceModel.Channels.IReplyChannel> .  
  
- Çift yönlü ( <xref:System.ServiceModel.Channels.IDuplexChannel> )  
  
     Çift yönlü MEP, istemci tarafından rastgele sayıda iletinin gönderilmesini ve herhangi bir sırada alınmasını sağlar. Çift yönlü MEP, konuşulan her sözcüğün bir ileti olduğu bir telefon konuşması gibidir. Her iki taraf da bu MEP 'de gönderebildiğinden ve alabileceği için, istemci ve hizmet kanalları tarafından uygulanan arabirim <xref:System.ServiceModel.Channels.IDuplexChannel> .  
  
 ![Üç temel ileti değişimi desenini gösteren akış çizelgesi](./media/wcfc-basicthreemepsc.gif)  
Üç temel ileti değişim deseni. Üstten alta: veri birimi, istek-yanıt ve çift yönlü.  
  
 Bu MEPs 'lerin her biri, *oturumları* da destekleyebilir. Bir oturum (ve türünün uygulanması <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType> ), bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirir. İstek ve yanıt bağıntılı olduğundan, istek-yanıt deseninin tek başına iki ileti oturumu vardır. Buna karşılık, oturumları destekleyen istek-yanıt deseninin, o kanaldaki tüm istek/yanıt çiftlerinin birbirleriyle bağıntılı olduğu anlamına gelir. Bu, aralarından seçim yapabileceğiniz toplam altı MEPs sağlar:  
  
- Inın  
  
- İstek-yanıt  
  
- Çift Yönlü  
  
- Oturumlarla veri birimi  
  
- İstek-oturumlarla yanıt  
  
- Oturumlarla çift yönlü  
  
> [!NOTE]
> UDP, doğal olarak bir yangın ve unutma Protokolü olduğundan, UDP taşıması için desteklenen tek MEP yalnızca veri birimi olur.  
  
## <a name="sessions-and-sessionful-channels"></a>Oturumlar ve oturumsuz kanallar  

 Ağ dünyasında bağlantı yönelimli protokoller (örneğin, TCP) ve bağlantı açısından daha az protokol (örneğin, UDP) vardır. WCF, bağlantı benzeri bir mantıksal soyutlama için oturum terimini kullanır. Oturumsuz WCF protokolleri, bağlantı odaklı ağ protokollerine benzerdir ve oturumsuz WCF protokolleri, bağlantı açısından daha az ağ protokollerine benzer.  
  
 Kanal nesne modelinde her mantıksal oturum, bir oturum kanalının bir örneği olarak bildirimlidir. Bu nedenle, istemci tarafından oluşturulan ve hizmette kabul edilen her yeni oturum, her bir tarafta yeni bir oturumsuz kanala karşılık gelir. Aşağıdaki diyagramda, en üstteki, sessionless kanalların yapısı ve en altta, oturum kanalların yapısı gösterilmektedir.  
  
 ![Oturumsuz ve oturumsuz kanalların yapısını gösteren akış çizelgesi](./media/wcfc-sessionandsessionlesschannelsc.gif)  
  
 İstemci yeni bir oturumsuz kanal oluşturur ve bir ileti gönderir. Hizmet tarafında, kanal dinleyicisi bu iletiyi alır ve yeni bir oturuma ait olduğunu algılar ve yeni bir oturum kanalı oluşturur ve uygulamayı uygulamaya (kanal dinleyicisinde AcceptChannel çağıran uygulamaya yanıt olarak) sahip olur. Daha sonra uygulama bu iletiyi ve sonraki tüm iletileri aynı oturumda, aynı oturumdaki kanal üzerinden gönderilir.  
  
 Başka bir istemci (veya aynı istemci) yeni bir oturumsuz oluşturur ve bir ileti gönderir. Kanal dinleyicisi, bu iletinin yeni bir oturumda olduğunu algılar ve yeni bir sessionchannel oluşturur ve işlem yinelenir.  
  
 Oturumlar olmadan, kanallar ve oturumlar arasında bir bağıntı yoktur. Bu nedenle, kanal dinleyicisi tüm alınan iletilerin uygulamaya teslim edildiği yalnızca bir kanal oluşturur. İleti sıralaması, içinde ileti sırası korunacak bir oturum olmadığından da yoktur. Yukarıdaki grafiğin en üst kısmında oturumsuz ileti alışverişi gösterilmektedir.  
  
## <a name="starting-and-terminating-sessions"></a>Oturumları başlatma ve sonlandırma  

 Oturumlar yalnızca yeni bir sessionchannel oluşturularak istemci üzerinde başlatılır. Hizmet yeni bir oturumda gönderilen bir ileti aldığında hizmette başlatılır. Benzer şekilde, oturumlar, oturumsuz bir kanalı kapatarak veya iptal ederek sonlandırılır.  
  
 Bunun özel durumu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , çift yönlü ve oturumsuz iletişim düzeninde ileti göndermek ve almak için kullanılır. Bir tarafın ileti gönderilmesini durdurmak, ancak ileti almaya devam etmek, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> daha fazla ileti gönderemeyeceğinizi belirten, giriş oturumunun açık kalmasını sağlayan bir mekanizma olduğunda, ileti almaya devam etmenizi sağlayan bir mekanizmanın daha fazla olması mümkündür.  
  
 Genel olarak, oturumlar giden tarafta kapatılır ve gelen tarafta değildir. Diğer bir deyişle, oturumsuz çıkış kanalları kapatılabilir ve bu sayede oturumu temiz bir şekilde sonlandıralabilirsiniz. Oturumsuz çıkış kanalının kapatılması, karşılık gelen oturum giriş kanalının, üzerinde çağıran uygulamaya null döndürmesine neden olur <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> .  
  
 Ancak, <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> oturumun zaten kapatıldığını belirten null değeri döndürülmediği takdirde oturumsuz giriş kanalları kapanmamalıdır. <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType>Üzerinde <xref:System.ServiceModel.Channels.IDuplexSessionChannel> null döndürülmediğinde, oturum açma işlemi sırasında beklenmeyen iletiler alabileceği için bir oturum giriş kanalının kapatılması bir özel durum oluşturabilir. Bir alıcı, gönderen olmadan önce bir oturumu sonlandırmaya istiyorsa, oturum beklenmedik bir şekilde <xref:System.ServiceModel.ICommunicationObject.Abort%2A> sona ermeden giriş kanalını çağırmalıdır.  
  
## <a name="writing-sessionful-channels"></a>Oturumsuz kanallar yazma  

 Oturumsuz kanal yazarı olarak, kanalınızın oturum sunmak için yapması gereken birkaç nokta vardır. Gönderme tarafında, kanalınızın şunları yapması gerekir:  
  
- Her yeni kanal için yeni bir oturum oluşturun ve benzersiz bir dize olan yeni bir oturum kimliğiyle ilişkilendirin. Ya da, yığında aşağıda bulunan oturumsuz kanaldan yeni bir oturum elde edin.  
  
- Bu kanalı kullanarak gönderilen her ileti için, kanalınız oturumu (sizin için aşağıdaki katmandan elde etmenin aksine) oluşturduysanız, iletiyi oturumla ilişkilendirmeniz gerekir. Protokol kanalları için bu genellikle bir SOAP üst bilgisi eklenerek yapılır. Taşıma kanalları için, bu genellikle yeni bir aktarım bağlantısı oluşturularak veya çerçeveleme protokolüne oturum bilgileri eklenerek yapılır.  
  
- Bu kanalı kullanarak gönderilen her ileti için yukarıda bahsedilen teslim garantisi sağlamanız gerekir. Oturumu sağlamanız için aşağıdaki kanala sahipseniz, bu kanal teslim garantisi verir. Oturumu kendiniz sağladıysanız, bu garantiyi protokolizin kapsamında uygulamanız gerekir. Genel olarak, her iki tarafta WCF 'yi kabul eden bir protokol kanalı yazıyorsanız, TCP aktarımı veya güvenilir mesajlaşma kanalı gerektirebilir ve bir oturum sağlamak için bunlardan birini kullanabilirsiniz.  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>Kanalınıza çağrıldığında, belirtilen zaman aşımını veya varsayılan olanı kullanarak oturumu kapatmak için gerekli işleri gerçekleştirin. Bu, aşağıdaki kanala çağrı yapmak kadar kolay olabilir <xref:System.ServiceModel.ICommunicationObject.Close%2A> (oturumu bundan önce edindiyseniz) veya özel BIR SOAP iletisi gönderiyor veya bir aktarım bağlantısını kapatıyor.  
  
- <xref:System.ServiceModel.ICommunicationObject.Abort%2A>Kanalınıza çağrıldığında, g/ç yapmadan oturumu aniden sonlandırın. Bu, herhangi bir şey yapmanın veya bir ağ bağlantısının ya da başka bir kaynağın iptal edilme olabileceği anlamına gelebilir.  
  
 Alma tarafında, kanalınızın şunları yapması gerekir:  
  
- Her gelen ileti için kanal dinleyicisi ait olduğu oturumu algılamamalıdır. Bu, oturumdaki ilk iletidir, kanal dinleyicisi yeni bir kanal oluşturmalı ve çağrısından döndürmelidir <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> . Aksi halde kanal dinleyicisi, oturuma karşılık gelen mevcut kanalı bulmalıdır ve iletiyi bu kanal üzerinden teslim eder.  
  
- Kanalınızın oturumu sağlaması varsa (gerekli teslimat garantisi ile birlikte), iletileri yeniden sıralama veya bildirimleri gönderme gibi bazı eylemler gerçekleştirmek için alma tarafı gerekebilir.  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A>Kanalınıza çağrıldığında, belirtilen zaman aşımı ya da varsayılan değer olan oturumu kapatmak için gerekli işleri gerçekleştirin. Bu, kanal bir ileti alırsa, kapatma zaman aşımının süresinin dolacağını beklerken özel durumlara neden olabilir. Bunun nedeni, kanalın, oluşturması için bir ileti aldığında kapanış durumunda olacağı durumdur.  
  
- <xref:System.ServiceModel.ICommunicationObject.Abort%2A>Kanalınıza çağrıldığında, g/ç yapmadan oturumu aniden sonlandırın. Bu durum, bir ağ bağlantısını veya başka bir kaynağı iptal edebilir veya herhangi bir şey yapmanız anlamına gelebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kanal Modeli Genel Bakış](channel-model-overview.md)
