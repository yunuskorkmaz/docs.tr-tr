---
title: İstemci Mimarisi
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781530"
---
# <a name="client-architecture"></a>İstemci Mimarisi
Uygulamaları Windows Communication Foundation (WCF) istemci nesneleri hizmet işlemleri çağırmak için kullanın. Bu konu, WCF istemci nesneler, WCF istemci kanalları ve ilişkilerinin kanal'ın temel mimarisini açıklar. WCF istemci nesneleri temel bir genel bakış için bkz [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md). Kanal katmanını hakkında daha fazla bilgi için bkz: [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Genel Bakış  
 Çalışma zamanı hizmet modeli aşağıdakilerden oluşur WCF istemcileri oluşturur:  
  
- Uygulama kodunuz çağrılarından giden iletiler kapatır ve yanıt iletilerini çıkış parametreleri ve uygulamanızı alabileceğiniz dönüş değerlerine dönüştürür hizmet sözleşmesini otomatik olarak oluşturulan istemci uygulaması.  
  
- Bir denetim arabiriminin (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>) çeşitli arabirimleri gruplandıran ve işlevleri, özellikle istemci oturumunu kapatın ve kanalı silmek için özelliği denetlemek için erişim sağlar.  
  
- Oluşturulan istemci kanal kullanılan bağlama tarafından belirtilen yapılandırma ayarları temel.  
  
 Uygulamalar üzerinden isteğe bağlı olarak bu gibi istemcilerde oluşturabilirsiniz bir <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> veya bir örneğini oluşturarak bir <xref:System.ServiceModel.ClientBase%601> türetilmiş sınıf tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu hazır oluşturulan istemci sınıfları kapsüllemek ve temsilci tarafından dinamik olarak oluşturulmuş bir istemci kanal uygulaması için bir <xref:System.ServiceModel.ChannelFactory>. Dolayısıyla, istemci kanal ve bunları üretir bir kanal fabrikası bu tartışma için ilgi odak noktası altındadır.  
  
