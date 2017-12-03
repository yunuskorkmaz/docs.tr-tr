---
title: "WCF İstemcisi Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6333db92d010eab7765cfc62a9f64601d5b82d55
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-client-overview"></a>WCF İstemcisi Genel Bakış
Bu bölümde hangi istemci uygulamaları yapın, yapılandırma, oluşturma ve kullanma açıklanmaktadır bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] istemci ve istemci uygulamalarının güvenliğini sağlama.  
  
## <a name="using-wcf-client-objects"></a>WCF istemci nesnelerini kullanma  
 Bir istemci uygulaması kullanan bir yönetilen uygulamayı olan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] başka bir uygulamayla iletişim kurmak için istemci. İçin bir istemci uygulaması oluşturmak için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti aşağıdakileri gerektirir:  
  
1.  Hizmet sözleşmesi, bağlamaları ve hizmet uç noktası için adres bilgilerini edinin.  
  
2.  Oluşturma bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bu bilgileri kullanarak istemci.  
  
3.  Operations çağırın.  
  
4.  Kapat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi.  
  
 Aşağıdaki bölümlerde bu adımları ele almaktadır ve kısa tanıtımlar aşağıdaki sorunlar için sağlayın:  
  
-   Hataları işleme.  
  
-   Yapılandırma ve istemcileri güvenli hale getirme.  
  
-   Çift yönlü hizmetler için geri çağırma nesneleri oluşturma.  
  
-   Hizmetleri zaman uyumsuz olarak çağırma.  
  
