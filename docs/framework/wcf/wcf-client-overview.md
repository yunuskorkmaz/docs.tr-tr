---
title: WCF İstemcisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 03a9580bee6308ef53c7d2bc6e9dbe619c2048f7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-client-overview"></a>WCF İstemcisi Genel Bakış
Bu bölümde, istemci uygulamalarının ne, yapılandırma, oluşturma ve bir Windows Communication Foundation (WCF) istemci kullanın ve istemci uygulamalarının güvenliğini sağlama açıklanmaktadır.  
  
## <a name="using-wcf-client-objects"></a>WCF istemci nesnelerini kullanma  
 Bir WCF istemcisi başka bir uygulama ile iletişim kurmak için kullandığı bir yönetilen uygulamayı bir istemci uygulamasıdır. Bir istemci oluşturmak için aşağıdaki adımları uygulama için bir WCF Hizmeti gerektirir:  
  
1.  Hizmet sözleşmesi, bağlamaları ve hizmet uç noktası için adres bilgilerini edinin.  
  
2.  Bu bilgileri kullanarak bir WCF istemcisi oluşturma.  
  
3.  Operations çağırın.  
  
4.  WCF istemci nesnesini kapatın.  
  
 Aşağıdaki bölümlerde bu adımları ele almaktadır ve kısa tanıtımlar aşağıdaki sorunlar için sağlayın:  
  
-   Hataları işleme.  
  
-   Yapılandırma ve istemcileri güvenli hale getirme.  
  
-   Çift yönlü hizmetler için geri çağırma nesneleri oluşturma.  
  
-   Hizmetleri zaman uyumsuz olarak çağırma.  
  
