---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c6bc16e97a87461be7b2c4877777329a0005a497
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296205"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>.NET Uzaktan İletişimden WCF'ye Taşınma
Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET uzaktan iletişim kullanan bir uygulamayı geçirmek açıklar. Bu ürünler arasındaki benzer kavramları karşılaştırır ve ardından WCF birkaç ortak uzaktan iletişim senaryolarında nasıl yapılacağını anlatmaktadır.  
  
 .NET uzaktan iletişim yalnızca geriye dönük uyumluluk için desteklenmeyen eski bir üründür. İstemci ve sunucu arasında ayrı güven düzeyleri koruyamadığını çünkü karma güven ortamlar genelinde güvenli değildir. Örneğin, bir .NET uzaktan iletişim uç noktası internet veya güvenilmeyen istemcilere hiçbir zaman sunmalıdır. Varolan uzaktan iletişim öneririz uygulamalar için daha yeni ve daha güvenli teknolojiler geçişi. Uygulama tasarımının yalnızca HTTP kullanan RESTful ise, ASP.NET Web API öneririz. Daha fazla bilgi için bkz: ASP.NET Web API. Uygulama üzerinde SOAP tabanlı ya da Http olmayan protokolleri TCP gibi gerektirir, WCF öneririz.  

## <a name="comparing-net-remoting-to-wcf"></a>.NET uzaktan iletişim için WCF ile karşılaştırma  
 Bu bölüm .NET uzaktan iletişim temel yapı taşlarını WCF eşdeğerleri ile karşılaştırır. Bu yapı taşlarını daha sonra bazı istemci-sunucu senaryoları WCF'de oluşturmak için kullanacağız. Aşağıdaki grafikte, ana arasındaki benzerlikleri ve farkları .NET uzaktan iletişim ve WCF özetler.  
  
||.NET uzaktan iletişim|WCF|  
|-|-------------------|---------|  
|Sunucu türü|Subclass MarshalByRefObject|[ServiceContract] özniteliği ile işaretleyin|  
|Hizmet işlemleri|Sunucu türü genel yöntemleri|[OperationContract] özniteliği ile işaretleyin|  
|Serileştirme|ISerializable veya [Serializable]|DataContractSerializer veya XmlSerializer|  
|Geçirilen nesneleri|Değere göre veya başvuruya göre|Değere göre yalnızca|  
|Hataları/özel durumları|Herhangi bir seri hale getirilebilir özel durumu|FaultContract\<TDetail >|  
|İstemci proxy nesneleri|Kesin türü belirtilmiş saydam proxy'lerin bulunan MarshalByRefObjects için otomatik olarak oluşturulur|Kesin türü belirtilmiş bir proxy oluşturulur üzerine ChannelFactory kullanarak\<TChannel >|  
|Gereken platformu|Microsoft OS hem .NET hem istemci hem de sunucu kullanmanız gerekir|Platformlar arası|  
|İleti biçimi|Özel|Endüstri standartları (SOAP, WS-*, vb..)|  
  
### <a name="server-implementation-comparison"></a>Sunucu uygulaması karşılaştırma  
  
#### <a name="creating-a-server-in-net-remoting"></a>.NET uzaktan iletişim'de bir sunucu oluşturma  
 .NET uzaktan iletişim sunucu türleri, MarshalByRefObject öğesinden türetilir ve istemci, aşağıdaki gibi çağırabileceğiniz yöntemler tanımlayın:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu sunucu türü genel yöntemleri genel sözleşmenin istemciler için kullanılabilir hale gelir.  Sunucunun ortak arabirim ve uygulaması arasında hiçbir ayrım yoktur: bir tür hem de işler.  
  
 Sunucu türü tanımlandıktan sonra istemciler için kullanılabilir aşağıdaki örnekte ister:  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Uzaktan iletişim türünü yapılandırma dosyalarını kullanarak da dahil, bir sunucu olarak kullanılabilir hale getirmek için birçok yolu vardır. Bu yalnızca bir örnektir.  
  