## <a name="client-objects-and-client-channels"></a>İstemci nesneleri ve istemci kanalları  
 WCF istemcileri, temel arabirim <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> çekirdek istemci işlevselliğinin yanı sıra temel iletişim nesnesi işlevselliğini kullanıma sunan arabirim, <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, bağlam işlevselliğini <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>ve Genişletilebilir davranışı <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Arabirimi, ancak tanımlamıyor bir servis sözleşmesi. Bu hizmet sözleşme arabirimi tarafından bildirilen (genellikle hizmet meta verileri gibi bir araç kullanarak oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). WCF istemci türleri genişleten hem <xref:System.ServiceModel.IClientChannel> ve doğrudan hem de işlemleri çağırmak uygulamaları etkinleştirmek için hedef hizmet sözleşme arabirimi istemci tarafı çalışma zamanı işlevleri erişime sahiptir. Bir WCF istemcisi oluşturma sağlar WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> bağlanabilir ve yapılandırılan hizmet uç noktası ile etkileşim nesneleri içeren bir çalışma zamanı oluşturmak gereken bilgileri.  
  
 Daha önce bahsedildiği gibi iki WCF istemci türlerini da kullanabilmeniz için önce yapılandırılması gerekir. Basit bir WCF istemci türlerini, türetilen nesnelerdir <xref:System.ServiceModel.ClientBase%601> (veya <xref:System.ServiceModel.DuplexClientBase%601> hizmet sözleşmesi çift yönlü sözleşme ise). Program aracılığıyla, yapılandırılmış, bir oluşturucu kullanılarak veya bir yapılandırma dosyası kullanarak bu türleri oluşturabilir ve hizmet işlemleri çağırmak için doğrudan çağırılır. Temel bir bakış için <xref:System.ServiceModel.ClientBase%601> nesneleri bkz [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 İkinci tür çağrısından çalışma zamanında oluşturulan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> yöntemi. Uygulamalar genellikle sıkı bir iletişim ayrıntıları denetimi ile ilgili olarak adlandırılan bu istemci türü kullanmak bir *istemci kanal nesnesi*, temel alınan istemci çalışma zamanı ve kanal'den fazla doğrudan etkileşim sağlar sistemi.  
  
## <a name="channel-factories"></a>Kanal fabrikaları  
 Temel çalışma zamanı yönelik istemci çağrılarını destekleyen oluşturmaktan sorumlu sınıftır <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıfı. WCF istemci nesneleri hem de WCF istemcisi kanal nesneleri kullanımı bir <xref:System.ServiceModel.ChannelFactory%601> örnekleri; oluşturmak için nesne <xref:System.ServiceModel.ClientBase%601> türetilmiş istemci nesnesini kanal fabrikası işlenmesini saklar, ancak çeşitli senaryolar için mükemmel bir şekilde kullanmak makul kanal fabrikası doğrudan. Yaygın senaryo, sürekli olarak yeni istemci var olan bir fabrikadan kanal oluşturma işlemidir. İstemci nesnesi kullanıyorsanız, arka plandaki kanal fabrikası bir WCF istemcisi nesnesinden çağırarak elde edebileceğiniz <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> özelliği.  
  
 İstemci yeni örneklerini çağırmadan önce bunları için sağlanan yapılandırma için Kanallar oluşturma hakkında kanal fabrikaları Anımsanması gereken önemli şey olan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Bir kez çağırmanız <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (veya <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, ya da bir WCF istemci nesnesi üzerinde herhangi bir işlem), kanal fabrikası değiştirmek ve yalnızca hedef uç nokta adresini değiştirmekte olduğunuz olsa bile farklı hizmet örneklerine kanalları bekler. İstemci nesnesi veya istemci kanal ile farklı bir yapılandırma oluşturmak istiyorsanız, öncelikle yeni bir kanal fabrikası oluşturmanız gerekir.  
  
 WCF istemci nesneleri ve WCF istemci kanalları kullanarak çeşitli sorunlar hakkında daha fazla bilgi için bkz. [WCF istemci kullanarak hizmetlere erişme](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 Aşağıdaki iki bölümü oluşturulmasını ve WCF istemci kanal nesnelerinin kullanımını açıklar.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF istemcisi kanalını nesnesi oluşturma  
 İstemci kanal kullanımını göstermek için aşağıdaki hizmet sözleşmesi oluşturulan varsayılır.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Bağlanmak için bir `ISampleService` hizmet, doğrudan bir kanal fabrikası ile oluşturulan sözleşme arabirimi kullanın (<xref:System.ServiceModel.ChannelFactory%601>). Oluşturup belirli bir sözleşme için kanal fabrikası yapılandırdıktan sonra çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> istemci ile iletişim kurmak için kullanabileceğiniz kanal nesneleri döndürmek için yöntemin bir `ISampleService` hizmeti.  
  
 Kullanırken <xref:System.ServiceModel.ChannelFactory%601> sınıfı e dönüştürmelisiniz hizmet sözleşme arabirimi ile <xref:System.ServiceModel.IClientChannel> açıkça açmak, kapatmak veya kanal iptal etmek için arabirim. Çalışmak daha kolay hale getirmek için Svcutil.exe aracını da her iki hizmet sözleşme arabirimi uygulayan bir yardımcı arabirimi oluşturur ve <xref:System.ServiceModel.IClientChannel> dönüştürme yapmak zorunda kalmadan istemci kanal altyapısıyla etkileşim sağlamak için. Aşağıdaki kod önceki hizmet sözleşmesi uygulayan yardımcı istemci kanal tanımı gösterilmektedir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF istemcisi kanalını nesnesi oluşturma  
 İstemci kanal bağlanmak için kullanılacak bir `ISampleService` hizmet, oluşturulan sözleşme arabirimi (veya Yardımcısı sürüm) bir kanal fabrikası ile doğrudan sözleşme arabirim türü tür parametresi geçirerek kullanın. Belirli bir sözleşme için kanal fabrikası oluşturulup yapılandırıldıktan sonra çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> istemci ile iletişim kurmak için kullanabileceğiniz kanal nesneleri döndürmek için yöntemin bir `ISampleService` hizmeti.  
  
 İstemci kanal nesneler oluşturduğunuzda, uygulama <xref:System.ServiceModel.IClientChannel> ve sözleşme arabirimi. Bu nedenle, bu sözleşme destekleyen bir hizmetle etkileşim operations doğrudan çağırmak için bunları kullanabilirsiniz.  
  
 İstemci nesneleri ve istemci kanal nesneleri kullanarak arasında yalnızca bir denetimin ve geliştiriciler için kullanım kolaylığı farktır. Sınıflar ve nesneler ile çalışırken rahatsanız birçok geliştiricinin WCF istemci nesnesi yerine WCF istemcisi kanalını kullanmayı tercih eder.  
  
 Bir örnek için bkz [nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
