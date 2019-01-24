---
title: WCF İstemcisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: d67da4cedc4bd9bad468197db4a2ad60d054894a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492604"
---
# <a name="wcf-client-overview"></a>WCF İstemcisi Genel Bakış
Bu bölümde, istemci uygulamaları neler, yapılandırma, oluşturma ve bir Windows Communication Foundation (WCF) istemci kullanın ve istemci uygulamalarının güvenliğini nasıl açıklanmaktadır.  
  
## <a name="using-wcf-client-objects"></a>WCF istemci nesnelerini kullanma  
 Başka bir uygulamayla iletişim kurmak için bir WCF istemcisi kullanan bir yönetilen uygulamayı bir istemci uygulamasıdır. Bir istemci oluşturmak için uygulama bir WCF hizmeti için aşağıdaki adımları gerektirir:  
  
1.  Hizmet sözleşmesi, bağlamalar ve hizmet uç noktası için adres bilgilerini edinin.  
  
2.  Bu bilgileri kullanarak bir WCF istemcisi oluşturma.  
  
3.  İşlemleri çağırın.  
  
4.  WCF istemci nesnesi kapatın.  
  
 Aşağıdaki bölümlerde, şu adımları tartışmak ve kısa tanıtımları aşağıdaki sorunlar için sağlayın:  
  
-   Hataları işleme.  
  
-   Yapılandırma ve istemcileri güvenli hale getirme.  
  
-   Çift yönlü hizmetler için geri çağırma nesnelerinin oluşturuluyor.  
  
-   Hizmetleri zaman uyumsuz olarak çağırma.  
  
