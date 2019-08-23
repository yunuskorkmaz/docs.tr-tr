---
title: WCF İstemcisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: adaaca596650c5bff486bd0c295c4f840ae58051
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916879"
---
# <a name="wcf-client-overview"></a>WCF İstemcisi Genel Bakış
Bu bölümde, istemci uygulamalarının ne yaptığını, bir Windows Communication Foundation (WCF) istemcisini yapılandırma, oluşturma ve kullanma ve istemci uygulamalarının güvenliğini sağlama işlemlerinin nasıl yapılacağı açıklanmaktadır.  
  
## <a name="using-wcf-client-objects"></a>WCF Istemci nesnelerini kullanma  
 İstemci uygulaması, başka bir uygulamayla iletişim kurmak için WCF istemcisi kullanan yönetilen bir uygulamadır. Bir WCF hizmeti için bir istemci uygulaması oluşturmak için aşağıdaki adımları gerektirir:  
  
1. Hizmet uç noktası için hizmet sözleşmesini, bağlamaları ve adres bilgilerini alın.  
  
2. Bu bilgileri kullanarak bir WCF istemcisi oluşturun.  
  
3. Çağrı işlemleri.  
  
4. WCF istemci nesnesini kapatın.  
  
 Aşağıdaki bölümlerde bu adımlar ele alınmaktadır ve aşağıdaki sorunlar için kısa tanıtımlar sağlanmaktadır:  
  
- Hataları işleme.  
  
- İstemcileri yapılandırma ve güvenli hale getirme.  
  
- Çift yönlü hizmetler için geri çağırma nesneleri oluşturma.  
  
- Hizmetler zaman uyumsuz olarak çağrılıyor.  
  
