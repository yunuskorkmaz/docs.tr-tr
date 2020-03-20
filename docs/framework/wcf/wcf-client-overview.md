---
title: WCF İstemcisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 7905d540e0f06dd2863cf80381210307e3021918
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183065"
---
# <a name="wcf-client-overview"></a>WCF İstemcisi Genel Bakış
Bu bölümde istemci uygulamalarının ne yaptığı, windows communication foundation (WCF) istemcisini nasıl yapılandırılabilmek, oluşturulmak ve kullanmak ve istemci uygulamalarının nasıl güvence altına alabilmek için kullanılacağı açıklanmaktadır.  
  
## <a name="using-wcf-client-objects"></a>WCF İstemci Nesnelerini Kullanma  
 İstemci uygulaması, başka bir uygulamayla iletişim kurmak için WCF istemcisi kullanan yönetilen bir uygulamadır. WCF hizmeti için istemci uygulaması oluşturmak için aşağıdaki adımlar gerektirir:  
  
1. Hizmet bitiş noktası için hizmet sözleşmesi, bağlamalar ve adres bilgilerini edinin.  
  
2. Bu bilgileri kullanarak bir WCF istemcisi oluşturun.  
  
3. Arama operasyonları.  
  
4. WCF istemci nesnesini kapatın.  
  
 Aşağıdaki bölümlerde bu adımları tartışmak ve aşağıdaki konulara kısa girişler sağlar:  
  
- Hataları işleme.  
  
- İstemleri yapılandırma ve güvence altına alma.  
  
- Çift yönlü hizmetler için geri arama nesneleri oluşturma.  
  
- Hizmetleri eşzamanlı olarak arama.  
  