-   İstemci kanalları kullanarak Hizmetleri çağrılıyor.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Hizmet sözleşmesi, bağlamaları ve adresleri alın  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], yönetilen öznitelikler, arabirimleri ve yöntemleri kullanarak hizmetler ve istemcileri modeli sözleşmeler. Bir istemci uygulamasında hizmetine bağlanmak için hizmet sözleşmesi için türü bilgileri edinmeniz gerekir. Genellikle, kullanarak bunu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), hangi hizmetinden meta verileri indirir, tercih ettiğiniz dilde yönetilen kaynak kodu dosyasına dönüştürür ve bir istemci oluşturur yapılandırmak için kullanabileceğiniz uygulama yapılandırma dosyası, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi. Örneğin, oluşturma bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çağırmak için istemci nesne bir `MyCalculatorService`, ve bu hizmet için meta veriler yayımlanma bildiğiniz `http://computerName/MyCalculatorService/Service.svc?wsdl`, aşağıdaki kod örneğinde elde etmek için Svcutil.exe kullanma gösterilmektedir sonra bir `ClientCode.vb` Yönetilen kodda sözleşme hizmet içeren dosya.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 İstemci uygulaması veya istemci uygulaması oluşturmak için kullanabileceğiniz başka bir derlemeyi ya da bu sözleşme kodu derleyebilirsiniz bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi. Yapılandırma dosyası doğru hizmete bağlanmak için istemci nesne yapılandırmak için kullanabilirsiniz.  
  
 Bu işlem bir örnek için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Sözleşmeleri hakkında daha ayrıntılı bilgi için bkz: [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Bir WCF istemcisi nesnesi oluşturun  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnedir temsil eden bir yerel bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet istemci uzak hizmetiyle iletişim kurmak için kullanabileceğiniz bir biçimde. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]İstemci türleri uygulayan hedef hizmet sözleşme oluşturun ve yapılandırın, ardından istemci nesnesi hizmet işlemleri doğrudan çağırmak için kullanabilmek için. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Yöntemi çağırır iletilere, hizmete gönderir, yanıtı dinler ve bu değerleri döndürür zaman dönüştürür çalıştırmak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi dönüş değerleri olarak veya `out` veya `ref` parametreleri.  
  
 Aynı zamanda [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ile bağlanmak ve hizmetlerini kullanmak için istemci kanal nesneleri. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Yeni bir WCF nesnesi oluşturma  
 Kullanımını göstermek için bir <xref:System.ServiceModel.ClientBase%601> sınıfı, bir hizmet uygulamasından aşağıdaki basit hizmet sözleşmesi oluşturuldu varsayalım.  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] oluşturmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci, nesneleri yüklenir otomatik olarak nesne tarayıcısı, hizmet başvurusu projenize ekleyin.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Kullanmıyorsanız, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], genişletir türü bulmak için oluşturulan sözleşme kodunu İnceleme <xref:System.ServiceModel.ClientBase%601> ve hizmet sözleşme arabirimi `ISampleService`. Bu durumda, bu tür aşağıdaki kod gibi görünür:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Bu sınıf oluşturucular birini kullanarak yerel bir nesne olarak oluşturulan, yapılandırılmış ve türünde bir hizmete bağlanmak için kullanılan `ISampleService`.  
  
 Oluşturduğunuz önerilir, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci ilk olarak, nesne kullanmak ve tek try/catch bloğu içinde kapatın. Kullanılamaz `using` deyimi (`Using` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) belirli hata modları durumlar maskeleyebilir olduğundan. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]Aşağıdaki bölümlerde de olarak [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Sözleşmeler, bağlamaları ve adresleri  
 Oluşturabilmeniz için önce bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi, istemci nesnesi yapılandırmanız gerekir. Özellikle, bir hizmet olmalıdır *endpoint* kullanmak için. Bir uç nokta bir hizmet sözleşmesini, bağlama ve adresi birleşimidir. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] uç noktaları, bkz: [uç noktalar: adresler, bağlamalar ve sözleşmeler](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Genellikle, bu bilgileri bulunan [ \<uç noktası >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) gibi Svcutil.exe araç oluşturur ve istemci oluşturduğunuzda otomatik olarak yüklenen bir istemci uygulama yapılandırma dosyası öğesi nesne. Her ikisi de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci türlerini Ayrıca bu bilgileri programlı olarak belirtmenizi sağlayan aşırı vardır.  
  
 Örneğin, üretilen yapılandırma dosyası için bir `ISampleService` önceki kullanılan örnekler aşağıdaki uç nokta bilgileri içerir.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Bu yapılandırma dosyasını hedef uç nokta içinde belirtir `<client>` öğesi. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bkz. birden çok hedef uç noktaları kullanma <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> oluşturucular.  
  
## <a name="calling-operations"></a>Arama işlemleri  
 Oluşturulan istemci nesnesi yüklü ve yapılandırılmış, bir try/catch bloğu Oluştur sonra yerel ve Kapat nesne varsa, yaptığınız aynı şekilde işlemlerini çağırma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi. İstemci uygulaması ilk işlemi çağırdığında [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] otomatik olarak açılır arka plandaki kanal ve nesneyi geri dönüştürüldüğünde temel kanal kapatılır. (Alternatif olarak, aynı zamanda açıkça açabilir ve kanal öncesinde veya diğer işlemlerin çağırma sonra kapatın.)  
  
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
  
 Oluşturarak işlemler çağırabilir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi ve aşağıdaki kod örneğinde gösterdiği gibi kendi yöntemleri çağırma. Unutmayın açma, arama ve kapanmasını [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi tek try/catch bloğu içinde gerçekleşir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) ve [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Hataları işleme  
 Özel durumlar, bir istemci uygulamasında gerçekleşebilir, temel alınan istemci açma kanal, (açıkça olup olmadığını veya tarafından otomatik olarak bir işlem çağırma) işlemlerini çağırmak için istemci veya kanal nesnesi kullanılarak veya temel alınan istemci kanal kapatırken. En azından uygulamaları olası işlemek beklediğiniz önerilir <xref:System.TimeoutException?displayProperty=nameWithType> ve <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> herhangi bir ek olarak özel durumlar <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> SOAP hataları işlemleri tarafından döndürülen sonucu olarak oluşturulan nesneleri. İşlemi sözleşmede belirtilen SOAP hataları istemci uygulamalar için yükseltilmiş bir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> burada tür parametresi, bir SOAP hatası ayrıntı türü. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bir istemci uygulamasında hata koşullarını işleme, bkz: [gönderme ve alma hataları](../../../docs/framework/wcf/sending-and-receiving-faults.md). Bir istemci hataların nasıl işleneceğini gösterir tam bir örnek için bkz: [beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Yapılandırma ve istemcileri güvenli hale getirme  
 Program aracılığıyla istemci oluşturucular ve özellikleri kullanarak bu bilgileri de yükleyebilirsiniz rağmen hedef uç nokta bilgileri istemci veya kanal nesneden, genellikle bir yapılandırma dosyası için gerekli yükleme ile bir istemci yapılandırma başlatır. Ancak, belirli istemci davranışını etkinleştirmek için ek yapılandırma adımları gerekir ve birçok güvenlik senaryoları.  
  
 Örneğin, hizmet sözleşmeleri için güvenlik gereksinimlerinin hizmet sözleşmesi arabiriminde bildirilir ve Svcutil.exe bir yapılandırma dosyası oluşturduysanız, bu dosya genellikle hizmet güvenlik gereksinimlerini destekleme kapasitesine sahip bir bağlama içerir. Bazı durumlarda, ancak daha fazla güvenlik yapılandırması, istemci kimlik bilgileri yapılandırma gibi gerekli olabilir. Bir güvenlik yapılandırması hakkında tam bilgi için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemciler, bkz: [istemcileri güvenli hale getirme](../../../docs/framework/wcf/securing-clients.md).  
  
 Ayrıca, bazı özel değişiklikler özel çalışma zamanı davranışlar gibi istemci uygulamalarını etkinleştirilebilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Özel istemci davranışını yapılandırma hakkında [istemci davranışlarını yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Çift yönlü hizmetler için geri çağırma nesneleri oluşturma  
 Çift yönlü hizmetler, istemci uygulaması sözleşme gereksinimlerine göre aramak hizmeti için bir geri çağırma nesnesi sağlamak için uygulanması gereken bir geri çağırma sözleşme belirtin. Geri çağırma nesneleri tam Hizmetleri olmasa da (örneğin, bir geri çağırma nesnesi ile bir kanalı başlatamaz), uygulama ve bunlar zorlayıcı hizmet bir tür olarak yapılandırma amacı.  
  
 Çift yönlü hizmetler istemcileri gerekir:  
  
-   Bir geri çağırma sözleşme sınıfı uygulayın.  
  
-   Geri çağırma sözleşmesi uygulama sınıfının bir örneği oluşturun ve oluşturmak için kullanın <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> için geçirdiğiniz nesne [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci Oluşturucusu.  
  
-   İşlem çağırma ve işlem geri çağırmaları işlemek.  
  
 Çift yönlü [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnelerini geri çağırmalar, geri çağırma hizmetinin yapılandırmasını dahil olmak üzere desteklemek için gerekli işlevselliği kullanıma özel nonduplex dekiler gibi çalışır.  
  
 Örneğin, özelliklerini kullanarak geri çağırma nesnesi çalışma zamanı davranışı çeşitli yönlerini kontrol edebilir <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> geri çağırma Sınıf özniteliği. Başka bir örneği kullanımıdır <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> geri çağırma nesnesi arama hizmetleri özel durum bilgilerini dönün etkinleştirmek için sınıf. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md). Tam bir örnek için bkz: [çift yönlü](../../../docs/framework/wcf/samples/duplex.md).  
  
 Internet Information Services (IIS) 5.1 çalıştıran Windows XP bilgisayarlarda, çift yönlü istemciler kullanarak bir istemci taban adresi belirtmeniz <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> sınıfı ya da bir özel durum oluşur. Aşağıdaki kod örneğinde, kodda bunun gösterilmektedir.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Aşağıdaki kod bu yapılandırma dosyasında nasıl gösterir  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Hizmetleri zaman uyumsuz olarak çağırma  
 Nasıl operations tamamen istemci Geliştirici kadar çağrılmaz. Yönetilen kodda belirtildiğinde zaman uyumlu veya zaman uyumsuz yöntemleri işlemi yapmak iletileri eşlenebilir olmasıdır. İşlemlerini zaman uyumsuz olarak çağırır bir istemci oluşturmak istiyorsanız, bu nedenle, Svcutil.exe zaman uyumsuz istemci kodu kullanarak oluşturmak için kullanabileceğiniz `/async` seçeneği. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Nasıl yapılır: çağrı hizmet işlemlerini zaman uyumsuz olarak](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF istemci kanalı kullanılarak arama hizmetleri  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]istemci türlerini genişletme <xref:System.ServiceModel.ClientBase%601>, kendisi türer <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> temeldeki kanal sistemi kullanıma sunmak için arabirim. Hedef hizmet sözleşmesine kullanarak Hizmetleri çağırabileceği <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıfı. Ayrıntılar için bkz [WCF istemci mimarisi](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
