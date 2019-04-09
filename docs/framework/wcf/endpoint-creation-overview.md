---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 6aecad3719fff98a2e834cff6eee9cfe39a699aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106541"
---
# <a name="endpoint-creation-overview"></a>Uç Noktası Oluşturma Genel Bakış
Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde üzerinden gerçekleşir *uç noktaları* hizmeti. Uç noktaları, istemcilerin bir WCF hizmeti sunan işlevine erişim sağlar. Bu bölümde, bir uç nokta yapısını açıklar ve bir uç nokta yapılandırması ve kodda nasıl tanımlanacağını açıklar.  
  
## <a name="the-structure-of-an-endpoint"></a>Bir uç nokta yapısı  
 Her uç nokta uç noktası, istemci uç noktasıyla nasıl iletişim kurabilir belirten bir bağlama ve uygun olan yöntemler tanımlayan bir sözleşme nerede bulacağını gösteren bir adres içeriyor.  
  
-   **Adres**. Adres benzersiz şekilde uç noktayı tanımlar ve olası tüketiciler hizmet nerede olduğunu bildirir. WCF nesne modeli tarafından temsil edilir <xref:System.ServiceModel.EndpointAddress> Tekdüzen Kaynak Tanımlayıcısı (URI) ve bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı bir koleksiyonunu içeren adres özelliklerini içeren adresi üstbilgileri. İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için ek ayrıntılı adresleme bilgi sağlar. Daha fazla bilgi için [bir uç nokta adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Bağlama**. Bağlama uç noktasıyla iletişim nasıl belirtir. Bağlama nasıl uç nokta kullanmak için hangi Aktarım Protokolü dahil olmak üzere dünya ile (örneğin, TCP veya HTTP) hangi (örneğin, metin veya ikili) iletileri için kullanılacak kodlama iletişim kurar ve hangi güvenlik gereksinimleri (gereken belirtir. Örneğin, Güvenli Yuva Katmanı [SSL] veya SOAP ileti güvenliği). Daha fazla bilgi için [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Hizmet sözleşmesini**. Hizmet sözleşmesi istemciye uç noktasını kullanıma sunar işlevler açıklanmaktadır. Bir anlaşma, bir istemci çağırabilirsiniz işlemleri, ileti biçimi ve giriş parametreleri veya işlem ve işleme veya istemci bekleyebileceğiniz yanıt iletisi türü çağırmak için gereken veri türünü belirtir. Sözleşmeler üç temel türde karşılık gelen temel ileti exchange desenlerini (MEPs): veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü). Hizmet sözleşmesi, erişilen, belirli veri türleri ve ileti formatları gerektiren veri ve ileti sözleşmeleri de kullanabilirsiniz. Bir hizmet sözleşmesini tanımlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md). Bir istemci da çift yönlü MEP hizmette iletileri alacak şekilde geri çağırma anlaşması adlı bir hizmet tarafından tanımlanan sözleşme uygulamak için gerekli unutmayın. Daha fazla bilgi için [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Kesin kod kullanarak veya bildirimli olarak yapılandırma yoluyla bir hizmet için uç nokta belirtilebilir. Uç nokta belirtilmezse çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Genel olarak, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha yararlı olur. Bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek sağlar.  
  
> [!NOTE]
>  Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken ya da birini kullanmalısınız <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri veya <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> sözleşme düzgün bir şekilde yeni bir yükleme yöntemini <xref:System.ServiceModel.Description.ServiceDescription> nesne.  
  
## <a name="defining-endpoints-in-code"></a>Uç noktaları kodda tanımlama  
 Aşağıdaki örnek, aşağıdaki kodda bir uç nokta belirtmek verilmektedir:  
  
-   Sözleşme tanımlamasına bir `IEcho` birisinin adını ve yankı yanıtı ile kabul eden hizmet türü "Hello \<name >!".  
  
-   Uygulama bir `Echo` hizmet tarafından tanımlanan tür `IEcho` sözleşme.  
  
-   Bir uç nokta adresini belirtin `http://localhost:8000/Echo` hizmeti.  
  
-   Yapılandırma `Echo` kullanarak hizmet bir <xref:System.ServiceModel.WSHttpBinding> bağlama.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  Hizmet ana bilgisayarı, bir taban adresi ile oluşturulur ve ardından temel adresini göreli adres geri kalanı bir uç noktasının bir parçası belirtilir. Bu bölümleme adresini daha rahat bir ana bilgisayar Hizmetleri için tanımlanmış birden çok uç noktaları sağlar.  
  
> [!NOTE]
>  Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama için subsequent değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodunda <xref:System.ServiceModel.ServiceHostBase>. Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlerde <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, bu noktanın ilerisine değiştirdiyseniz bir özel durum. Diğerleri, bunları değiştirmek için izin verir, ancak sonuç tanımsızdır.  
>   
>  Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerlerin değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği bu noktanın ilerisine değiştirdiyseniz bir özel durum oluşturur. Diğer istemci açıklama değerler hatasız değiştirilebilir, ancak sonuç tanımsızdır.  
>   
>  Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Uç noktalar yapılandırmada tanımlama  
 Bir uygulama oluştururken, genellikle uygulama dağıtma Yöneticisi kararları erteleme istersiniz. Örneğin, yoktur genellikle önceden (URI) yönelik bir hizmet olduğunu bilmesinin imkanı olacaktır. Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak bir yönetici izin vermek için tercih edilir. Bu esnekliğin yapılandırma aracılığıyla gerçekleştirilir. Ayrıntılar için bkz [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config:` *filename*`[,`*filename* `]` geçin yapılandırma dosyaları hızlı bir şekilde oluşturun.  
  
## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma  
 Uç nokta kod veya yapılandırma belirtilirse çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.ICommunicationObject.Open> üzerinde çağrılır <xref:System.ServiceModel.ServiceHost>. Bu örnek, önceki bölümde aynı örneği olmakla birlikte varsayılan uç noktalarını, uç nokta belirlendiğinden eklenir.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 Uç noktalar açıkça verdiyse, varsayılan uç noktaları hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmelerini Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