- İstemci kanallarını kullanarak hizmetleri arama.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Hizmet Sözleşmesi, Ciltler ve Adresler Edinin  
 WCF'de, hizmetler ve istemciler yönetilen öznitelikleri, arabirimleri ve yöntemleri kullanarak sözleşmeleri modeller. İstemci uygulamasındaki bir hizmete bağlanmak için hizmet sözleşmesinin tür bilgilerini almanız gerekir. Genellikle, bunu, hizmetten meta veri indiren, seçtiğiniz dilde yönetilen bir kaynak kodu dosyasına dönüştüren ve WCF istemci nesnenizi yapılandırmak için kullanabileceğiniz bir istemci uygulama yapılandırma dosyası oluşturan [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak yaparsınız. Örneğin, bir `MyCalculatorService`'yi çağırmak için bir WCF istemcisi nesnesi oluşturacaksanız ve bu `http://computerName/MyCalculatorService/Service.svc?wsdl`hizmete ait meta verilerin , yönetilen kodda hizmet `ClientCode.vb` sözleşmesi içeren bir dosyayı elde etmek için Svcutil.exe'nin nasıl kullanılacağını aşağıdaki kod örneğinde yayımlandığını biliyorsanız.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Bu sözleşme kodunu istemci uygulamasına veya istemci uygulamasının wcf istemci nesnesi oluşturmak için kullanabileceği başka bir derlemeye ekleyebilirsiniz. Aygıta düzgün bir şekilde bağlanmak için istemci nesnesini yapılandırmak için yapılandırma dosyasını kullanabilirsiniz.  
  
 Bu işlemin bir örneği için [bkz: İstemci oluşturma](how-to-create-a-wcf-client.md). Sözleşmeler hakkında daha fazla bilgi için [Sözleşmeler'e](./feature-details/contracts.md)bakın.  
  
## <a name="create-a-wcf-client-object"></a>WCF İstemci Nesnesi Oluşturma  
 WCF istemcisi, istemcinin uzak hizmetle iletişim kurmak için kullanabileceği bir biçimde bir WCF hizmetini temsil eden yerel bir nesnedir. WCF istemci türleri hedef hizmet sözleşmesini uygular, bu nedenle bir tane oluşturup yapılandırdığınızda, istemci nesnesini doğrudan hizmet işlemlerini çağırmak için kullanabilirsiniz. WCF çalışma süresi yöntem çağrılarını iletilere dönüştürür, servise gönderir, yanıtı dinler ve bu değerleri iade değerleri veya `out` `ref` parametreler olarak WCF istemci nesnesine döndürür.  
  
 Hizmetlere bağlanmak ve hizmetleri kullanmak için WCF istemci kanal nesnelerini de kullanabilirsiniz. Ayrıntılar için [WCF İstemci Mimarisi'ne](./feature-details/client-architecture.md)bakın.  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni Bir WCF Nesnesi Oluşturma  
 Bir <xref:System.ServiceModel.ClientBase%601> sınıfın kullanımını göstermek için, bir hizmet uygulamasından aşağıdaki basit hizmet sözleşmesinin oluşturulduğunu varsayalım.  
  
> [!NOTE]
> WCF istemcinizi oluşturmak için Visual Studio kullanıyorsanız, projenize bir hizmet başvurusu eklediğinizde nesneler nesne tarayıcısına otomatik olarak yüklenir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio kullanmıyorsanız, genişletilmiş türü <xref:System.ServiceModel.ClientBase%601> ve hizmet sözleşmesi arabirimini `ISampleService`bulmak için oluşturulan sözleşme kodunu inceleyin. Bu durumda, bu tür aşağıdaki kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf, yapılandırılan ve daha sonra türünün `ISampleService`bir hizmetine bağlanmak için kullanılan, yapılandırılan, yapılandırılan ve yerel bir nesne olarak oluşturulabilir.  
  
 Önce WCF istemci nesnenizi oluşturmanız ve sonra kullanmanız ve tek bir deneme/yakalama bloğunda kapatmanız önerilir. Belirli hata modlarında özel durumları maskeleyebilir, çünkü `using` deyimi (Visual`Using` Basic'te) kullanmamalısınız. Daha fazla bilgi için, WCF istemci kaynaklarını serbest bırakmak için aşağıdaki bölümlere ve [Yakın ve İptal'i kullan'a](./samples/use-close-abort-release-wcf-client-resources.md)bakın.  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, Ciltler ve Adresler  
 Bir WCF istemci nesnesi oluşturamadan önce istemci nesnesini yapılandırmanız gerekir. Özellikle, kullanmak için bir hizmet *bitiş noktası* olmalıdır. Bitiş noktası, hizmet sözleşmesi, bağlama ve adresin birleşimidir. (Uç noktalar hakkında daha fazla bilgi için [bkz: Uç Noktalar: Adresler, Ciltler ve Sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgiler, Svcutil.exe aracının [ \<](../configure-apps/file-schema/wcf/endpoint-of-client.md) oluşturduğu gibi istemci uygulama yapılandırma dosyasındaki bitiş noktası>öğesinde bulunur ve istemci nesnenizi oluşturduğunuzda otomatik olarak yüklenir. Her iki WCF istemci türüde de bu bilgileri programlı olarak belirtmenizi sağlayan aşırı yüklemeler vardır.  
  
 Örneğin, önceki örneklerde kullanılan `ISampleService` bir yapılandırma dosyası aşağıdaki uç nokta bilgilerini içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma `<client>` dosyası, öğedeki hedef bitiş noktasını belirtir. Birden çok hedef uç noktası kullanma <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> hakkında <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> daha fazla bilgi için, oluşturuculara veya kuruculara bakın.  
  
## <a name="calling-operations"></a>Arama İşlemleri  
 Bir istemci nesnesi oluşturulduktan ve yapılandırıldıktan sonra, bir try/catch bloğu oluşturun, nesneleri yerel olsaydı aynı şekilde işlemleri arayın ve WCF istemci nesnesini kapatın. İstemci uygulaması ilk işlemi aradığında, WCF temel kanalı otomatik olarak açar ve nesne geri dönüştürüldüğünde temel kanal kapatılır. (Alternatif olarak, kanalı diğer işlemleri çağırmadan önce veya sonraki olarak açıkça açıp kapatabilirsiniz.)  
  
 Örneğin, aşağıdaki hizmet sözleşmeniz varsa:  
  
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
  
 Aşağıdaki kod örneğinde gösterildiği gibi, bir WCF istemci nesnesi oluşturup yöntemlerini çağırarak işlemleri çağırabilirsiniz. WCF istemci nesnesinin açılması, çağrılması ve kapatılmasının tek bir try/catch bloğu içinde gerçekleştiğini unutmayın. Daha fazla bilgi için [wcf istemcisi kullanan Hizmetlere Erişim](./feature-details/accessing-services-using-a-client.md) ve [WCF istemci kaynaklarını serbest bırakmak için Kapat ve İptal'i kullanın.](./samples/use-close-abort-release-wcf-client-resources.md)  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları İşleme  
 Bir istemci uygulamasında, temel istemci kanalını açarken (bir işlemi açıkça veya otomatik olarak çağırarak), istemci veya kanal nesnesini kullanarak işlemleri çağırırken veya temel istemci kanalını kapatırken oluşabilir. En azından uygulamaların, işlemler tarafından döndürülen <xref:System.TimeoutException?displayProperty=nameWithType> <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> SOAP hataları sonucunda <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> atılan nesnelere ek olarak olası ve özel durumları da ele almayı beklemesi önerilir. Operasyon sözleşmesinde belirtilen SOAP arızaları, tür parametresi SOAP arızasının detay türü olarak <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> istemci uygulamalarına yükseltilir. İstemci uygulamasındaki hata koşullarını işleme hakkında daha fazla bilgi için [bkz.](sending-and-receiving-faults.md) Tam bir örnek için, istemcideki hataların nasıl işleyeceğini gösterir, [bkz.](./samples/expected-exceptions.md)  
  
## <a name="configuring-and-securing-clients"></a>İstemcileri Yapılandırma ve Güvence Altına Alma  
 İstemci yapılandırma, istemci oluşturucuları ve özelliklerini kullanarak bu bilgileri programlı olarak yükleyebiliyor sanız, istemci veya kanal nesnesi için genellikle bir yapılandırma dosyasından hedef uç nokta bilgilerinin gerekli yüklenmesiyle başlar. Ancak, belirli istemci davranışını etkinleştirmek ve birçok güvenlik senaryosu için ek yapılandırma adımları gereklidir.  
  
 Örneğin, hizmet sözleşmeleri için güvenlik gereksinimleri hizmet sözleşmesi arabiriminde beyan edilir ve Svcutil.exe bir yapılandırma dosyası oluşturduysa, bu dosya genellikle hizmetin güvenlik gereksinimlerini destekleyebilecek bir bağlama içerir. Ancak bazı durumlarda, istemci kimlik bilgilerini yapılandırmak gibi daha fazla güvenlik yapılandırması gerekebilir. WCF istemcileri için güvenlik yapılandırması hakkında tam bilgi için [bkz.](securing-clients.md)  
  
 Ayrıca, istemci uygulamalarında özel çalışma zamanı davranışları gibi bazı özel değişiklikler etkinleştirilebilir. Özel bir istemci davranışının nasıl yapılandırılabildiğini hakkında daha fazla bilgi [için](configuring-client-behaviors.md)bkz.  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift Yönlü Hizmetler için Geri Arama Nesneleri Oluşturma  
 Çift yönlü hizmetler, hizmetin sözleşmenin gereklerine göre arama yapması için bir geri arama nesnesi sağlamak için istemci uygulamasının uygulaması gereken bir geri arama sözleşmesi belirtir. Geri arama nesneleri tam hizmet olmasa da (örneğin, geri arama nesnesi olan bir kanalı başlatamazsınız), uygulama ve yapılandırma amacıyla bir hizmet türü olarak düşünülebilir.  
  
 Çift yönlü hizmetlerin istemcileri şunları yapmalıdır:  
  
- Bir geri arama sözleşmesi sınıfı uygulayın.  
  
- Geri arama sözleşmesi uygulama sınıfının bir örneğini <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> oluşturun ve WCF istemci oluşturucuya geçtiğiniz nesneyi oluşturmak için kullanın.  
  
- İşlemleri çağırın ve operasyon geri aramalarını işleyin.  
  
 Duplex WCF istemci nesneleri, geri arama hizmetinin yapılandırması da dahil olmak üzere geri aramaları desteklemek için gerekli işlevselliği ortaya çıkarmaları dışında, çift yönlü olmayan karşılıkları gibi çalışır.  
  
 Örneğin, geri arama sınıfındaöz özellikleri kullanarak geri arama nesnesi çalışma zamanı davranışının <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> çeşitli yönlerini denetleyebilirsiniz. Başka bir örnek, <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> özel durum bilgilerinin geri arama nesnesini arayan hizmetlere geri dönmesini etkinleştirmek için sınıfın kullanılmasıdır. Daha fazla bilgi için [Çift Yönlü Hizmetler'e](./feature-details/duplex-services.md)bakın. Tam bir örnek için [Çift Yönlü'ye](./samples/duplex.md)bakın.  
  
 Internet Information Services (IIS) 5.1 çalıştıran Windows XP bilgisayarlarda, çift <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> yönlü istemciler sınıfı kullanarak bir istemci taban adresi belirtmelidir veya bir özel durum atılır. Aşağıdaki kod örneği, bunu kod da nasıl yapacağını gösterir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod, yapılandırma dosyasında bunun nasıl yapılacağını gösterir  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri Eşzamanlı Olarak Arama  
 İşlemlerin nasıl adlandırılması tamamen istemci geliştiriciye bağlıdır. Bunun nedeni, bir işlemi oluşturan iletilerin yönetilen kodla ifade edildiğinde eşzamanlı veya eşzamanlı yöntemlerle eşlenebileceğidir. Bu nedenle, işlemleri eşsenkronize olarak çağıran bir istemci oluşturmak istiyorsanız, `/async` seçeneği kullanarak eşzamanlı istemci kodu oluşturmak için Svcutil.exe'yi kullanabilirsiniz. Daha fazla bilgi için [bkz: Hizmet İşlemleri'ni eşit bir şekilde arayın.](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF İstemci Kanallarını Kullanarak Hizmetleri Arama  
 WCF istemci <xref:System.ServiceModel.ClientBase%601>türleri, temel kanal <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> sistemini ortaya çıkarmak için kendi arabiriminden türetilen genişletmeyi sağlar. <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Sınıfla hedef hizmet sözleşmesini kullanarak hizmetleri çağırabilirsiniz. Ayrıntılar için [WCF İstemci Mimarisi'ne](./feature-details/client-architecture.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
