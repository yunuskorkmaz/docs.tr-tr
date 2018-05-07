---
title: İstemci Mimarisi
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="client-architecture"></a>İstemci Mimarisi
Uygulamaları Windows Communication Foundation (WCF) istemci nesneleri hizmet işlemleri çağırmak için kullanın. Bu konuda, WCF istemci nesneleri, WCF istemci kanalları ve ilişkilerini temel alınan kanal mimarisinde anlatılmaktadır. WCF istemci nesneleri temel bir genel bakış için bkz: [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md). Kanal katmanını hakkında daha fazla bilgi için bkz: [kanal katmanını genişletme](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Genel Bakış  
 Çalışma zamanı hizmet modeli aşağıdakilerden oluşur WCF istemcileri oluşturur:  
  
-   Uygulama kodunuz gelen çağrıları giden iletilere kapatır ve çıkış parametreleri ve uygulamanızı alabilir dönüş değerleri yanıt iletilerini bırakır hizmet sözleşmesini otomatik olarak oluşturulan istemci uygulaması.  
  
-   Bir denetim arabirim uygulaması (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>), çeşitli arabirimleri gruplandıran ve işlevselliği, istemci oturumu kapatın ve kanal dispose özellikle olanağı denetlemek için erişim sağlar.  
  
-   Yerleşik olan istemci kanal kullanılan bağlama tarafından belirtilen yapılandırma ayarları temel.  
  
 Uygulamaları aracılığıyla ya da isteğe bağlı bu gibi istemcilerde oluşturabilirsiniz bir <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> veya bir örneğini oluşturarak bir <xref:System.ServiceModel.ClientBase%601> türetilmiş sınıf tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu hazır oluşturulan istemci sınıfları kapsüllemek ve temsilci tarafından dinamik olarak oluşturulan bir istemci kanal uygulaması için bir <xref:System.ServiceModel.ChannelFactory>. Dolayısıyla, istemci kanal ve bunları üreten kanal fabrikası bu tartışma için ilgi odak noktası altındadır.  
  
## <a name="client-objects-and-client-channels"></a>İstemci nesneleri ve istemci kanalları  
 WCF istemcileri temel arabirim <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> çekirdek istemci işlevselliğinin yanı sıra temel iletişim nesnesi işlevselliği kullanıma sunan arabirim <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, bağlam işlevselliğini <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>, Genişletilebilir davranışını <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Arabirimi, ancak değil tanımlayan bir hizmet sözleşmesini. Bu hizmet sözleşme arabirimi tarafından bildirilen (genellikle hizmeti meta verileri gibi bir araç kullanılarak oluşturulmuş [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). WCF istemci türlerini genişletmek her ikisi de <xref:System.ServiceModel.IClientChannel> ve uygulamaların doğrudan ve ayrıca operations çağrı yapmasını etkinleştirmek için hedef hizmet sözleşme arabirimi istemci-tarafı çalışma zamanı işlevselliği erişime sahiptir. Bir WCF istemcisi oluşturma sağlar WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> bağlanabilir ve yapılandırılan hizmet uç noktası ile etkileşim nesnelerle çalışma süresi oluşturmak için gereken bilgiler.  
  
 Daha önce belirtildiği gibi iki WCF istemci türlerini da kullanabilmek için önce yapılandırılması gerekir. En basit WCF istemci türlerini türetmek nesneleridir <xref:System.ServiceModel.ClientBase%601> (veya <xref:System.ServiceModel.DuplexClientBase%601> hizmet sözleşmesi çift yönlü sözleşme ise). Bu tür programlı olarak yapılandırılmış bir Oluşturucu kullanarak veya bir yapılandırma dosyası kullanarak oluşturabilirsiniz ve hizmet işlemleri çağırmak için doğrudan çağrılır. Temel bir bakış için <xref:System.ServiceModel.ClientBase%601> nesneleri bkz [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 İkinci türü çağrısından çalışma zamanında oluşturulan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> yöntemi. Genellikle iletişim özellikleri sıkı denetimi ile ilgili uygulamalar olarak adlandırılan bu istemci tür kullanın bir *istemci kanal nesnesi*, temel alınan istemci çalışma zamanı ve kanal'den fazla doğrudan etkileşim sağlar Sistem.  
  
## <a name="channel-factories"></a>Kanal fabrikaları  
 İstemci çağrılarını destekleyen çalıştırma arka plandaki oluşturmaktan sorumlu sınıfı <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıfı. WCF istemci nesneleri ve WCF istemci kanal nesneleri kullanımı bir <xref:System.ServiceModel.ChannelFactory%601> örnekleri; oluşturmak için nesne <xref:System.ServiceModel.ClientBase%601> türetilmiş istemci nesnesi kanal fabrikası işlenmesini saklar, ancak çeşitli senaryoları için kullanılacak mükemmel makul kanal fabrikası doğrudan. Bunun yaygın bir senaryo, sürekli yeni istemci varolan fabrikası'ndan kanallar oluşturmak isteyip istemediğinizi ' dir. İstemci nesnesi kullanıyorsanız, arka plandaki kanal fabrikası bir WCF istemcisi nesneden çağırarak elde edebileceğiniz <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> özelliği.  
  
 İstemci yeni örneklerini arama önce bunları için sağlanan yapılandırma için kanal oluşturmak hakkında kanal fabrikaları anımsaması önemli şey. <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Çağırmanız sonra <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (veya <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, ya da bir WCF istemcisi nesnesi üzerinde herhangi bir işlem), kanal fabrikası değiştirmek ve yalnızca hedef uç nokta adresi değiştiriyorsunuz olsa bile kanalları farklı hizmet örneklerine bekler. Bir istemci nesnesi ya da istemci kanal ile farklı bir yapılandırma oluşturmak istiyorsanız, yeni bir kanal fabrikası önce oluşturmanız gerekir.  
  
 WCF istemci nesneleri ve WCF istemci kanalları kullanarak çeşitli sorunlar hakkında daha fazla bilgi için bkz: [bir WCF istemcisi kullanarak hizmetlere erişme](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 Aşağıdaki iki bölümü oluşturulması ve WCF istemci kanal nesnelerinin kullanımını açıklar.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF istemcisi kanal nesnesi oluşturma  
 İstemci kanal kullanımını anlamak için aşağıdaki hizmet sözleşmesini oluşturulan varsayalım.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Bağlanmak için bir `ISampleService` hizmet, doğrudan bir kanal fabrikası ile oluşturulan sözleşme arabirimi kullanın (<xref:System.ServiceModel.ChannelFactory%601>). Oluşturup belirli bir sözleşme için bir kanal fabrikası yapılandırdıktan sonra çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> istemci ile iletişim kurmak için kullanabileceğiniz kanal nesneler döndürmeye yöntemi bir `ISampleService` hizmet.  
  
 Kullanırken <xref:System.ServiceModel.ChannelFactory%601> sınıfı için atamalısınız hizmet sözleşme arabirimi ile <xref:System.ServiceModel.IClientChannel> açıkça açmak, kapatmak veya kanal iptal etmek için arabirim. Çalışmak kolaylaştırmak için Svcutil.exe aracı ayrıca her iki hizmet sözleşmesi arabirimini uygulayan bir yardımcı arabirimi oluşturur ve <xref:System.ServiceModel.IClientChannel> cast gerek kalmadan istemci kanal altyapısıyla etkileşime geçmesini sağlamak için. Aşağıdaki kod, önceki hizmet sözleşmesini uygulayan bir yardımcı istemci kanal tanımını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF istemcisi kanal nesnesi oluşturma  
 İstemci kanal bağlanmak için kullanılacak bir `ISampleService` hizmet, oluşturulan sözleşme arabirimi (veya Yardımcısı sürüm) doğrudan bir kanal fabrikası sözleşme arabirimi türü tür parametresi geçirme kullanın. Belirli bir sözleşme için bir kanal fabrikası oluşturup yapılandırılmış sonra çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> istemci ile iletişim kurmak için kullanabileceğiniz kanal nesneler döndürmeye yöntemi bir `ISampleService` hizmet.  
  
 İstemci kanal nesneleri oluşturduğunuzda, uygulama <xref:System.ServiceModel.IClientChannel> ve sözleşme arabirimi. Bu nedenle, bu sözleşme destekleyen bir hizmet ile etkileşim işlemleri doğrudan çağırmak için bunları kullanabilirsiniz.  
  
 İstemci ve istemci kanal nesneleri kullanarak arasında yalnızca bir denetim ve geliştiriciler için kullanım kolaylığı farktır. Sınıfları ve nesneleri ile çalışma deneyimliyseniz birçok geliştiriciler yerine WCF istemci kanal WCF istemci nesnesi kullanmayı tercih eder.  
  
 Bir örnek için bkz: [nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
