---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319922"
---
# <a name="endpoint-creation-overview"></a>Uç Noktası Oluşturma Genel Bakış

Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur. Uç noktalar, istemcilerin bir WCF hizmetinin sunduğu işlevlere erişmesini sağlar. Bu bölüm bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını özetler.

## <a name="the-structure-of-an-endpoint"></a>Bir uç noktanın yapısı

Her uç nokta, uç noktanın nerede bulunacağını belirten bir adres içerir, bir istemcinin uç noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir anlaşma.

- **Adres**. Adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu potansiyel tüketicilere bildirir. Bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı üstbilgiler koleksiyonu içeren bir Tekdüzen Kaynak tanımlayıcısı (URI) ve adres özellikleri içeren <xref:System.ServiceModel.EndpointAddress> adresi tarafından WCF nesne modelinde temsil edilir. İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya bunlarla etkileşime geçmek için ek ayrıntılı adresleme bilgileri sağlar. Daha fazla bilgi için bkz. [uç nokta adresi belirtme](specifying-an-endpoint-address.md).

- **Bağlama**. Bağlama, uç noktayla nasıl iletişim kuracağını belirtir. Bağlama, (örneğin, metin veya ikili) ve hangi güvenlik gereksinimlerinin gerekli olduğu ile (örneğin, metin veya ikili) hangi Aktarım protokolünün kullanılacağını (örneğin, TCP veya HTTP) dahil olmak üzere, uç noktanın dünya ile nasıl iletişim kuracağını belirtir ( örnek, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenliği). Daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md).

- **Hizmet sözleşmesi**. Hizmet sözleşmesi, uç noktanın istemciye sunduğu işlevselliği özetler. Bir anlaşma, bir istemcinin çağırabilecekleri işlemleri, ileti formunu ve giriş parametrelerinin türünü ya da işlemi çağırmak için gereken verileri, istemcinin beklediği işlem veya yanıt iletisi türünü belirtir. Üç temel sözleşme türü, temel ileti değişimi desenlerine (MEPs) karşılık gelir: veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü). Hizmet sözleşmesi, erişim sırasında belirli veri türleri ve ileti biçimleri istemek için veri ve ileti sözleşmeleri de kullanabilir. Hizmet sözleşmesinin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md). Bir istemcinin, bir çift yönlü MEP 'de hizmetten ileti almak için, geri arama sözleşmesi olarak adlandırılan hizmet tanımlı bir sözleşmeyi uygulamak için de gerekli olabileceğini unutmayın. Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).

Bir hizmetin uç noktası, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir. Hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır. Bağlama ve adresleme bilgilerinin koddan tutulması, uygulamayı yeniden derlemek ve yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.

> [!NOTE]
> Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken, sözleşmeyi yeni bir <xref:System.ServiceModel.Description.ServiceDescription> nesnesine doğru bir şekilde yüklemek için <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemlerinden birini ya da <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> yöntemini kullanmanız gerekir.

## <a name="defining-endpoints-in-code"></a>Koddaki uç noktaları tanımlama

Aşağıdaki örnek, kodda aşağıdaki gibi bir uç noktanın nasıl belirtildiğini göstermektedir:

- "Hello \<name >!" yanıtıyla birlikte birisinin adını ve yankısını kabul eden `IEcho` hizmet türü için bir sözleşme tanımlayın.

- @No__t-1 sözleşmesi tarafından tanımlanan türde `Echo` hizmeti uygulayın.

- Hizmet için `http://localhost:8000/Echo` ' nın bir uç nokta adresini belirtin.

- @No__t-0 hizmetini <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanarak yapılandırın.

```csharp
namespace Echo
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
> Hizmet ana bilgisayarı bir temel adresle oluşturulur ve ardından temel adrese göre adresin geri kalanı bir uç noktanın parçası olarak belirtilir. Adresin bu bölümlenmesi, birden çok uç noktanın bir konaktaki hizmetler için daha kolay tanımlanmasına olanak tanır.

> [!NOTE]
> Hizmet uygulamasındaki <xref:System.ServiceModel.Description.ServiceDescription> ' ın özellikleri, daha sonra <xref:System.ServiceModel.ServiceHostBase> ' deki <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemine değiştirilmemelidir. @No__t-0 özelliği ve <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost> üzerindeki `AddServiceEndpoint` yöntemleri gibi bazı üyeler o noktadan sonra değiştirilirse bir özel durum oluşturur. Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.
>
> Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri <xref:System.ServiceModel.ChannelFactory> ' de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> ' e çağrıdan sonra değiştirilmemelidir. @No__t-0 özelliği o noktadan sonra değiştirilirse bir özel durum oluşturur. Diğer istemci açıklama değerleri hata olmadan değiştirilebilir, ancak sonuç tanımsızdır.
>
> Hizmet veya istemci için, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce açıklamayı değiştirmeniz önerilir.

## <a name="defining-endpoints-in-configuration"></a>Yapılandırmada uç noktaları tanımlama

Bir uygulama oluştururken, kararları genellikle uygulamayı dağıtan yöneticiye erteleyebilirsiniz. Örneğin, genellikle bir hizmet adresinin (URI) ne olduğunu bilmenin bir yolu yoktur. Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir. Ayrıntılar için bkz. [Hizmetleri yapılandırma](configuring-services.md).

> [!NOTE]
> Yapılandırma dosyalarını hızlıca oluşturmak için `/config:`*dosya adı*`[,`*Dosya*adı `]` anahtarıyla [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.

## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma

Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Temel adres kodda veya yapılandırmada belirtilebilir ve varsayılan uç noktalar <xref:System.ServiceModel.ICommunicationObject.Open> <xref:System.ServiceModel.ServiceHost> ' de çağrıldığında eklenir. Bu örnek, önceki bölümden aynı örnektir, ancak hiçbir uç nokta belirtilmediğinden varsayılan uç noktalar eklenir.

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
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

 Uç noktalar açıkça sağlanmışsa, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce <xref:System.ServiceModel.ServiceHost> ' de <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> çağırarak varsayılan uç noktalar eklenebilir. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Anlaşmalarını Uygulama](implementing-service-contracts.md)