-   İstemci kanalları kullanarak arama hizmetleri.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Hizmet sözleşmesi, bağlamalar ve adresleri alın  
 WCF'de, hizmetler ve istemcileri yönetilen öznitelikleri, arabirimler ve yöntemler kullanarak sözleşmeler model. Bir istemci uygulamasındaki bir hizmete bağlanmak için hizmet sözleşmesi için tür bilgilerini edinmeniz gerekir. Genellikle, kullanarak bunu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), meta veri hizmetinden indiren bir yönetilen kaynak kod dosyasını tercih ettiğiniz dilde dönüştürür ve bir istemci oluşturur WCF istemci nesnenizin yapılandırmak için kullanabileceğiniz uygulama yapılandırma dosyası. Çağırmak için WCF istemci nesne oluşturmak için kullanacaksanız, örneğin bir `MyCalculatorService`, ve bu hizmet için meta veriler yayımlanma bildiğiniz `http://computerName/MyCalculatorService/Service.svc?wsdl`, aşağıdaki kod örneğinde elde etmek için Svcutil.exe kullanma işlemini gösterir, ardından bir `ClientCode.vb` dosya yönetilen kod içinde hizmet sözleşmesi içeriyor.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Bu sözleşme kodu, istemci uygulaması veya istemci uygulaması WCF istemci nesne oluşturmak için kullanabileceğiniz başka bir derleme ya da derleyebilirsiniz. Yapılandırma dosyası düzgün hizmetine bağlanmak için istemci nesne yapılandırmak için kullanabilirsiniz.  
  
 Bu işlem bir örnek için bkz [nasıl yapılır: Bir istemci oluşturmanız](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Sözleşmeleri hakkında daha ayrıntılı bilgi için bkz. [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>WCF istemci nesnesi oluşturma  
 Bir WCF istemcisi bir WCF hizmeti istemcisi, Uzak hizmetle iletişim kurmak için kullanabileceğiniz bir formda temsil eden yerel bir nesnedir. WCF istemci türleri uygulayan hedef hizmet sözleşmesi oluşturun ve yapılandırın, ardından istemci nesnesini doğrudan hizmet işlemleri çağırmak için kullanabilirsiniz. Çalışma zamanı WCF yöntem çağrılarını iletilere dönüştürür, bunları hizmetine gönderir, yanıtı dinler ve bu değerleri dönüş değerleri için WCF istemci nesnesi döndürür ya da `out` veya `ref` parametreleri.  
  
 İle bağlanmak ve Hizmetleri kullanarak WCF istemci kanal nesnelerini de kullanabilirsiniz. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni bir WCF nesnesi oluşturma  
 Kullanımını gösteren bir <xref:System.ServiceModel.ClientBase%601> sınıfında, aşağıdaki basit hizmet sözleşmesi, bir hizmet uygulamasından oluşturulan olduğunu varsayın.  
  
> [!NOTE]
>  WCF istemci oluşturmak için Visual Studio kullanıyorsanız, projenize bir hizmet başvurusu eklediğinizde, nesneler nesne tarayıcıda otomatik olarak yüklenir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio kullanmıyorsanız genişleten türünü bulmak için oluşturulan sözleşme kodu inceleyin <xref:System.ServiceModel.ClientBase%601> ve hizmet sözleşme arabirimi `ISampleService`. Bu durumda, bu tür, şu kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf oluşturucuları kullanarak yerel bir nesne oluşturulur, yapılandırılmış ve ardından türünde bir hizmete bağlanmak için kullanılan `ISampleService`.  
  
 İlk olarak, WCF istemci nesnesi oluşturun ve daha sonra kullanmak ve tek bir try/catch bloğu içinde kapatın, önerilir. Kullanmamalısınız `using` deyimi (`Using` Visual Basic'te) için belirli hata modlarını özel durumları maskeleyebilir. Daha fazla bilgi için aşağıdaki bölümlere bakın yanı [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, bağlamalar ve adresleri  
 WCF istemci nesnesi oluşturmadan önce istemci nesnesini yapılandırmanız gerekir. Özellikle, bir hizmete sahip olmaları gerekir *uç nokta* kullanılacak. Bir uç nokta, hizmet sözleşmesi, bağlama ve bir adresi birleşimidir. (Uç noktaları hakkında daha fazla bilgi için bkz. [uç noktalar: Adresler, bağlamalar ve sözleşmeleri](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgiler şurada bulunur [ \<uç noktası >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) öğesi gibi Svcutil.exe aracını oluşturur ve istemci oluşturduğunuzda otomatik olarak yüklenen bir istemci uygulama yapılandırma dosyası nesne. Her iki WCF istemci türü, aynı zamanda program aracılığıyla bu bilgileri belirtmenize olanak sağlayan aşırı yüklemeleri vardır.  
  
 Örneğin, oluşturulan yapılandırma dosyası bir `ISampleService` önceki kullanılan örnekler aşağıdaki uç nokta bilgileri içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma dosyası bir hedef uç noktasını belirtir `<client>` öğesi. Birden çok hedef uç noktaları kullanma hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> oluşturucular.  
  
## <a name="calling-operations"></a>İşlem çağırma  
 Bir kez, oluşturulan istemci nesnesi olması ve yapılandırılmış, bir try/catch bloğu oluşturma, yerel bir nesneymiş yaptığınız aynı şekilde işlemleri çağırmak ve WCF istemci nesnesi kapatın. İstemci uygulaması ilk işlem çağırdığında, WCF arka plandaki kanal otomatik olarak açılır ve arka plandaki kanal nesnesi geri dönüştürüldüğünde kapalı. (Alternatif olarak, aynı zamanda açıkça açabilir ve kanal öncesinde veya diğer işlemler çağırma den kapatın.)  
  
 Örneğin, aşağıdaki hizmet sözleşmesi varsa:  
  
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
  
 WCF istemci nesnesi oluşturarak işlemler çağırabilir ve aşağıdaki kod örneği kendi yöntemlerini çağırmak gösterir. Açma, arama ve kapanış WCF istemci nesnesinin bir try/catch bloğu içinde oluştuğunu unutmayın. Daha fazla bilgi için [WCF istemci kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) ve [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları işleme  
 Özel durumlar, bir istemci uygulamasında gerçekleşebilir, temel alınan istemcinin açma kanal olduğunda (açıkça veya otomatik olarak bir işlem çağırarak), işlemleri çağırmak için istemci veya kanal nesnesini kullanarak ya da temel alınan istemci Kanal kapatılırken. En azından uygulamaları olası işlemek beklemeniz önerilir <xref:System.TimeoutException?displayProperty=nameWithType> ve <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> herhangi ek olarak özel durumlar <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> işlemleri tarafından dönen SOAP hatalarının sonucu olarak oluşturulan nesneleri. İstemci uygulamalar için işlem sözleşmede belirtilen SOAP hataları oluştuğunda bir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi, bir SOAP hatası ayrıntı türü olduğu. Bir istemci uygulamasında hata koşullarını işleme hakkında daha fazla bilgi için bkz. [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md). Bir istemci hataları işlemek nasıl gösterir eksiksiz bir örnek için bkz: [beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Yapılandırma ve istemcileri güvenli hale getirme  
 Bu bilgileri kullanarak program aracılığıyla istemci oluşturucular ve Özellikler'i de yükleyebilirsiniz ancak bir istemci yapılandırma gerekli yükleme istemci veya kanal nesneden, genellikle bir yapılandırma dosyası için hedef uç noktası bilgileri ile başlar. Ancak, bazı istemci davranışı etkinleştirmek için ek yapılandırma adımları gerekir ve birçok güvenlik senaryoları.  
  
 Örneğin, hizmet sözleşmelerini güvenlik gereksinimlerini hizmet sözleşmesi arabiriminde bildirilir ve Svcutil.exe bir yapılandırma dosyası oluşturduysanız, bu dosya genellikle hizmet güvenlik gereksinimlerini destekleyen bir bağlama içerir. Bazı durumlarda, ancak daha fazla güvenlik yapılandırması, istemci kimlik bilgileri yapılandırma gibi gerekli olabilir. WCF istemcileri için güvenlik yapılandırması hakkında tam bilgi için bkz. [istemcileri güvenli hale getirme](../../../docs/framework/wcf/securing-clients.md).  
  
 Ayrıca, bazı özel değişiklikler özel çalışma zamanı davranışları gibi istemci uygulamaları etkinleştirilebilir. Özel istemci davranışını yapılandırma hakkında daha fazla bilgi için bkz. [istemci davranışlarını yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma nesneleri oluşturma  
 İstemci uygulaması sözleşme gereksinimlerine göre çağırmak hizmeti için bir geri çağırma nesnesi sağlamak için uygulanması gereken bir geri çağırma anlaşması çift yönlü hizmetler belirtin. Geri çağırma nesnelerinin tam Hizmetleri olmamasına rağmen (örneğin, bir geri çağırma nesnesi ile bir kanalı başlatamazsınız), amacı doğrultusunda, uygulama ve bunlar düşünülebilir hizmeti bir tür olarak yapılandırma.  
  
 Çift yönlü hizmetler istemcileri gerekir:  
  
-   Bir geri çağırma anlaşması sınıf uygulayın.  
  
-   Geri çağırma anlaşması uygulama sınıfının bir örneğini oluşturun ve oluşturmak için bunu kullanın <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> WCF istemci oluşturucuya geçirdiğiniz bir nesne.  
  
-   İşlem çağırma ve işlem geri çağırmaları işlemek.  
  
 Çift yönlü WCF istemci nesneleri işlevi, bunlar geri çağırmalar, geri arama hizmetinin yapılandırılması dahil olmak üzere desteklemek için gereken işlevselliği göstermek üzere bu durumun nonduplex karşılıkları ister.  
  
 Örneğin, özelliklerini kullanarak çeşitli yönlerini geri çağırma nesnesi çalışma zamanı davranışını kontrol edebilirsiniz <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> geri çağırma sınıfı özniteliği. Başka bir örnek kullanımıdır <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> geri çağırma nesnesi arama hizmetleri özel durum bilgilerini dön etkinleştirmek için sınıf. Daha fazla bilgi için [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md). Eksiksiz bir örnek için bkz. [çift yönlü](../../../docs/framework/wcf/samples/duplex.md).  
  
 Internet Information Services (IIS) 5.1 çalıştıran Windows XP bilgisayarlarda, çift yönlü istemciler istemci kullanarak temel adresi belirtmeniz <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sınıfı ya da özel durum harekete geçirilir. Aşağıdaki kod örneği, kod içinde bunun nasıl yapılacağını gösterir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod bir yapılandırma dosyasında bunun nasıl yapılacağını gösterir.  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri zaman uyumsuz olarak çağırma  
 İşlemler nasıl verilir, tamamen istemci geliştiricisi kadar kadar. Yönetilen kodda belirtildiğinde zaman uyumlu veya zaman uyumsuz yöntemler için bir işlemi yapmak iletileri eşlenebilir olmasıdır. Bu nedenle, zaman uyumsuz olarak işlemlerini çağıran bir istemci oluşturmak istiyorsanız, zaman uyumsuz istemci kullanılarak kod üretmek için Svcutil.exe kullanabilirsiniz `/async` seçeneği. Daha fazla bilgi için [nasıl yapılır: Hizmet işlemlerini zaman uyumsuz çağırma](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF istemci kanalları kullanarak arama hizmetleri  
 WCF istemci türleri genişleten <xref:System.ServiceModel.ClientBase%601>, kendisi türetilir <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> arka plandaki kanal sistem kullanıma sunmak için arabirim. Hedef hizmet söyleşmesi kullanarak Hizmetleri çağırabilirsiniz <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıfı. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