-   İstemci kanalları kullanarak Hizmetleri çağrılıyor.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Hizmet sözleşmesi, bağlamaları ve adresleri alın  
 WCF'de, hizmetler ve istemcileri yönetilen öznitelikler, arabirimleri ve yöntemleri kullanarak sözleşmeler model. Bir istemci uygulamasında hizmetine bağlanmak için hizmet sözleşmesi için türü bilgileri edinmeniz gerekir. Genellikle, kullanarak bunu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), hangi hizmetinden meta verileri indirir, tercih ettiğiniz dilde yönetilen kaynak kodu dosyasına dönüştürür ve bir istemci oluşturur WCF istemci nesnesi yapılandırmak için kullanabileceğiniz uygulama yapılandırma dosyası. Örneğin, çağırmak için WCF istemci nesne oluşturmak bir `MyCalculatorService`, ve bu hizmet için meta veriler yayımlanma bildiğiniz `http://computerName/MyCalculatorService/Service.svc?wsdl`, aşağıdaki kod örneğinde elde etmek için Svcutil.exe kullanma gösterilmektedir sonra bir `ClientCode.vb` dosya Yönetilen kodda hizmet sözleşmesini içerir.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 İstemci uygulaması veya istemci uygulaması bir WCF istemcisi nesnesi oluşturmak için kullanabileceğiniz başka bir derlemeyi ya da bu sözleşme kodu derleyebilirsiniz. Yapılandırma dosyası doğru hizmete bağlanmak için istemci nesne yapılandırmak için kullanabilirsiniz.  
  
 Bu işlem bir örnek için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Sözleşmeleri hakkında daha ayrıntılı bilgi için bkz: [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Bir WCF istemcisi nesnesi oluşturun  
 Bir WCF istemcisi istemci uzak hizmetiyle iletişim kurmak için kullanabileceğiniz bir formda bir WCF hizmeti temsil eden yerel bir nesnedir. WCF istemci türleri uygulayan hedef hizmet sözleşme oluşturun ve yapılandırın, ardından istemci nesnesi hizmet işlemleri doğrudan çağırmak için kullanabilmek için. Çalışma zamanı WCF yöntem çağrılarını iletilere dönüştürür, hizmetine gönderir, yanıtı dinler ve bu değerleri dönüş değerleri için WCF istemci nesnesi döndürür ya da `out` veya `ref` parametreleri.  
  
 WCF istemci kanal nesneleri, bağlanın ve hizmetlerini kullanmak için de kullanabilirsiniz. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni bir WCF nesnesi oluşturma  
 Kullanımını göstermek için bir <xref:System.ServiceModel.ClientBase%601> sınıfı, bir hizmet uygulamasından aşağıdaki basit hizmet sözleşmesi oluşturuldu varsayalım.  
  
> [!NOTE]
>  WCF istemcisi oluşturmak için Visual Studio kullanıyorsanız, projeniz için bir hizmet Başvurusu Ekle nesneleri otomatik olarak nesne tarayıcısı yüklenir.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio kullanmıyorsanız genişletir türü bulmak için oluşturulan sözleşme kodu incelemek <xref:System.ServiceModel.ClientBase%601> ve hizmet sözleşme arabirimi `ISampleService`. Bu durumda, bu tür aşağıdaki kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf oluşturucular birini kullanarak yerel bir nesne olarak oluşturulan, yapılandırılmış ve türünde bir hizmete bağlanmak için kullanılan `ISampleService`.  
  
 İlk olarak, WCF istemci nesnesi oluşturun ve daha sonra kullanmak ve tek try/catch bloğu içinde kapatın, önerilir. Kullanılamaz `using` deyimi (`Using` Visual Basic'te) belirli hata modları durumlar maskeleyebilir olduğundan. Daha fazla bilgi için aşağıdaki bölümlere bakın yanı [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, bağlamaları ve adresleri  
 WCF istemci nesnesi oluşturmadan önce istemci nesnesi yapılandırmanız gerekir. Özellikle, bir hizmet olmalıdır *endpoint* kullanmak için. Bir uç nokta bir hizmet sözleşmesini, bağlama ve adresi birleşimidir. (Uç noktaları hakkında daha fazla bilgi için bkz: [uç noktalar: adresler, bağlamalar ve sözleşmeler](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgileri bulunan [ \<uç noktası >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) gibi Svcutil.exe araç oluşturur ve istemci oluşturduğunuzda otomatik olarak yüklenen bir istemci uygulama yapılandırma dosyası öğesi nesne. Her iki WCF istemci türü Ayrıca bu bilgileri programlı olarak belirtmenizi sağlayan aşırı vardır.  
  
 Örneğin, üretilen yapılandırma dosyası için bir `ISampleService` önceki kullanılan örnekler aşağıdaki uç nokta bilgileri içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma dosyasını hedef uç nokta içinde belirtir `<client>` öğesi. Birden çok hedef uç noktaları kullanma hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> oluşturucular.  
  
## <a name="calling-operations"></a>Arama işlemleri  
 Sonra oluşturulan istemci nesnesi yüklü ve yapılandırılmış, bir try/catch bloğu Oluştur nesne yerel olsaydı, yaptığınız aynı şekilde işlemlerini çağırma ve WCF istemci nesnesi kapatın. İstemci uygulaması ilk işlemi aradığında, WCF otomatik olarak temel kanal açar ve nesneyi geri dönüştürüldüğünde temel kanal kapatılır. (Alternatif olarak, aynı zamanda açıkça açabilir ve kanal öncesinde veya diğer işlemlerin çağırma sonra kapatın.)  
  
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
  
 WCF istemci nesnesi oluşturarak işlemler çağırabilir ve aşağıdaki kod örneği kendi yöntemleri çağırma gösterir. Not: açılış, arama ve WCF istemci nesnesi kapanmasını tek try/catch bloğu içinde oluşur. Daha fazla bilgi için bkz: [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) ve [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları işleme  
 Özel durumlar, bir istemci uygulamasında gerçekleşebilir, temel alınan istemci açma kanal, (açıkça olup olmadığını veya tarafından otomatik olarak bir işlem çağırma) işlemlerini çağırmak için istemci veya kanal nesnesi kullanılarak veya temel alınan istemci kanal kapatırken. En azından uygulamaları olası işlemek beklediğiniz önerilir <xref:System.TimeoutException?displayProperty=nameWithType> ve <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> herhangi bir ek olarak özel durumlar <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> SOAP hataları işlemleri tarafından döndürülen sonucu olarak oluşturulan nesneleri. İşlemi sözleşmede belirtilen SOAP hataları istemci uygulamalar için yükseltilmiş bir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> burada tür parametresi, bir SOAP hatası ayrıntı türü. Bir istemci uygulamasında hata koşullarını işleme hakkında daha fazla bilgi için bkz: [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md). Bir istemci hataların nasıl işleneceğini gösterir tam bir örnek için bkz: [beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Yapılandırma ve istemcileri güvenli hale getirme  
 Program aracılığıyla istemci oluşturucular ve özellikleri kullanarak bu bilgileri de yükleyebilirsiniz rağmen hedef uç nokta bilgileri istemci veya kanal nesneden, genellikle bir yapılandırma dosyası için gerekli yükleme ile bir istemci yapılandırma başlatır. Ancak, belirli istemci davranışını etkinleştirmek için ek yapılandırma adımları gerekir ve birçok güvenlik senaryoları.  
  
 Örneğin, hizmet sözleşmeleri için güvenlik gereksinimlerinin hizmet sözleşmesi arabiriminde bildirilir ve Svcutil.exe bir yapılandırma dosyası oluşturduysanız, bu dosya genellikle hizmet güvenlik gereksinimlerini destekleme kapasitesine sahip bir bağlama içerir. Bazı durumlarda, ancak daha fazla güvenlik yapılandırması, istemci kimlik bilgileri yapılandırma gibi gerekli olabilir. WCF istemcileri için güvenlik yapılandırması hakkında tam bilgi için bkz: [istemcileri güvenli hale getirme](../../../docs/framework/wcf/securing-clients.md).  
  
 Ayrıca, bazı özel değişiklikler özel çalışma zamanı davranışlar gibi istemci uygulamalarını etkinleştirilebilir. Özel istemci davranışını yapılandırma hakkında daha fazla bilgi için bkz: [istemci davranışlarını yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma nesneleri oluşturma  
 Çift yönlü hizmetler, istemci uygulaması sözleşme gereksinimlerine göre aramak hizmeti için bir geri çağırma nesnesi sağlamak için uygulanması gereken bir geri çağırma sözleşme belirtin. Geri çağırma nesneleri tam Hizmetleri olmasa da (örneğin, bir geri çağırma nesnesi ile bir kanalı başlatamaz), uygulama ve bunlar zorlayıcı hizmet bir tür olarak yapılandırma amacı.  
  
 Çift yönlü hizmetler istemcileri gerekir:  
  
-   Bir geri çağırma sözleşme sınıfı uygulayın.  
  
-   Geri çağırma sözleşmesi uygulama sınıfının bir örneği oluşturun ve oluşturmak için kullanın <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> WCF istemci oluşturucuya geçirdiğiniz nesne.  
  
-   İşlem çağırma ve işlem geri çağırmaları işlemek.  
  
 Çift yönlü WCF istemci nesneleri işlevinin geri çağırma hizmetinin yapılandırmasını dahil olmak üzere geri çağırmalar desteklemek için gerekli işlevselliği kullanıma durumla nonduplex dekiler gibi.  
  
 Örneğin, özelliklerini kullanarak geri çağırma nesnesi çalışma zamanı davranışı çeşitli yönlerini kontrol edebilir <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> geri çağırma Sınıf özniteliği. Başka bir örneği kullanımıdır <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> geri çağırma nesnesi arama hizmetleri özel durum bilgilerini dönün etkinleştirmek için sınıf. Daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md). Tam bir örnek için bkz: [çift yönlü](../../../docs/framework/wcf/samples/duplex.md).  
  
 Internet Information Services (IIS) 5.1 çalıştıran Windows XP bilgisayarlarda, çift yönlü istemciler kullanarak bir istemci taban adresi belirtmeniz <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sınıfı ya da bir özel durum oluşur. Aşağıdaki kod örneğinde, kodda bunun gösterilmektedir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod bu yapılandırma dosyasında nasıl gösterir  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri zaman uyumsuz olarak çağırma  
 Nasıl operations tamamen istemci Geliştirici kadar çağrılmaz. Yönetilen kodda belirtildiğinde zaman uyumlu veya zaman uyumsuz yöntemleri işlemi yapmak iletileri eşlenebilir olmasıdır. İşlemlerini zaman uyumsuz olarak çağırır bir istemci oluşturmak istiyorsanız, bu nedenle, Svcutil.exe zaman uyumsuz istemci kodu kullanarak oluşturmak için kullanabileceğiniz `/async` seçeneği. Daha fazla bilgi için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF istemci kanalı kullanılarak arama hizmetleri  
 WCF istemci türlerini genişletme <xref:System.ServiceModel.ClientBase%601>, kendisi türer <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> temeldeki kanal sistemi kullanıma sunmak için arabirim. Hedef hizmet sözleşmesine kullanarak Hizmetleri çağırabileceği <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıfı. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