- İstemci kanalları kullanarak hizmetleri çağırma.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Hizmet sözleşmesini, bağlamaları ve adresleri alma  
 WCF 'de, hizmetler ve istemciler, yönetilen öznitelikler, arabirimler ve yöntemler kullanılarak sözleşmeleri modelleyebilir. Bir istemci uygulamasındaki bir hizmete bağlanmak için, hizmet sözleşmesinin tür bilgilerini edinmeniz gerekir. Genellikle bunu, hizmetten meta verileri indiren [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak yapar, bunu istediğiniz dilde bir yönetilen kaynak kodu dosyasına dönüştürür ve bir istemci uygulama yapılandırma dosyası oluşturur Bu, WCF istemci nesneniz yapılandırmak için kullanabilirsiniz. Örneğin, çağırmak `MyCalculatorService`için bir WCF istemci nesnesi oluşturacaksanız ve bu hizmet için meta verilerin `http://computerName/MyCalculatorService/Service.svc?wsdl`' de yayımlandığını biliyorsanız, aşağıdaki kod örneği, bir `ClientCode.vb` dosyayı almak için Svcutil. exe ' nin nasıl kullanılacağını göstermektedir. Yönetilen koddaki hizmet sözleşmesini içerir.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Bu sözleşme kodunu istemci uygulamasına ya da istemci uygulamanın daha sonra bir WCF istemci nesnesi oluşturmak için kullanabileceği başka bir derlemeye derleyebilirsiniz. İstemci nesnesini hizmete düzgün şekilde bağlanacak şekilde yapılandırmak için yapılandırma dosyasını kullanabilirsiniz.  
  
 Bu işleme bir örnek için bkz [. nasıl yapılır: Istemci](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)oluşturun. Sözleşmeler hakkında daha fazla bilgi için bkz. [sözleşmeler](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>WCF Istemci nesnesi oluşturma  
 WCF istemcisi, istemcinin uzak hizmetle iletişim kurmak için kullanabileceği bir formda WCF hizmetini temsil eden yerel bir nesnedir. WCF istemci türleri hedef hizmet sözleşmesini uygular, bu nedenle bir tane oluşturup yapılandırdığınızda, istemci nesnesini doğrudan hizmet işlemlerini çağırmak için kullanabilirsiniz. WCF çalışma süresi, Yöntem çağrılarını iletilere dönüştürür, bunları hizmete gönderir, yanıtı dinler ve bu değerleri, dönüş değerleri veya `out` `ref` parametreler olarak WCF istemci nesnesine döndürür.  
  
 Ayrıca, ile bağlantı kurmak ve hizmetleri kullanmak için WCF istemci kanalı nesnelerini de kullanabilirsiniz. Ayrıntılar için bkz. [WCF Istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni bir WCF nesnesi oluşturma  
 Bir <xref:System.ServiceModel.ClientBase%601> sınıfın kullanımını göstermek için, bir hizmet uygulamasından aşağıdaki basit hizmet sözleşmesinin oluşturulduğunu varsayın.  
  
> [!NOTE]
> WCF istemcinizi oluşturmak için Visual Studio kullanıyorsanız, projenize bir hizmet başvurusu eklediğinizde nesneler nesne tarayıcısına otomatik olarak yüklenir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio kullanmıyorsanız, ve hizmet sözleşmesi arabirimini <xref:System.ServiceModel.ClientBase%601> `ISampleService`genişleten türü bulmak için oluşturulan sözleşme kodunu inceleyin. Bu durumda, bu tür aşağıdaki kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf, yapılandırılmış oluşturuculardan biri kullanılarak yerel bir nesne olarak oluşturulabilir ve sonra türün `ISampleService`bir hizmetine bağlanmak için kullanılır.  
  
 Önce WCF istemci nesneniz oluşturmanız ve ardından bunu kullanarak tek bir try/catch bloğu içinde kapatmanız önerilir. Belirli hata modlarında özel durumları `using` maskeleyebilir`Using` olduğundan, (Visual Basic) ifadesini kullanmayın. Daha fazla bilgi için, aşağıdaki bölümlere ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)' i kullanma konusuna bakın.  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, bağlamalar ve adresler  
 Bir WCF istemci nesnesi oluşturabilmeniz için önce istemci nesnesini yapılandırmanız gerekir. Özellikle, kullanmak için bir hizmet *uç noktası* olması gerekir. Uç nokta, bir hizmet sözleşmesinin, bağlamanın ve bir adresin birleşimidir. (Uç noktalar hakkında daha fazla bilgi için [bkz. uç noktalar: Adresler, bağlamalar ve sözleşmeler](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgiler, bir istemci uygulama yapılandırma dosyasındaki, Svcutil. exe aracının oluşturduğu ve istemci nesneniz oluştururken otomatik olarak yüklenen [ \<Endpoint >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) öğesinde bulunur. Her iki WCF istemci türünün de bu bilgileri programlı bir şekilde belirtmenizi sağlayan aşırı yüklemeleri vardır.  
  
 Örneğin, Yukarıdaki örneklerde kullanılan bir `ISampleService` oluşturulan yapılandırma dosyası aşağıdaki uç nokta bilgilerini içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma dosyası, `<client>` öğesinde bir hedef uç nokta belirtir. Birden çok hedef uç nokta kullanma hakkında daha fazla bilgi için <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> bkz. <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> veya oluşturucuları.  
  
## <a name="calling-operations"></a>Işlemleri çağırma  
 Bir istemci nesnesi oluşturulup yapılandırıldıktan sonra bir try/catch bloğu oluşturun, işlem, nesne yerelde olacak şekilde çağrı yapın ve WCF istemci nesnesini kapatın. İstemci uygulaması ilk işlemi çağırdığında, WCF otomatik olarak temel alınan kanalı açar ve nesne geri dönüştürüldüğünde temeldeki kanal kapatılır. (Alternatif olarak, diğer işlemleri çağırmak için veya daha sonra kanalı doğrudan açıp kapatabilirsiniz.)  
  
 Örneğin, aşağıdaki hizmet sözleşmesine sahipseniz:  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 Aşağıdaki kod örneğinde gösterildiği gibi, bir WCF istemci nesnesi oluşturup yöntemlerini çağırarak işlemleri çağırabilirsiniz. WCF istemci nesnesinin açma, çağırma ve kapanışının tek bir try/catch bloğu içinde gerçekleştiğini unutmayın. Daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal kullanma](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları İşleme  
 Temel alınan istemci kanalını (bir işlem çağırarak açıkça veya otomatik olarak) açarken, işlemleri çağırmak için istemci veya kanal nesnesi kullanılarak veya temel alınan istemci kanalının kapatılması sırasında bir istemci uygulamasında özel durumlar meydana gelebilir. Uygulamaların, işlemler tarafından döndürülen soap hatalarının sonucu olarak oluşturulan <xref:System.TimeoutException?displayProperty=nameWithType> <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesnelere ek olarak <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> olası ve özel durumları işlemek için beklediği en az sayıda uygulama olması önerilir. İşlem sözleşmesinde belirtilen SOAP hataları, istemci uygulamalarına <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi, SOAP hatasının ayrıntı türü olduğu yerde tetiklenir. İstemci uygulamasında hata koşullarını işleme hakkında daha fazla bilgi için bkz. [hataları gönderme ve alma](../../../docs/framework/wcf/sending-and-receiving-faults.md). Tüm bir örnek için, istemcideki hataların nasıl işleneceğini gösterir, bkz. [Beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Istemcileri yapılandırma ve güvenli hale getirme  
 Bir istemciyi yapılandırmak, genellikle bir yapılandırma dosyasından, istemci veya kanal nesnesi için gerekli hedef uç nokta bilgilerinin yüklenmesi ile başlar, ancak istemci oluşturucular ve özellikler kullanarak bu bilgileri program aracılığıyla da yükleyebilirsiniz. Ancak, bazı istemci davranışlarını etkinleştirmek ve birçok güvenlik senaryosu için ek yapılandırma adımları gereklidir.  
  
 Örneğin, hizmet sözleşmeleri için güvenlik gereksinimleri hizmet sözleşmesi arabiriminde bildirilmiştir ve Svcutil. exe bir yapılandırma dosyası oluşturulduysa, bu dosya genellikle hizmetin güvenlik gereksinimlerini destekleyebilen bir bağlama içerir. Ancak bazı durumlarda, istemci kimlik bilgilerini yapılandırma gibi daha fazla güvenlik yapılandırması gerekebilir. WCF istemcileri için güvenlik yapılandırması hakkında tüm bilgiler için bkz. [Istemcileri güvenli hale getirme](../../../docs/framework/wcf/securing-clients.md).  
  
 Ayrıca, özel çalışma zamanı davranışları gibi bazı özel değişiklikler istemci uygulamalarında etkinleştirilebilir. Özel bir istemci davranışının nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [Istemci davranışlarını yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma nesneleri oluşturma  
 Çift yönlü hizmetler, hizmetin sözleşme gereksinimlerine göre çağırması için bir geri çağırma nesnesi sağlamak üzere istemci uygulamanın uygulaması gereken bir geri çağırma anlaşması belirtir. Geri çağırma nesneleri tam hizmet olmasa da (örneğin, geri çağırma nesnesi olan bir kanal başlatamazsınız), uygulama ve yapılandırma amaçları doğrultusunda bir hizmet türü olarak düşünülebilir.  
  
 Çift yönlü hizmetlerin istemcileri şunları içermelidir:  
  
- Bir geri çağırma sözleşmesi sınıfı uygulayın.  
  
- Geri çağırma sözleşmesi uygulama sınıfının bir örneğini oluşturun ve WCF istemci oluşturucusuna geçirdiğiniz <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> nesneyi oluşturmak için bunu kullanın.  
  
- İşlemleri çağır ve işlem geri çağırmaları işleme.  
  
 Çift yönlü WCF istemci nesneleri, geri arama hizmeti yapılandırması da dahil olmak üzere geri çağırmaları desteklemek için gereken işlevselliği kullanıma sundukları özel durum ile çift yönlü olmayan karşılıkları gibi çalışır.  
  
 Örneğin, geri çağırma sınıfında <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> özniteliğin özelliklerini kullanarak geri çağırma nesnesi çalışma zamanı davranışının çeşitli yönlerini denetleyebilirsiniz. Diğer bir örnek, geri çağırma nesnesini <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> çağıran hizmetlere özel durum bilgilerinin döndürülmesini sağlamak için sınıfının kullanımı. Daha fazla bilgi için bkz. [çift yönlü hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md). Tüm bir örnek için bkz. [çift yönlü](../../../docs/framework/wcf/samples/duplex.md).  
  
 Internet Information Services (IIS) 5,1 çalıştıran Windows XP bilgisayarlarda çift yönlü istemciler, <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sınıfı kullanarak bir istemci temel adresi belirtmelidir veya bir özel durum oluşturulur. Aşağıdaki kod örneği, kodda nasıl yapılacağını gösterir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod, bir yapılandırma dosyasında bunun nasıl yapılacağını gösterir  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri zaman uyumsuz olarak çağırma  
 İşlemler çağrıldığında istemci geliştiricisine tamamen aynıdır. Bunun nedeni, bir işlemi oluşturan iletilerin yönetilen kodda ifade edildiğinde zaman uyumlu veya zaman uyumsuz yöntemlerle eşlenmesine olanak sağlar. Bu nedenle, işlemleri zaman uyumsuz olarak çağıran bir istemci oluşturmak isterseniz, `/async` seçeneğini kullanarak zaman uyumsuz istemci kodu oluşturmak için Svcutil. exe ' yi kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Hizmet Işlemlerini zaman uyumsuz](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)olarak çağırın.  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF Istemci kanalları kullanarak hizmetleri çağırma  
 WCF istemci türleri genişletilir <xref:System.ServiceModel.ClientBase%601>, bu, kendisini temel <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> alınan Kanal sistemini kullanıma sunmak için arabiriminden türetilir. <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Sınıfı ile hedef hizmet sözleşmesini kullanarak hizmetleri çağırabilirsiniz. Ayrıntılar için bkz. [WCF Istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
