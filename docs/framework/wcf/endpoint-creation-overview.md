---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 0b0c22737e9407ebe2cb56c15fb7ff75d16b50a4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040302"
---
# <a name="endpoint-creation-overview"></a>Uç Noktası Oluşturma Genel Bakış

Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur. Uç noktalar, istemcilerin bir WCF hizmetinin sunduğu işlevlere erişmesini sağlar. Bu bölüm bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını özetler.

## <a name="the-structure-of-an-endpoint"></a>Bir uç noktanın yapısı

Her uç nokta, uç noktanın nerede bulunacağını belirten bir adres içerir, bir istemcinin uç noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir anlaşma.

- **Adres**. Adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu potansiyel tüketicilere bildirir. Bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL <xref:System.ServiceModel.EndpointAddress> ) öğeleri ve isteğe bağlı bir koleksiyon içeren bir Tekdüzen Kaynak tanımlayıcısı (URI) ve adres özellikleri içeren adres tarafından WCF nesne modelinde temsil edilir bilgisinde. İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya bunlarla etkileşime geçmek için ek ayrıntılı adresleme bilgileri sağlar. Daha fazla bilgi için bkz. [uç nokta adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).

- **Bağlama**. Bağlama, uç noktayla nasıl iletişim kuracağını belirtir. Bağlama, (örneğin, metin veya ikili) ve hangi güvenlik gereksinimlerinin gerekli olduğu ile (örneğin, metin veya ikili) hangi Aktarım protokolünün kullanılacağını (örneğin, TCP veya HTTP) dahil olmak üzere, uç noktanın dünya ile nasıl iletişim kuracağını belirtir ( örnek, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenliği). Daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).

- **Hizmet sözleşmesi**. Hizmet sözleşmesi, uç noktanın istemciye sunduğu işlevselliği özetler. Bir anlaşma, bir istemcinin çağırabilecekleri işlemleri, ileti formunu ve giriş parametrelerinin türünü ya da işlemi çağırmak için gereken verileri, istemcinin beklediği işlem veya yanıt iletisi türünü belirtir. Üç temel sözleşme türü, temel ileti değişimi desenlerine (MEPs) karşılık gelir: veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü). Hizmet sözleşmesi, erişim sırasında belirli veri türleri ve ileti biçimleri istemek için veri ve ileti sözleşmeleri de kullanabilir. Hizmet sözleşmesinin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md). Bir istemcinin, bir çift yönlü MEP 'de hizmetten ileti almak için, geri arama sözleşmesi olarak adlandırılan hizmet tanımlı bir sözleşmeyi uygulamak için de gerekli olabileceğini unutmayın. Daha fazla bilgi için bkz. [çift yönlü hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).

Bir hizmetin uç noktası, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir. Hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır. Bağlama ve adresleme bilgilerinin koddan tutulması, uygulamayı yeniden derlemek ve yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.

> [!NOTE]
> Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken, iki <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemden birini <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> veya bir yöntemi kullanarak sözleşmeyi doğru bir şekilde yeni <xref:System.ServiceModel.Description.ServiceDescription> bir nesneye yüklemeniz gerekir.

## <a name="defining-endpoints-in-code"></a>Koddaki uç noktaları tanımlama

Aşağıdaki örnek, kodda aşağıdaki gibi bir uç noktanın nasıl belirtildiğini göstermektedir:

- "Hello `IEcho` \<name >!" yanıtıyla birlikte birisinin adını ve yankısını kabul eden bir hizmet türü için bir sözleşme tanımlayın.

- Sözleşme tarafından tanımlanan türde bir `Echo` hizmet uygulayın. `IEcho`

- Hizmet `http://localhost:8000/Echo` için bir uç nokta adresi belirtin.

- `Echo` Bir<xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanarak hizmeti yapılandırın.

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
> Hizmet uygulamasındaki özelliklerinin, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ServiceHostBase>yönteminin ardından değiştirilmemelidir. <xref:System.ServiceModel.Description.ServiceDescription> <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Özelliği <xref:System.ServiceModel.ServiceHost> veiçindeki<xref:System.ServiceModel.ServiceHostBase>yöntemlerigibi bazı üyeler, o noktadan sonra değiştirilirse bir özel durum oluşturur. `AddServiceEndpoint` Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.
>
> Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint> , <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerine <xref:System.ServiceModel.ChannelFactory>çağrısından sonra değerler değiştirilmemelidir. Özelliği <xref:System.ServiceModel.ChannelFactory.Credentials%2A> , o noktadan sonra değiştirilirse bir özel durum oluşturur. Diğer istemci açıklama değerleri hata olmadan değiştirilebilir, ancak sonuç tanımsızdır.
>
> Hizmet veya istemci için, çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce açıklamayı değiştirmeniz önerilir.

## <a name="defining-endpoints-in-configuration"></a>Yapılandırmada uç noktaları tanımlama

Bir uygulama oluştururken, kararları genellikle uygulamayı dağıtan yöneticiye erteleyebilirsiniz. Örneğin, genellikle bir hizmet adresinin (URI) ne olduğunu bilmenin bir yolu yoktur. Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir. Bu esneklik yapılandırma aracılığıyla gerçekleştirilir. Ayrıntılar için bkz. [Hizmetleri yapılandırma](../../../docs/framework/wcf/configuring-services.md).

> [!NOTE]
> Yapılandırma dosyalarını hızlıca oluşturmak için *Dosya*`[,`adı*dosya adı* `]` anahtarıyla [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) `/config:`kullanın.

## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma

Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Temel adres kodda veya yapılandırmada belirtilebilir ve varsayılan uç noktalar, <xref:System.ServiceModel.ICommunicationObject.Open> <xref:System.ServiceModel.ServiceHost>üzerinde çağrıldığında eklenir. Bu örnek, önceki bölümden aynı örnektir, ancak hiçbir uç nokta belirtilmediğinden varsayılan uç noktalar eklenir.

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

 Uç noktalar açık olarak sağlanmışsa, çağrılmadan <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce ' de çağırarak varsayılan uç noktalar eklenebilir. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
