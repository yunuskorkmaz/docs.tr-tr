---
title: WCF İstemcisi Genel Bakış
description: İstemci uygulamalarının ne yaptığını, bir WCF istemcisi yapılandırma, oluşturma ve kullanma ve istemci uygulamalarının güvenliğini sağlama hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: c66541f95d04373a9a29fafe58528872335936c4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245926"
---
# <a name="wcf-client-overview"></a>WCF istemcisine genel bakış

Bu bölümde, istemci uygulamalarının ne yaptığını, bir Windows Communication Foundation (WCF) istemcisini yapılandırma, oluşturma ve kullanma ve istemci uygulamalarının güvenliğini sağlama işlemlerinin nasıl yapılacağı açıklanmaktadır.  
  
## <a name="using-wcf-client-objects"></a>WCF Istemci nesnelerini kullanma  
 İstemci uygulaması, başka bir uygulamayla iletişim kurmak için WCF istemcisi kullanan yönetilen bir uygulamadır. WCF hizmeti için bir istemci uygulaması oluşturmak aşağıdaki adımları gerektirir:  
  
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
 WCF 'de, hizmetler ve istemciler, yönetilen öznitelikler, arabirimler ve yöntemler kullanılarak sözleşmeleri modelleyebilir. Bir istemci uygulamasındaki bir hizmete bağlanmak için, hizmet sözleşmesinin tür bilgilerini edinmeniz gerekir. Genellikle, [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak hizmet sözleşmesinin tür bilgilerini elde edersiniz. Yardımcı programı hizmetten meta verileri indirir, bunu seçtiğiniz dilde bir yönetilen kaynak kodu dosyasına dönüştürür ve WCF istemci nesneniz yapılandırmak için kullanabileceğiniz bir istemci uygulama yapılandırma dosyası oluşturur. Örneğin, çağırmak için bir WCF istemci nesnesi oluşturacaksanız `MyCalculatorService` ve bu hizmet için meta verilerin ' de yayımlandığını biliyorsanız `http://computerName/MyCalculatorService/Service.svc?wsdl` , aşağıdaki kod örneği, `ClientCode.vb` Yönetilen koddaki hizmet sözleşmesini içeren bir dosyayı almak için Svcutil.exe nasıl kullanacağınızı gösterir.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Bu sözleşme kodunu istemci uygulamasına ya da istemci uygulamanın daha sonra bir WCF istemci nesnesi oluşturmak için kullanabileceği başka bir derlemeye derleyebilirsiniz. İstemci nesnesini hizmete düzgün şekilde bağlanacak şekilde yapılandırmak için yapılandırma dosyasını kullanabilirsiniz.  
  
 Bu işleme bir örnek için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md). Sözleşmeler hakkında daha fazla bilgi için bkz. [sözleşmeler](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>WCF Istemci nesnesi oluşturma  
 WCF istemcisi, istemcinin uzak hizmetle iletişim kurmak için kullanabileceği bir formda WCF hizmetini temsil eden yerel bir nesnedir. WCF istemci türleri hedef hizmet sözleşmesini uygular, bu nedenle bir tane oluşturup yapılandırdığınızda, istemci nesnesini doğrudan hizmet işlemlerini çağırmak için kullanabilirsiniz. WCF çalışma süresi, Yöntem çağrılarını iletilere dönüştürür, bunları hizmete gönderir, yanıtı dinler ve bu değerleri, dönüş değerleri veya parametreler olarak WCF istemci nesnesine döndürür `out` `ref` .  
  
 Ayrıca, ile bağlantı kurmak ve hizmetleri kullanmak için WCF istemci kanalı nesnelerini de kullanabilirsiniz. Ayrıntılar için bkz. [WCF Istemci mimarisi](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni bir WCF nesnesi oluşturma  
 Bir sınıfın kullanımını göstermek için <xref:System.ServiceModel.ClientBase%601> , bir hizmet uygulamasından aşağıdaki basit hizmet sözleşmesinin oluşturulduğunu varsayın.  
  
> [!NOTE]
> WCF istemcinizi oluşturmak için Visual Studio kullanıyorsanız, projenize bir hizmet başvurusu eklediğinizde nesneler nesne tarayıcısına otomatik olarak yüklenir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio kullanmıyorsanız, <xref:System.ServiceModel.ClientBase%601> ve hizmet sözleşmesi arabirimini genişleten türü bulmak için oluşturulan sözleşme kodunu inceleyin `ISampleService` . Bu durumda, bu tür aşağıdaki kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf, yapılandırılmış oluşturuculardan biri kullanılarak yerel bir nesne olarak oluşturulabilir ve sonra türün bir hizmetine bağlanmak için kullanılır `ISampleService` .  
  
 Önce WCF istemci nesneniz oluşturmanız ve ardından bunu kullanarak tek bir try/catch bloğu içinde kapatmanız önerilir. `using` `Using` Belirli hata modlarında özel durumları maskeleyip, (Visual Basic) ifadesini kullanmayın. Daha fazla bilgi için, aşağıdaki bölümlere ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal](./samples/use-close-abort-release-wcf-client-resources.md)' i kullanma konusuna bakın.  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, bağlamalar ve adresler  
 Bir WCF istemci nesnesi oluşturabilmeniz için önce istemci nesnesini yapılandırmanız gerekir. Özellikle, kullanmak için bir hizmet *uç noktası* olması gerekir. Uç nokta, bir hizmet sözleşmesinin, bağlamanın ve bir adresin birleşimidir. (Uç noktalar hakkında daha fazla bilgi için bkz. [uç noktalar: adresler, bağlamalar ve sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgiler [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-of-client.md) bir istemci uygulama yapılandırma dosyasında bulunur, örneğin Svcutil.exe aracı oluşturulur ve istemci nesneniz oluşturduğunuzda otomatik olarak yüklenir. Her iki WCF istemci türünün de bu bilgileri programlı bir şekilde belirtmenizi sağlayan aşırı yüklemeleri vardır.  
  
 Örneğin, Yukarıdaki örneklerde kullanılan bir oluşturulan yapılandırma dosyası `ISampleService` aşağıdaki uç nokta bilgilerini içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma dosyası, öğesinde bir hedef uç nokta belirtir `<client>` . Birden çok hedef uç nokta kullanma hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> . veya oluşturucuları.  
  
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
  
 Aşağıdaki kod örneğinde gösterildiği gibi, bir WCF istemci nesnesi oluşturup yöntemlerini çağırarak işlemleri çağırabilirsiniz. WCF istemci nesnesini açma, çağırma ve kapatma tek bir try/catch bloğu içinde gerçekleşir. Daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](./feature-details/accessing-services-using-a-client.md) ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal kullanma](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları İşleme  
 Temel alınan istemci kanalını (bir işlem çağırarak açıkça veya otomatik olarak) açarken, işlemleri çağırmak için istemci veya kanal nesnesi kullanılarak veya temel alınan istemci kanalının kapatılması sırasında bir istemci uygulamasında özel durumlar meydana gelebilir. Uygulamaların <xref:System.TimeoutException?displayProperty=nameWithType> , <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> Işlemler tarafından döndürülen soap hatalarının sonucu olarak oluşturulan nesnelere ek olarak olası ve özel durumları işlemek için beklediği en az sayıda uygulama olması önerilir. İşlem sözleşmesinde belirtilen SOAP hataları, istemci uygulamalarına <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi, SOAP hatasının ayrıntı türü olduğu yerde tetiklenir. İstemci uygulamasında hata koşullarını işleme hakkında daha fazla bilgi için bkz. [hataları gönderme ve alma](sending-and-receiving-faults.md). Tüm bir örnek için, istemcideki hataların nasıl işleneceğini gösterir, bkz. [Beklenen özel durumlar](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Istemcileri yapılandırma ve güvenli hale getirme  
 Bir istemciyi yapılandırmak, genellikle bir yapılandırma dosyasından, istemci veya kanal nesnesi için gerekli hedef uç nokta bilgilerinin yüklenmesi ile başlar, ancak istemci oluşturucular ve özellikler kullanarak bu bilgileri program aracılığıyla da yükleyebilirsiniz. Ancak, bazı istemci davranışlarını etkinleştirmek ve birçok güvenlik senaryosu için ek yapılandırma adımları gereklidir.  
  
 Örneğin, hizmet sözleşmeleri için güvenlik gereksinimleri hizmet sözleşmesi arabiriminde belirtilir ve Svcutil.exe bir yapılandırma dosyası oluşturulduysa, bu dosya genellikle hizmetin güvenlik gereksinimlerini destekleyebilen bir bağlama içerir. Ancak bazı durumlarda, istemci kimlik bilgilerini yapılandırma gibi daha fazla güvenlik yapılandırması gerekebilir. WCF istemcileri için güvenlik yapılandırması hakkında tüm bilgiler için bkz. [Istemcileri güvenli hale getirme](securing-clients.md).  
  
 Ayrıca, özel çalışma zamanı davranışları gibi bazı özel değişiklikler istemci uygulamalarında etkinleştirilebilir. Özel bir istemci davranışının nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [Istemci davranışlarını yapılandırma](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma nesneleri oluşturma  
 Çift yönlü hizmetler, hizmetin sözleşme gereksinimlerine göre çağırması için bir geri çağırma nesnesi sağlamak üzere istemci uygulamanın uygulaması gereken bir geri çağırma anlaşması belirtir. Geri çağırma nesneleri tam hizmet olmasa da (örneğin, geri çağırma nesnesi olan bir kanal başlatamazsınız), uygulama ve yapılandırma amaçları doğrultusunda bir hizmet türü olarak düşünülebilir.  
  
 Çift yönlü hizmetlerin istemcileri şunları içermelidir:  
  
- Bir geri çağırma sözleşmesi sınıfı uygulayın.  
  
- Geri çağırma sözleşmesi uygulama sınıfının bir örneğini oluşturun ve <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> WCF istemci oluşturucusuna geçirdiğiniz nesneyi oluşturmak için bunu kullanın.  
  
- İşlemleri çağır ve işlem geri çağırmaları işleme.  
  
 Çift yönlü WCF istemci nesneleri, geri arama hizmeti yapılandırması da dahil olmak üzere geri çağırmaları desteklemek için gereken işlevselliği kullanıma sundukları özel durum ile çift yönlü olmayan karşılıkları gibi çalışır.  
  
 Örneğin, geri çağırma sınıfında özniteliğin özelliklerini kullanarak geri çağırma nesnesi çalışma zamanı davranışının çeşitli yönlerini denetleyebilirsiniz <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> . Diğer bir örnek, <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> geri çağırma nesnesini çağıran hizmetlere özel durum bilgilerinin döndürülmesini sağlamak için sınıfının kullanımı. Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md). Tüm bir örnek için bkz. [çift yönlü](./samples/duplex.md).  
  
 Internet Information Services (IIS) 5,1 çalıştıran Windows XP bilgisayarlarda çift yönlü istemciler, sınıfı kullanarak bir istemci temel adresi belirtmelidir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> veya bir özel durum oluşturulur. Aşağıdaki kod örneği, kodda nasıl yapılacağını gösterir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod, bir yapılandırma dosyasında bunun nasıl yapılacağını gösterir  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri zaman uyumsuz olarak çağırma  
 İşlemler çağrıldığında istemci geliştiricisine tamamen aynıdır. Bunun nedeni, bir işlemi oluşturan iletilerin yönetilen kodda ifade edildiğinde zaman uyumlu veya zaman uyumsuz yöntemlerle eşlenmesine olanak sağlar. Bu nedenle, işlemleri zaman uyumsuz olarak çağıran bir istemci oluşturmak istiyorsanız seçeneğini kullanarak zaman uyumsuz istemci kodu oluşturmak için Svcutil.exe kullanabilirsiniz `/async` . Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF Istemci kanalları kullanarak hizmetleri çağırma  
 WCF istemci türleri genişletilir <xref:System.ServiceModel.ClientBase%601> , bu, kendisini <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> temel alınan Kanal sistemini kullanıma sunmak için arabiriminden türetilir. Sınıfı ile hedef hizmet sözleşmesini kullanarak hizmetleri çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> . Ayrıntılar için bkz. [WCF Istemci mimarisi](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
