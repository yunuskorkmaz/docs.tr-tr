---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 46ca6294d68537e86a319b55d8c11e3ae0084738
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809176"
---
# <a name="endpoint-creation-overview"></a>Uç Noktası Oluşturma Genel Bakış
Tüm Windows Communication Foundation (WCF) hizmetiyle aracılığıyla iletişimin *uç noktaları* hizmetinin. Uç noktaları istemciler için bir WCF hizmeti sunan işlevlere erişimi sağlar. Bu bölümde bir uç nokta yapısını tanımlar ve bir uç nokta yapılandırması ve kodda nasıl tanımlanacağını açıklar.  
  
## <a name="the-structure-of-an-endpoint"></a>Bir uç nokta yapısı  
 Her uç nokta uç noktası, bir istemci uç noktasıyla nasıl iletişim kurabilir belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir sözleşme nerede bulacağını gösterir bir adres içeriyor.  
  
-   **Adres**. Adresi benzersiz olarak uç nokta tanımlar ve olası tüketicileri hizmet nerede olduğunu bildirir. WCF nesne modeli tarafından temsil edilen <xref:System.ServiceModel.EndpointAddress> Tekdüzen Kaynak Tanımlayıcısı (URI) ve bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı bir koleksiyonunu içeren adres özelliklerini içeren adresi üstbilgileri. İsteğe bağlı üstbilgi tanımlamak veya uç noktasıyla etkileşim için ek ayrıntılı adresleme bilgi sağlar. Daha fazla bilgi için bkz: [bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Bağlama**. Bağlama bitiş noktası ile iletişim kurmak nasıl belirtir. Bağlama nasıl uç nokta kullanmak için hangi Aktarım Protokolü dahil olmak üzere dünya ile (örneğin, TCP veya HTTP) hangi (örneğin, metin veya ikili) iletileri için kullanılacak kodlama iletişim kurar ve hangi güvenlik gereksinimlerini (için gerekli olduğunu belirler Örneğin, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenlik). Daha fazla bilgi için bkz: [kullanarak bağlamaları yapılandırma hizmetler ve istemcileri için](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Hizmet sözleşmesi**. Hizmet sözleşmesi istemciye uç noktasını kullanıma sunar hangi işlevsellikler özetlenmektedir. Bir sözleşme istemci çağırabilirsiniz işlemleri, ileti biçimi ve giriş parametreleri veya işlem ve işleme veya istemci bekleyebilirsiniz yanıt iletisi türünü aramak için gerekli veri türünü belirtir. Sözleşmeleri üç temel türde karşılık gelen temel ileti exchange desenlerini (MEPs): (tek yönlü), veri birimi istek/yanıt ve çift yönlü (çift yönlü). Hizmet sözleşmesi belirli veri türlerini ve ileti formatları erişilen zaman gerektirecek şekilde veri ve ileti sözleşmeleri da tercih edebilirsiniz. Bir hizmet sözleşmesini tanımlama hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md). Bir istemci da çift yönlü MEP hizmetinde iletileri almak için bir geri çağırma sözleşme adlı bir hizmet tarafından tanımlanan sözleşme uygulamak için gerekli unutmayın. Daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Bir hizmeti için uç noktaya kodu kullanarak imperatively ya da bildirimli olarak yapılandırma yoluyla belirtilebilir. Uç nokta yok belirtilmezse, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Genellikle, kod yerine Yapılandırması kullanılarak hizmet uç noktaları tanımlamak daha pratik olur. Bağlama tutulması ve kod dışında bilgisine derlenir ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.  
  
> [!NOTE]
>  Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken ya da birini kullanmanız gerekir <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri veya <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> düzgün sözleşmeyi yeni bir yükleme yöntemini <xref:System.ServiceModel.Description.ServiceDescription> nesnesi.  
  
## <a name="defining-endpoints-in-code"></a>Uç noktaları kodda tanımlama  
 Aşağıdaki örnek, bir uç nokta aşağıdaki kodla belirtmek üzere verilmektedir:  
  
-   Tanımlamak için bir sözleşmede bir `IEcho` birisinin adını ve yankı yanıtı ile kabul hizmet türü "Merhaba \<adı >!".  
  
-   Uygulama bir `Echo` tarafından tanımlanan türdeki hizmet `IEcho` sözleşme.  
  
-   Bir uç nokta adresini belirtin http://localhost:8000/Echo hizmeti.  
  
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
>  Hizmet ana bilgisayarı ile temel bir adres oluşturulur ve temel adres göre adresi geri kalanı bir uç nokta bir parçası olarak sonra belirtilir. Bu adresini bölümleme daha rahat bir ana adresinde Hizmetleri tanımlanması birden çok uç nokta sağlar.  
  
> [!NOTE]
>  Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama subsequent için değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemi <xref:System.ServiceModel.ServiceHostBase>. Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlere <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, o noktayı değiştirilirse bir özel durum. Başkalarının, bunları değiştirmek için izin verme, ancak sonuç tanımlanmadı.  
>   
>  Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği bu noktayı değiştirilirse bir özel durum oluşturur. Bir istemci açıklama değerleri hatasız değiştirilebilir, ancak sonuç tanımlanmadı.  
>   
>  Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olup olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Uç nokta yapılandırmasında tanımlama  
 Bir uygulama oluştururken, genellikle uygulama dağıtma Yöneticisi kararları erteleneceği istersiniz. Örneğin, olduğundan genellikle önceden (URI) adresi bir hizmet bilerek hiçbir şekilde olacaktır. Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak için yönetici izin vermek için tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir. Ayrıntılar için bkz [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config:` *filename*`[,`*filename* `]` geç yapılandırma dosyaları hızla oluşturun.  
  
## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma  
 Uç nokta yok kod veya yapılandırma belirtilmezse, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.ICommunicationObject.Open> üzerinde adlı <xref:System.ServiceModel.ServiceHost>. Bu örnek, önceki bölümde aynı örnekten olmakla birlikte uç nokta yok belirtilen olduğundan, varsayılan uç noktalar eklenir.  
  
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
  
 Uç noktalar açıkça verdiyse, varsayılan uç noktalar hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