#### <a name="creating-a-server-in-wcf"></a>WCF'de bir sunucu oluşturma  
 WCF eşdeğer adımda, iki tür--' % s'genel "hizmet sözleşmesi" ve somut uygulama oluşturmayı içerir. İlk [ServiceContract] ile işaretli bir arabirim olarak bildirilir. İstemciler için kullanılabilir olan yöntemler [OperationContract] ile işaretli:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucu uygulaması aşağıdaki örnekte gibi ayrı bir somut sınıf tanımlanır:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu tür tanımladıktan sonra WCF sunucunun istemciler için kullanılabilir hale getirilebilir aşağıdaki örnekte ister:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP örneklerin her ikisi de bunları mümkün olduğu kadar benzer tutmak için kullanılır. HTTP kullanan örnekler için bu konunun ilerleyen bölümlerinde senaryo kılavuzlarına bakın.  
  
 Yapılandırmak için birçok yolu vardır ve WCF hizmetlerini barındırmak için. "Kendini" bilinen tek bir örnek budur. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: Bir hizmet sözleşmesini tanımlama](how-to-define-a-wcf-service-contract.md)  
  
-   [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)  
  
-   [Barındırma Hizmetleri](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>İstemci uygulaması karşılaştırması  
  
#### <a name="creating-a-client-in-net-remoting"></a>.NET uzaktan iletişim'de bir istemci oluşturma  
 Bir .NET uzaktan iletişim sunucu nesnesi kullanılabilir yapıldıktan sonra bu istemciler tarafından gibi aşağıdaki örnekte tarafından kullanılabilir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Activator.GetObject() döndürülen RemotingServer örneği bilinen bir "saydam Ara sunucusu olarak." İstemcide RemotingServer türü için genel API uygular, ancak farklı bir işlem veya makine çalışan sunucu nesnesi tüm yöntemleri çağırın.  
  
#### <a name="creating-a-client-in-wcf"></a>WCF'de bir istemci oluşturma  
 Proxy açıkça oluşturmak için bir kanal fabrikası kullanarak WCF eşdeğer adım içerir. Proxy nesnesi gibi uzaktan iletişim, aşağıdaki örnekte sunucu üzerindeki işlemler gibi çağırmak için kullanılabilir:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Bu örnekte, en çok uzak örneğe benzer olduğundan kanal düzeyinde programlama gösterilmektedir. Ayrıca kullanılabilir **hizmet Başvurusu Ekle** yaklaşım Visual Studio'da, istemci programlama basitleştirmek için kod oluşturur. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [İstemci Kanal Düzeyi Programlama](./extending/client-channel-level-programming.md)  
  
-   [Nasıl yapılır: Ekleme, güncelleştirme veya hizmet başvurusunu Kaldır](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Serileştirme kullanım  
 .NET uzaktan iletişim hem de WCF istemci ve sunucu arasında nesneleri göndermek için serileştirme kullanmak, ancak bunlar bu önemli bakımlardan ayrılır:  
  
1. Bunlar farklı seri hale getiricileri genişletme ve kuralları seri hale getirmek ne belirtmek için kullanın.  
  
2. .NET uzaktan iletişim güvenlik sınırları arasında olan diğer katmanındaki kod yürütmek için bir katmanda metot veya özellik erişimi sağlayan "başvuru tarafından" serileştirme destekler. Bu özellik, güvenlik açıklarını ortaya çıkaran ve neden uzak uç noktaları asla güvenilmeyen istemcilere açılmamalıdır temel nedenlerinden biridir.  
  
3. Uzaktan iletişim tarafından kullanılan seri hale getirme çevirme (seri hale getirmek için hangi değil açıkça hariç) ve WCF seri hale getirme kabul etme (seri hale getirmek için hangi üyelerin açıkça işaretleyin).  
  
#### <a name="serialization-in-net-remoting"></a>.NET uzaktan iletişim serileştirme  
 .NET uzaktan iletişim, istemci ve sunucu arasında nesneleri seri hale getrime ve iki yolu destekler:  
  
-   *Değere göre* : nesnenin değerleri katman sınırlarında serileştirilme şeklini ve o nesnenin yeni bir örneğini başka bir katmanında oluşturulur. Yöntemleri veya yeni bu örneğin özelliklerini yapılan her çağrı yalnızca yerel olarak yürütün ve özgün nesne veya katmanı etkilemez.  
  
-   *Başvuruya göre* – özel bir "nesne başvurusu" katman sınırlarında serileştirilmiş. Yöntem ya da o nesnenin özellikleri ile bir katman etkileşim kurduğunda orijinal katman özgün nesneye geri iletişim kurar. Başvuruya göre nesneleri, her iki yönünde – sunucudan istemciye ya da istemciden sunucuya akabilir.  
  
 Uzaktan iletişim tarafından değer türleri [Serializable] özniteliğiyle işaretlenmiş olduğundan veya ISerializable, aşağıdaki örnekte gibi uygulayın:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Başvuruya göre türleri MarshalByRefObject sınıfından, aşağıdaki örnekte gibi türetilir:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Uzaktan iletişimi'nın başvuruya göre nesnelerin etkilerini anlamak son derece önemlidir. Her iki katmanı (istemci veya sunucu) bir katman için bir başvuruya göre nesne gönderirse, tüm yöntem çağrıları geri nesnenin sahibi olan katmanında yürütün. Örneğin, sunucu tarafından döndürülen bir başvuruya göre nesne üzerinde yöntemleri çağırmak bir istemci, sunucu üzerinde kod yürütülür. Benzer şekilde, istemci tarafından sağlanan bir başvuruya göre nesne üzerinde yöntemleri çağırmak bir sunucu, istemci üzerinde kod yürütülür. Bu nedenle, sadece tam güvenilir ortamlar içinde .NET uzaktan iletişim kullanımı önerilir. Güvenilmeyen istemciler için genel bir .NET uzaktan iletişim uç noktayı kullanıma sunmayı bir uzak sunucu saldırılara açık hale getirir.  
  
#### <a name="serialization-in-wcf"></a>Wcf'de seri hale getirme  
 WCF yalnızca değere göre serileştirme destekler. Aşağıdaki örnekte istemci ve sunucu değişimi için bir tür tanımlamak için en yaygın yolu gibidir:  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 [DataContract] özniteliği sıralanabilir ve istemci ile sunucu arasında seri durumdan bu türün biri olarak tanımlar. [DataMember] özniteliği, ayrı özellikler ve alanları serileştirmek için tanımlar.  
  
 WCF katmanlarda nesneyi gönderdiğinde, değerler yalnızca serileştirir ve diğer katmanında nesnesinin yeni bir örneğini oluşturur. Değerlerle tüm etkileşimler nesnesinin yalnızca yerel olarak – ortaya yolu .NET uzaktan iletişim başvuruya göre Nesneleri'ne diğer katmanla iletişim kurarlar değil. Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Özel durum işleme özellikleri  
  
#### <a name="exceptions-in-net-remoting"></a>.NET uzaktan iletişim özel durumları  
 Bir uzak sunucu tarafından oluşturulan özel durumları istemciye gönderilen, serileştirilmiş ve gibi başka bir özel durum istemci üzerinde yerel olarak oluşturulur. Özel durumları [Serializable] ile işaretlemeyi ve özel durum türü alt classing tarafından oluşturulabilir.   Çoğu framework özel durumları zaten serileştirilmiş ve istemcide yeniden durum sunucusu tarafından oluşturulan çoğu izin vererek, bu şekilde işaretlenir. Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri istemciye yanlışlıkla çıkarılabilecek. Bu, yalnızca tamamen güvenilen ortamlarda Remoting kullanılması gereken çok sayıda gerekçe biridir.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Özel durum ve hataları wcf'de  
 WCF rastgele bir özel durum türlerini bilgilerin yanlışlıkla açığa çıkmasına için sunucudan istemciye döndürülmesine izin vermez. Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, bir genel amaçlı FaultException istemcide harekete geçirilmesine neden olur. Bu durum, neden ya da burada bir hata oluştu ve bazı uygulamalar için bu yeterli herhangi bir bilgi içermez. Gereken uygulamalar istemci yapmak için daha zengin hata bilgileri hatalı sözleşme tanımlayarak iletişim.  
  
 Bunu yapmak için önce hata bilgilerini taşımak için [DataContract] türü oluşturun.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Her hizmet işlemi için kullanılacak hatalı sözleşme belirtin.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucu bir FaultException özel durum atma hata koşulları bildirir.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 Ve istemci, sunucuya istek yaptığında, normal özel durumlar olarak hatalar yakalayabilir.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Hata sözleşmeleri hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
  
#### <a name="security-in-net-remoting"></a>.NET uzaktan iletişim güvenlik  
 Bazı .NET uzaktan iletişim kanalları, kimlik doğrulaması ve şifrelemeyi kanal katmanında (IPC ve TCP) gibi güvenlik özelliklerini destekler. HTTP kanalı, kimlik doğrulama ve şifreleme için Internet Information Services (IIS) kullanır. Bu destek rağmen bir güvenli olmayan bir iletişim protokolü .NET uzaktan iletişim göz önünde bulundurun ve sadece tam güvenilir ortamlar içinde kullanın. Hiçbir zaman Internet veya güvenilmeyen istemciler için genel bir uzak uç nokta kullanıma sunar.  
  
#### <a name="security-in-wcf"></a>WCF'de Güvenlik  
 WCF ile göz önünde bulundurularak, kısmen türlerini .NET uzaktan iletişim'de bulunan güvenlik açıklarına yönelik olarak tasarlanmıştır. WCF güvenlik hem aktarım hem de ileti düzeyinde sunar ve kimlik doğrulama, yetkilendirme, şifreleme ve benzeri pek çok seçenek sunar. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Güvenlik](./feature-details/security.md)  
  
-   [WCF Güvenlik Kılavuzu](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>WCF'ye taşınma  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Neden uzaktan iletişimden WCF'ye geçirme?  
  
-   **.NET uzaktan iletişim eski bir üründür.** Bölümünde anlatıldığı gibi [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), eski bir ürün olarak kabul edilir ve yeni geliştirme projeleri için önerilmez. WCF veya ASP.NET Web API yeni ve mevcut uygulamalar için önerilir.  
  
-   **WCF platformlar arası standartlar kullanır.** WCF ile platformlar arası birlikte çalışabilirlik düşünülerek tasarlanmıştır ve çoğu endüstri standartları destekler (SOAP, WS-Security, WS-Trust, vs.). Bir WCF hizmeti, Windows dışındaki işletim sistemleri üzerinde çalışan istemciler ile çalışabilirler. Uzaktan iletişim, öncelikle bir Windows işletim sisteminde .NET framework kullanarak sunucu ve istemci uygulamaları çalıştırdığı ortamlar için tasarlanmıştır.  
  
-   **WCF yerleşik güvenlik sahiptir.** WCF güvenlik düşünülerek tasarlanmıştır ve kimlik doğrulaması, aktarım düzeyi güvenlik, ileti düzeyi güvenlik, vb. pek çok seçenek sunar. Uzaktan iletişim uygulamalarını çalışmak kolaylaştırmak için tasarlanmıştır ancak güvenilir olmayan ortamlarda güvenli olacak şekilde tasarlanmamıştır. WCF, güvenilir ve güvenilir olmayan ortamlarda çalışacak şekilde tasarlanmıştır.  
  
### <a name="migration-recommendations"></a>Geçiş önerileri  
 .NET uzaktan iletişimden WCF'ye geçirme önerilen adımlar şunlardır:  
  
-   **Hizmet sözleşmesi oluşturun.** Hizmet arabirimi türlerinizi tanımlamak ve bunları [ServiceContract] özniteliği ile işaretleyin. İstemciler [OperationContract] ile çağırmak için izin verilecek tüm yöntemleri işaretleyin.  
  
-   **Veri sözleşmesi oluşturun.** Sunucu ve istemci arasında değiş tokuş ve bunları [DataContract] özniteliği ile işaretleyin veri türlerini tanımlayın. Bir istemci kullanın [DataMember] ile izin verilecek tüm alanlar ve Özellikler'i işaretleyin.  
  
-   **Hatalı sözleşme oluşturma (isteğe bağlı).** Hatalarla karşılaştı, sunucu ve istemci arasında alınıp türleri oluşturun. Bu türler ile [DataContract] ve [DataMember] serileştirilebilir hale getirmek için bu seçeneği işaretleyin. Bunları [OperationContract] ile işaretli tüm hizmet işlemleri için de [döndürme olasılığı hangi hatalarını belirtmek için FaultContract] ile işaretleyin.  
  
-   **Yapılandırma ve hizmet barındırın.** Hizmet sözleşmesi oluşturulduktan sonra sonraki adım bir uç nokta adresindeki hizmet kullanıma sunmak için bir bağlama yapılandırmaktır. Daha fazla bilgi için [uç noktalar: Adresler, bağlamalar ve sözleşmeleri](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Bir uzaktan uygulama WCF'ye geçirilmiş olan sonra .NET uzaktan iletişim bağımlılıkları kaldırın yine de önemlidir. Bu, herhangi bir uzaktan iletişim açığını uygulamadan kaldırılmasını sağlar. Bu adımlar şunlardır:  
  
-   **MarshalByRefObject bırakmaktır.** MarshalByRefObject türü, yalnızca uzaktan iletişim için bulunmaktadır ve WCF tarafından kullanılmaz. MarshalByRefObject alt sınıf herhangi bir uygulama türünün kaldırılan veya değiştirilen.  
  
-   **[Serializable] kullanımı ve ISerializable bırakmaktır.** [Serializable] özniteliği ve ISerializable arabirimini başlangıçta güvenilir ortamlar içinde türleri serileştirmek için tasarlanmıştır ve Uzaktan iletişim tarafından kullanılır. WCF seri hale getirme [DataContract] ile işaretlenen türler ve [DataMember] kullanır. Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.  
  
### <a name="migration-scenarios"></a>Geçiş senaryoları  
 Artık aşağıdaki ortak uzaktan iletişim senaryolarında WCF yerine getirmeyi bakalım:  
  
1. Sunucu istemciye bir nesne tarafından değeri döndürür.  
  
2. Sunucu bir nesne başvuru tarafından istemciye döndürür.  
  
3. İstemci bir nesneyi değere göre sunucuya gönderir.  
  
> [!NOTE]
>  Bir nesne başvuruya göre istemciden sunucuya gönderme WCF'de izin verilmez.  
  
 Bu senaryolar üzerinden okurken aşağıdaki örnekteki gibi .NET uzaktan iletişim için sunduğumuz temel arabirimleri konum varsayılır. .NET uzaktan iletişim uygulaması WCF eşdeğer bir işlevselliği uygulamak için yalnızca nasıl kullanılacağını örneklendiren istediğimizden burada önemli değildir.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Senaryo 1: Hizmet bir nesne değeri döndürür.  
 Bu senaryo, bir nesne istemciye değere göre döndürmenin bir sunucu gösterir. Aşağıdaki adımları normal bir WCF hizmeti oluşturmak nasıl tanımlamaları yeterlidir, böylece WCF her zaman nesneleri sunucudan değere göre döndürür.  
  
1. WCF hizmeti için ortak bir arabirim tanımlayarak işe başlamak ve [ServiceContract] özniteliği ile işaretleyin. [OperationContract] istemcimizin çağıran sunucu taraflı yöntemleri tanımlamak için kullanırız.  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. Sonraki adım, bu hizmet için veri anlaşması oluşturmaktır. [DataContract] özniteliği ile işaretlenmiş sınıfların (arabirimler değil) oluşturarak bunu. Tek tek özellikler veya alanları hem istemci hem de sunucu görünür istiyoruz, [DataMember] ile işaretlenir. İzin verilmesi için türetilen türlerin istiyoruz, biz bunları tanımlamak için [KnownType] özniteliğini kullanmanız gerekir. WCF türleri yalnızca, serileştirilecek veya seri durumdan çıkarılmakta olan bu hizmet için hizmet arabirimi ve bu "bilinen türler" olanak sağlar. Bu listede olmayan herhangi bir türü exchange çalışılıyor reddedilir.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Ardından, hizmet arabirimi uygulamasını sağlar.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. WCF hizmeti çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL'den bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmek ihtiyacımız var. Bu durum genellikle aşağıdaki bölümlerde sunucu projenin web.config dosyasına ekleyerek gerçekleştirilir.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. WCF hizmeti, ardından aşağıdaki kod ile başlatılabilir:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Bu ServiceHost başlatıldığında, uygun sözleşmeyi, bağlamayı ve uç nokta oluşturmak için web.config dosyasını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](./configuring-services-using-configuration-files.md). Sunucu başlangıç bu stil, kendi kendine barındırma olarak bilinir. WCF hizmetleri barındırma için diğer seçenekler hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](./hosting-services.md).  
  
6. İstemci projenin app.config hizmet uç noktası için eşleşen bağlama bilgileri belirtmesi gerekir. Visual Studio'da bunu yapmanın en kolay yolu kullanmaktır **hizmet Başvurusu Ekle**, hangi otomatik olarak güncelleştirilir app.config dosyası. Alternatif olarak, aynı değişiklikleri el ile eklenebilir.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Kullanma hakkında daha fazla bilgi için **hizmet Başvurusu Ekle**, bkz: [nasıl yapılır: Ekleme, güncelleştirme veya hizmet başvurusunu kaldırın](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Şimdi biz WCF Hizmeti istemciden çağırabilirsiniz. Bu hizmet için kanal fabrikası oluşturma için bir kanal isteyen ve doğrudan bu kanalda istiyoruz yöntemi çağırma bunu. Kanal hizmet arabirimi uygulayan ve bizim için temel alınan istek/yanıt mantığı işler çünkü biz bunu yapabilirsiniz. Bu yöntem çağrısının dönüş değeri, sunucunun yanıt seri durumdan çıkarılmış kopyasıdır.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 WCF tarafından sunucudan istemciye döndürülen nesneleri tarafından her zaman değerlerdir. Sunucu tarafından gönderilen verileri seri durumdan çıkarılmış kopyalarını nesneleridir. İstemci, sunucu kodu çağırmalarla çağırma herhangi olma tehlikesi olmadan bu yerel kopyalar üzerinde yöntemleri çağırabilir.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Senaryo 2: Sunucu başvuruya göre bir nesne döndürür.  
 Bu senaryo, bir nesne başvurusu tarafından istemciye sağlayan sunucu gösterir. .NET uzaktan iletişim'de bu otomatik olarak MarshalByRefObject öğesinden türetilen her tür için işlenir başvuruya göre sıralanmış olan. Bu senaryoya örnek olarak, bağımsız kapatamaması sunucu tarafı nesneleri birden çok istemci izin verir. Daha önce belirtildiği gibi bir WCF hizmeti tarafından döndürülen nesne her zaman değere göre bu yüzden bir başvuruya göre nesnesinin doğrudan bir eşdeğer ancak başvuruya göre semantiği kullanarak benzer bir şey elde etmek olası bir <xref:System.ServiceModel.EndpointAddress10> nesne. Bu sunucuda kapatamaması başvuru tarafından nesnesini almak için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir bir nesnedir. Bu, birden fazla istemciyle sunucu tarafı nesneleri kapatamaması bağımsız olması, senaryosu sağlar.  
  
1. İlk olarak biz kapatamaması nesnenin kendisine karşılık gelen bir WCF Hizmeti sözleşmesi tanımlamanız gerekir.  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  Oturum nesnesi [ServiceContract] ile işaretli, normal yapmadan WCF hizmet arabirimi dikkat edin. Sessionmode'u ayarlama özelliği kapatamaması hizmet olacaktır gösterir. WCF'de, oturum, birden çok ileti iki uç nokta arasında gönderilen ilişkilendirme bir yoludur. Bu, istemci bu hizmet için bir bağlantı alır, sonra oturumu istemci ve sunucu arasında kurulur, anlamına gelir. İstemci bu oturumla içinde için tüm etkileşimler bir tek benzersiz bir sunucu tarafı nesne örneği kullanın.  
  
2. Ardından, bu hizmet arabiriminin uygulamasını sağlamak ihtiyacımız var. [ServiceBehavior] ile belirten ve InstanceContextMode ayarlayarak, biz WCF her oturum için benzersiz bir örnek bu türde kullanılacak istiyoruz söyleyin.  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. Şimdi bu kapatamaması nesne örneği elde etmek için bir yol gerekir. EndpointAddress10 nesneyi döndürür. başka bir WCF Hizmeti arabirimi oluşturarak bunu. Bu istemci kapatamaması nesnesi oluşturmak için kullanabileceğiniz bir uç nokta seri hale getirilebilir bir biçimidir.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     Ve biz bu WCF Hizmeti uygulayın:  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     Bu uygulama kapatamaması nesneleri oluşturmak için singleton kanal fabrikası tutar. GetInstanceAddress() çağrıldığında, bir kanal oluşturur ve etkili bir şekilde bu kanal ile ilişkili uzak adresini işaret eden EndpointAddress10 nesne oluşturur. EndpointAddress10 yalnızca istemci tarafından değeri olarak döndürülebilecek bir veri türü var.  
  
4. Biz aşağıdaki örnekte gösterildiği gibi iki şunları yaparak sunucunun yapılandırma dosyasını değiştirmeniz gerekir:  
  
    1.  Bildirme bir \<istemci > kapatamaması nesne için uç nokta açıklayan bölümü. Bunun gerekli olmasının nedeni, sunucunun da bu durumda istemci olarak davranır.  
  
    2.  Uç noktaları için Fabrika ve sessionful nesne bildirir. Bu istemci, hizmet uç noktaları ile EndpointAddress10 alma ve oturum kanalı oluşturmak için iletişim kurmasına izin vermek gereklidir.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     ' İ tıklatın ve ardından şu hizmetlerin başlayabilirsiniz:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Bu aynı uç noktaları, projenin app.config dosyasında bildirerek istemcinin yapılandırıyoruz.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. Bu oturumdaki nesnesi oluşturma ve kullanma hakkında bilgi için istemci aşağıdakileri yapmanız gerekir:  
  
    1.  ISessionBoundFactory hizmete bir kanal oluşturun.  
  
    2.  Bu kanal, bir EndpointAddress10 almak için bu hizmeti çağırmak için kullanın.  
  
    3.  EndpointAddress10 kapatamaması bir nesne elde etmek için bir kanal oluşturmak için kullanın.  
  
    4.  Birden çok çağrı aynı örneğini kalır göstermek için kapatamaması nesne ile etkileşim kurun.  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF değere göre her zaman nesnelerini döndürür, ancak başvuruya göre semantiği EndpointAddress10 genelindeki denk desteklemek mümkündür. Bu istemcinin sonra Bu raporla herhangi bir WCF hizmeti gibi etkileşim kurmasını kapatamaması bir WCF hizmeti örneği isteği izin verir.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Senaryo 3: İstemci sunucusu bir değere göre örneği gönderir.  
 Bu senaryo, temel olmayan nesne örneği, değere göre sunucuya gönderme istemci gösterir. WCF nesneleri değerine göre yalnızca gönderir. çünkü bu senaryo normal WCF kullanım gösterir.  
  
1. Senaryo 1 aynı WCF hizmetinden kullanın.  
  
2. İstemci, yeni bir değere göre nesne (müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesne göndermek için kullanın.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     Müşteri nesnesi seri hale getirilmiş ve o nesnenin yeni bir kopyasını nereden serisi sunucuya gönderilir.  
  
    > [!NOTE]
    >  Bu kod Ayrıca, türetilmiş bir tür (PremiumCustomer) gönderme gösterir. Hizmet arabirimi müşteri nesnesi bekliyor, ancak müşteri sınıfı [KnownType] özniteliğini PremiumCustomer de izin belirtilen. WCF serileştirmek veya bu hizmet arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.  
  
 Veri değişimleri normal WCF tarafından değerlerdir. Bu garanti bu veri nesneleri birinde yöntemlerini çağırma, yalnızca yerel olarak yürütür: kod bir katman çağırma kullanılamaz. Başvuru ile döndürülen nesne gibi bir şey elde etmek mümkün olmakla birlikte *gelen* sunucuya bir istemci bir başvuruya göre nesneyi geçirmek mümkün değildir *için* sunucu. İstemci ve sunucu arasında sürekli bir konuşma gerektiren bir senaryo, bir çift yönlü hizmet kullanarak WCF'de gerçekleştirilebilir. Daha fazla bilgi için [çift yönlü Hizmetler](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Özet  
 .NET uzaktan iletişim sadece tam güvenilir ortamlar içinde kullanılmak üzere bir iletişim çerçevedir. Bu, eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir. Yeni uygulamalar oluşturmak için kullanılmamalıdır. Buna karşılık, WCF güvenlik düşünülerek tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir. Microsoft önerir, mevcut uzaktan iletişim uygulamalarını geçişi WCF veya ASP.NET Web API'si yerine kullanılacak.
