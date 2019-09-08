---
title: Kanal Modeli Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 362a7392d9dbaedb1942280a6c3b6c8f2139afe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795894"
---
# <a name="channel-model-overview"></a>Kanal Modeli Genel Bakış
Windows Communication Foundation (WCF) kanal yığını, iletileri işleyen bir veya daha fazla kanala sahip katmanlı bir iletişim yığınıdır. Yığının en altında, kanal yığınını temel alınan aktarıma (örneğin, TCP, HTTP, SMTP ve diğer taşıma türleri) uyarmaktan sorumlu bir taşıma kanalı vardır. Kanallar, ileti göndermek ve almak için düşük düzey bir programlama modeli sağlar. Bu programlama modeli çeşitli arabirimlere ve WCF kanal modeli olarak bilinen diğer türlere dayanır. Bu konu başlığı altında, temel kanal dinleyicisi (hizmette) ve kanal fabrikasının (istemcide) oluşturulması, kanal şekilleri ele alınmaktadır.  
  
## <a name="channel-stack"></a>Kanal yığını  
 WCF uç noktaları, kanal yığını adlı bir iletişim yığınını kullanarak dünya ile iletişim kurar. Aşağıdaki diyagramda kanal yığını diğer iletişim yığınları ile karşılaştırılır, örneğin TCP/IP.  
  
 ![Kanal modeli](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Birincisi, benzerlikler: Her iki durumda da yığının her bir katmanı, bu katmanın altındaki dünyanın bir soyutlamasını sağlar ve bu soyutlamayı yalnızca doğrudan onun üzerinde olan katmana açık hale getirir. Her katman yalnızca doğrudan altındaki katmanın soyutlamasını kullanır. Her iki durumda da iki yığın iletişim kurduğunda, her katman diğer yığında karşılık gelen katmanla iletişim kurar. Örneğin, IP katmanı IP katmanıyla ve TCP katmanı ile TCP katmanıyla iletişim kurar ve bu şekilde devam eder.  
  
 Şu anda farklar: TCP yığını fiziksel ağın bir soyutlamasını sunacak şekilde tasarlanırken, kanal yığını yalnızca iletinin nasıl teslim edildiğini, diğer bir deyişle, taşımanın, ancak ileti içinde olanlar gibi diğer özellikleri ve ayrıca ne protokol, taşıma dahil, ancak bundan çok daha fazla iletişim için kullanılır. Örneğin, güvenilir oturum bağlama öğesi kanal yığınının bir parçasıdır, ancak taşımanın veya taşımanın altında değildir. Bu soyutlama, temeldeki aktarım protokolünü kanal yığını mimarisine uyarlamak ve sonra da güvenilirlik gibi iletişim özellikleri sağlamak üzere yığında daha fazla kanala güvenmek için yığında alt kanal gerektirilerek elde edilir. garanti ve güvenlik.  
  
 İletiler, iletişim yığınında nesneler olarak <xref:System.ServiceModel.Channels.Message> akar. Yukarıdaki şekilde gösterildiği gibi, alt kanala bir taşıma kanalı denir. Diğer taraflara ve onlardan ileti göndermekten ve onlardan sorumlu olan kanaldır. Bu, <xref:System.ServiceModel.Channels.Message> nesneyi diğer taraflarla iletişim kurmak için kullanılan biçimden ve biçiminden dönüştürme sorumluluğunu içerir. Aktarım kanalının üzerinde, güvenilir teslim garantisi gibi bir iletişim işlevi sağlamaktan sorumlu her bir sayıda protokol kanalı olabilir. Protokol kanalları, <xref:System.ServiceModel.Channels.Message> nesne biçiminde akan iletiler üzerinde çalışır. Genellikle, örneğin, başlık ekleyerek veya gövdeyi şifreleyerek ya da kendi protokol denetim iletilerini (örneğin, alındı bilgileri) alıp alarak iletiyi dönüştürür.  
  
## <a name="channel-shapes"></a>Kanal şekilleri  
 Her kanal, kanal şekil arabirimleri veya kanal şekilleri olarak bilinen bir veya daha fazla arabirimi uygular. Bu kanal şekilleri, kanalın uyguladığı ve kanal çağrılarının Kullanıcı tarafından kullanılan gönderme ve alma veya istek ve yanıt gibi iletişim yönelimli yöntemler sağlar. Kanal şekillerinin <xref:System.ServiceModel.Channels.IChannel> tabanında, yığındaki kanallar tarafından kullanıma sunulan rastgele özelliklere erişmek için katmanlı bir mekanizma olarak tasarlanan `GetProperty`bir \<T > yöntemi sağlayan arabirim. Genişleyen <xref:System.ServiceModel.Channels.IChannel> beş kanal şekli şunlardır:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Ayrıca, bu şekillerin her biri, destek oturumlarını genişleten <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> bir eşdeğerini içerir. Bunlar:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kanal şekilleri, mevcut taşıma protokolleri tarafından desteklenen bazı temel ileti değişimi desenlerinden sonra desenli şekilde yapılır. Örneğin, <xref:System.ServiceModel.Channels.IInputChannel> tek yönlü mesajlaşma bir / <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IReplyChannel> / <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IOutputChannel> çifte karşılık gelir, istek-yanıt, çiftler ve çift yönlü çift yönlü iletişimlere karşılık gelir (ve <xref:System.ServiceModel.Channels.IInputChannel> <xref:System.ServiceModel.Channels.IOutputChannel>ikisini de genişletir).  
  
## <a name="programming-with-the-channel-stack"></a>Kanal yığını ile programlama  
 Kanal yığınları genellikle bir bağlamanın kanal yığınını oluşturduğu bir fabrika düzeniyle oluşturulur. Gönderme tarafında, bir <xref:System.ServiceModel.ChannelFactory>bağlayıcı oluşturmak için kullanılır, bu da bir kanal yığını oluşturur ve yığındaki en üst kanala bir başvuru döndürür. Uygulama daha sonra bu kanalı kullanarak ileti gönderebilirler. Daha fazla bilgi için bkz. [Istemci kanal düzeyi programlama](client-channel-level-programming.md).  
  
 Alma tarafında bir bağlama, gelen iletileri dinleyen bir <xref:System.ServiceModel.Channels.IChannelListener>oluşturmak için kullanılır. , <xref:System.ServiceModel.Channels.IChannelListener> Kanal yığınları oluşturarak ve uygulama başvurusunu en üst kanala teslim ederek dinleme uygulamasına ileti sağlar. Uygulama daha sonra gelen iletileri almak için bu kanalı kullanır. Daha fazla bilgi için bkz. [hizmet kanalı düzeyi programlama](service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Kanal nesne modeli  
 Kanal nesne modeli, kanallar, kanal dinleyicileri ve kanal fabrikaları uygulamak için gereken temel arabirimlerin bir kümesidir. Özel uygulamalarda yardımcı olmak için bazı temel sınıflar da vardır.  
  
 Kanal dinleyicileri, gelen iletileri dinlemeden sorumludur ve bunları kanal dinleyicisi tarafından oluşturulan kanallar aracılığıyla yukarıdaki katmana teslim eder.  
  
 Kanal fabrikaları, ileti göndermek için kullanılan kanalları oluşturmaktan ve kanal fabrikası kapalıyken oluşturdukları tüm kanalların kapatılmasını sağlamaktan sorumludur.  
  
 <xref:System.ServiceModel.ICommunicationObject>, tüm iletişim nesnelerinin uygulaması olan temel durum makinesini tanımlayan çekirdek arabirimdir. <xref:System.ServiceModel.Channels.CommunicationObject>Bu çekirdek arabirimin, arabirimi yeniden uygulamak yerine, diğer kanal sınıflarının türetileyeceği bir uygulamasını sağlar. Ancak, bu gerekli değildir: özel bir kanal doğrudan uygulayabilir <xref:System.ServiceModel.ICommunicationObject> ve kaynağından <xref:System.ServiceModel.Channels.CommunicationObject>devralma işlemi yapabilir. Şekil 3 ' te sınıfların hiçbiri kanal modelinin parçası olarak kabul edilmez; Bunlar, kanallar oluşturmak isteyen özel kanal uygulayıcıları için kullanılabilir yardımcılardır.  
  
 ![Kanal modeli](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Aşağıdaki konularda, kanal nesne modelinin yanı sıra özel kanallar oluşturmaya yardımcı olan çeşitli geliştirme alanlarının de açıklaması verilmiştir.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Hizmetle Kanal dinleyicileri ve kanalları](service-channel-listeners-and-channels.md)|Bir hizmet uygulamasındaki gelen kanalları dinleyen Kanal dinleyicileri açıklar.|  
|[İstemcilerinin Kanal fabrikaları ve kanallar](client-channel-factories-and-channels.md)|Bir hizmet uygulamasına bağlanacak kanallar oluşturan Kanal fabrikalarını açıklar.|  
|[Durum Değişikliklerini Anlama](understanding-state-changes.md)|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> Arabirimin kanallarda durum değişikliklerinin nasıl yapıldığını açıklar.|  
|[İleti Değişim Deseni Seçme](choosing-a-message-exchange-pattern.md)|Kanalların destekleyebileceği altı temel ileti değişim modelini açıklar.|  
|[Özel Durum ve Hataları İşleme](handling-exceptions-and-faults.md)|Özel kanallarda hataların ve özel durumların nasıl işleneceğini açıklar.|  
|[Yapılandırma ve Meta Veri Desteği](configuration-and-metadata-support.md)|Uygulama modelinden özel kanalların kullanımını ve bağlamaları ve bağlama öğelerini kullanarak meta verileri dışa ve içe aktarmayı açıklar.|
