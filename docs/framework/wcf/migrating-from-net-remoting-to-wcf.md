---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183959"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>.NET Uzaktan İletişimden WCF'ye Taşınma
Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET Remoting kullanan bir uygulamanın nasıl geçirilen açıklanmaktadır. Bu ürünler arasındaki benzer kavramları karşılaştırır ve wcf'de birkaç yaygın Remoting senaryosunun nasıl gerçekleştirileceğine açıklanır.  
  
 .NET Remoting, yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür. İstemci ve sunucu arasındaki ayrı güven düzeylerini koruyamadığından karışık güven ortamları arasında güvenli değildir. Örneğin, .NET Remoting bitiş noktasını Hiçbir zaman Internet'e veya güvenilmeyen istemcilere maruz bırakmamalısınız. Mevcut Remoting uygulamalarının daha yeni ve daha güvenli teknolojilere geçirilmelerini öneririz. Uygulamanın tasarımı yalnızca HTTP kullanıyorsa ve RESTful ise, Web API ASP.NET öneririz. Daha fazla bilgi için ASP.NET Web API'ye bakın. Uygulama SOAP'a dayanıyorsa veya TCP gibi Http dışı protokoller gerektiriyorsa, WCF'yi öneririz.  

## <a name="comparing-net-remoting-to-wcf"></a>.NET Remoting ile WCF karşılaştırması  
 Bu bölümde .NET Remoting'in temel yapı taşları WCF eşdeğerleri ile karşılaştırılır. Bu yapı taşlarını daha sonra WCF'de bazı ortak istemci sunucu senaryoları oluşturmak için kullanacağız. Aşağıdaki grafikte .NET Remoting ve WCF arasındaki temel benzerlikler ve farklar özetlenmiştir.  
  
||.NET uzaktan iletişim|WCF|  
|-|-------------------|---------|  
|Sunucu türü|Alt sınıf MarshalByRefObject|[ServiceContract] özniteliği ile işaretle|  
|Servis işlemleri|Sunucu türünde genel yöntemler|[OperationContract] özniteliği ile işaretle|  
|Serileştirme|ISerializable veya [Serializable]|DataContractSerializer veya XmlSerializer|  
|Geçen nesneler|Değer veya referans|Yalnızca göredeğer|  
|Hatalar/özel durumlar|Herhangi bir serializable özel durum|Arıza\<Sözleşme Detay>|  
|İstemci proxy nesneleri|Güçlü bir şekilde yazılan saydam yakınlıklar MareşalByRefObjects'ten otomatik olarak oluşturulur|Güçlü dakti-sa'lar ChannelFactory\<TChannel kullanılarak isteğe bağlı olarak oluşturulur>|  
|Platform gerekli|Hem istemci hem de sunucu Microsoft OS ve .NET kullanmalıdır|Platformlar arası|  
|İleti biçimi|Özel|Endüstri standartları (SOAP, WS-*, vb.)|  
  
### <a name="server-implementation-comparison"></a>Sunucu Uygulama Karşılaştırması  
  
#### <a name="creating-a-server-in-net-remoting"></a>.NET Remoting'de Sunucu Oluşturma  
 .NET Remoting sunucu türleri MarshalByRefObject'ten türemiş olmalı ve istemcinin çağırabileceği yöntemleri tanımlamalıdır:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu sunucu türünün ortak yöntemleri istemcilerin kullanabileceği ortak sözleşme haline gelir.  Sunucunun ortak arabirimi ile uygulanması arasında ayrım yoktur – bir tür her ikisini de işler.  
  
 Sunucu türü tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi istemcilerin kullanımına sunulabilir:  
  
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
  
 Yapılandırma dosyalarını kullanmak da dahil olmak üzere Remoting türünü sunucu olarak kullanılabilir hale getirmenin birçok yolu vardır. Bu sadece bir örnektir.  
  
#### <a name="creating-a-server-in-wcf"></a>WCF'de Sunucu Oluşturma  
 WCF'deki eşdeğer adım, iki tür -kamu "hizmet sözleşmesi" ve somut uygulama olmak üzere oluşturulmasını içeriyor. İlki [ServiceContract] ile işaretlenmiş bir arabirim olarak bildirilir. İstemciler için kullanılabilen yöntemler [OperationContract] ile işaretlenir:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucunun uygulaması aşağıdaki örnekte olduğu gibi ayrı bir somut sınıfta tanımlanır:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu türler tanımlandıktan sonra, WCF sunucusu aşağıdaki örnekte olduğu gibi istemcilerin kullanımına sunulabilir:  
  
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
> TCP, her iki örnekte de mümkün olduğunca benzer tutmak için kullanılır. HTTP'yi kullanan örnekler için bu konunun ilerleyen yerlerine bakın.  
  
 WCF hizmetlerini yapılandırmanın ve barındırmanın birçok yolu vardır. Bu sadece bir örnektir, "kendi kendine barındırılan" olarak bilinir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](how-to-define-a-wcf-service-contract.md)  
  
- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)  
  
- [Barındırma Hizmetleri](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>İstemci Uygulama Karşılaştırması  
  
#### <a name="creating-a-client-in-net-remoting"></a>.NET Remoting'de İstemci Oluşturma  
 Bir .NET Remoting sunucu nesnesi kullanıma sunulduktan sonra, aşağıdaki örnekte olduğu gibi istemciler tarafından tüketilebilir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Activator.GetObject() döndürülen RemotingServer örneği "saydam proxy" olarak bilinir. İstemcide RemotingServer türü için genel API uygular, ancak tüm yöntemler farklı bir işlem veya makinede çalışan sunucu nesnesini çağırır.  
  
#### <a name="creating-a-client-in-wcf"></a>WCF'de İstemci Oluşturma  
 WCF eşdeğer adım açıkça proxy oluşturmak için bir kanal fabrikası kullanarak içerir. Remoting gibi proxy nesnesi de aşağıdaki örnekte olduğu gibi sunucudaki işlemleri çağırmak için kullanılabilir:  
  
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
  
 Bu örnek, Remoting örneğine en çok benzediği için programlamayı kanal düzeyinde gösterir. Ayrıca, Visual Studio'da istemci programlamayı basitleştirmek için kod üreten **Hizmet Başvurusu Ekle** yaklaşımı da mevcuttur. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [İstemci Kanal Düzeyi Programlama](./extending/client-channel-level-programming.md)  
  
- [Nasıl yapilir: Hizmet Başvurusu Ekleme, Güncelleştirme veya Kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Serileştirme Kullanımı  
 Hem .NET Remoting hem de WCF, istemci ve sunucu arasında nesneleri göndermek için serileştirme kullanır, ancak bunlar şu önemli şekillerde farklılık gösterir:  
  
1. Neyi seri hale getirmek için farklı serializers ve kurallar kullanırlar.  
  
2. .NET Remoting, bir katmanda yöntem veya özellik erişiminin diğer katmanda, güvenlik sınırlarının ötesinde olan kodu yürütmesine olanak tanıyan "referans" serileştirmeyi destekler. Bu özellik güvenlik açıklarını ortaya çıkarır ve Remoting uç noktalarının asla güvenilmeyen istemcilere maruz kalmaması için temel nedenlerden biridir.  
  
3. Remoting tarafından kullanılan serileştirme devre dışı bırakma (serileştirmeme ne hariç) ve WCF serileştirme opt-in (açıkça hangi üyeleri serileştirmek için işaret) olduğunu.  
  
#### <a name="serialization-in-net-remoting"></a>.NET Remoting'de serileştirme  
 .NET Remoting, istemci ve sunucu arasındaki nesneleri serihale ve deserialize etmenin iki yolunu destekler:  
  
- *Değer* olarak – nesnenin değerleri katman sınırları arasında seri hale getirilir ve bu nesnenin yeni bir örneği diğer katmanda oluşturulur. Bu yeni örneğin yöntemlerine veya özelliklerine yapılan tüm çağrılar yalnızca yerel olarak yürütülür ve özgün nesneyi veya katmanı etkilemez.  
  
- *Referans olarak* – özel bir "nesne başvurusu" katman sınırları arasında seri hale getirilir. Bir katman, o nesnenin yöntemleri veya özellikleriyle etkileşime girdiğinde, özgün katmandaki özgün nesneye geri iletir. Başvuru nesneleri her iki yönde de akabilir – sunucudan istemciye veya istemciden sunucuya.  
  
 Remoting'deki yan değer türleri aşağıdaki örnekte olduğu gibi [Serializable] özniteliği ile işaretlenir veya ISerializable'ı uygular:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Başvuru türleri aşağıdaki örnekte olduğu gibi MarshalByRefObject sınıfından türetilmiştir:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Remoting'in referans nesnelerinin sonuçlarını anlamak son derece önemlidir. Katmandan biri (istemci veya sunucu) diğer katmana bir by-reference nesnesi gönderirse, tüm yöntem çağrıları nesneye sahip olan katmanda yürütülür. Örneğin, sunucu tarafından döndürülen bir başvuru nesnesi üzerinde arama yöntemleri çağıran bir istemci sunucuda kod yürütecektir. Benzer şekilde, istemci tarafından sağlanan bir başvuru nesnesi üzerinde arama yöntemleri bir sunucu istemci üzerinde kodu geri yürütecektir. Bu nedenle, .NET Remoting'in kullanımı yalnızca tam güvenilen ortamlarda önerilir. Bir public .NET Remoting bitiş noktasını güvenilmeyen istemcilere vermek, Remoting sunucusunun saldırıya açık olmasını sağlar.  
  
#### <a name="serialization-in-wcf"></a>WCF'de serileştirme  
 WCF yalnızca yan değer serileştirmeyi destekler. İstemci ve sunucu arasında alışverişyapmak için bir tür tanımlamak için en yaygın yolu aşağıdaki örnekte olduğu gibi:  
  
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
  
 [DataContract] özniteliği, bu türü istemci ve sunucu arasında serileştirilebilen ve deserialize edilebilen bir tür olarak tanımlar. [DataMember] özniteliği, seri hale getirmek için tek tek özellikleri veya alanları tanımlar.  
  
 WCF bir nesneyi katmanlar arasında gönderdiğinde, yalnızca değerleri seri hale eder ve diğer katmandaki nesnenin yeni bir örneğini oluşturur. Nesnenin değerleri ile herhangi bir etkileşim yalnızca yerel olarak oluşur - onlar diğer katman ile iletişim yok .NET Remoting by-reference nesneleri yapmak. Daha fazla bilgi için [serileştirme ve deserialization'a](./feature-details/serialization-and-deserialization.md)bakın.  
  
### <a name="exception-handling-capabilities"></a>Özel Durum İşleme Yetenekleri  
  
#### <a name="exceptions-in-net-remoting"></a>.NET Remoting'deki özel durumlar  
 Remoting sunucusu tarafından atılan özel durumlar seri hale getirilir, istemciye gönderilir ve diğer özel durumlar gibi istemciye yerel olarak atılır. Özel özel durumlar, Özel Durum türünü alt sınıflayarak ve [Serializable] ile işaretleyerek oluşturulabilir.   Çoğu çerçeve özel durumu zaten bu şekilde işaretlenir ve çoğu sunucu tarafından atılmasına, seri hale getirilmesine ve istemciye yeniden atılmasına izin verir. Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafındaki bilgiler istemeden istemciye açıklanabilir. Bu, Remoting'in yalnızca tam güvenilen ortamlarda kullanılmasının birçok nedenidir.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>WCF'deki Özel Durumlar ve Hatalar  
 WCF, yanlışlıkla bilgi ifşasına yol açabileceğinden, rasgele özel durum türlerinin sunucudan istemciye döndürülmesine izin vermez. Bir hizmet işlemi beklenmeyen bir özel durum atarsa, genel amaçlı bir hata özel durum istemcisi üzerine atılmasına neden olur. Bu özel durum, sorunun neden veya nerede oluştuğu hakkında herhangi bir bilgi taşımaz ve bazı uygulamalar için bu yeterlidir. İstemciye daha zengin hata bilgilerini iletmesi gereken uygulamalar, hata sözleşmesi tanımlayarak bunu yapar.  
  
 Bunu yapmak için, önce hata bilgilerini taşımak için bir [DataContract] türü oluşturun.  
  
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
  
 Her hizmet işlemi için kullanılacak hata sözleşmesini belirtin.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucu, hata özel durumlarını bir Hata Özel Durum atarak bildirir.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 İstemci sunucuya bir istekte bulunsa, hataları normal özel durumlar olarak yakalayabilir.  
  
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
  
 Hata sözleşmeleri hakkında daha <xref:System.ServiceModel.FaultException>fazla bilgi için bkz.  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
  
#### <a name="security-in-net-remoting"></a>.NET Remoting'de güvenlik  
 Bazı .NET Remoting kanalları, kanal katmanındaki kimlik doğrulama ve şifreleme (IPC ve TCP) gibi güvenlik özelliklerini destekler. HTTP kanalı, hem kimlik doğrulaması hem de şifreleme için Internet Information Services'a (IIS) dayanır. Bu desteğe rağmen, .NET Güvenli olmayan bir iletişim protokolünü yeniden ifade etmeyi ve yalnızca tam güvenilen ortamlarda kullanmayı düşünmelisiniz. Genel Remoting bitiş noktasını asla Internet'e veya güvenilmeyen istemcilere ifşa etmeyin.  
  
#### <a name="security-in-wcf"></a>WCF'de Güvenlik  
 WCF, kısmen .NET Remoting'de bulunan güvenlik açıklarını gidermek için güvenlik göz önünde bulundurularak tasarlanmıştır. WCF hem aktarım hem de ileti düzeyinde güvenlik sunar ve kimlik doğrulama, yetkilendirme, şifreleme ve benzeri birçok seçenek sunar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Güvenlik](./feature-details/security.md)  
  
- [WCF Güvenlik Rehberi](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>WCF'ye geçiş  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Neden Remoting'den WCF'ye geçiş?  
  
- **.NET Remoting eski bir üründür.** [.NET Remoting'de](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)açıklandığı gibi, eski bir ürün olarak kabul edilir ve yeni geliştirme için önerilmez. WCF veya ASP.NET Web API'si yeni ve varolan uygulamalar için önerilir.  
  
- **WCF çapraz platform standartları kullanır.** WCF, platformlar arası birlikte çalışabilirlik göz önünde bulundurularak tasarlanmıştır ve birçok endüstri standardına (SOAP, WS-Security, WS-Trust, vb.) destek vermektedir. Bir WCF hizmeti, Windows dışındaki işletim sistemlerinde çalışan istemcilerle birlikte çalışabilir. Remoting, öncelikle windows işletim sisteminde .NET Framework kullanılarak hem sunucu hem de istemci uygulamalarının çalıştığı ortamlar için tasarlanmıştır.
  
- **WCF yerleşik güvenlik vardır.** WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve kimlik doğrulama, aktarım düzeyi güvenliği, ileti düzeyi güvenliği, vb. için birçok seçenek sunar. Remoting, uygulamaların birlikte çalışmasını kolaylaştırmak için tasarlanmıştır, ancak güvenilmeyen ortamlarda güvenli olacak şekilde tasarlanmamaktadır. WCF hem güvenilir hem de güvenilmeyen ortamlarda çalışacak şekilde tasarlanmıştır.  
  
### <a name="migration-recommendations"></a>Geçiş Önerileri  
 .NET Remoting'den WCF'ye geçiş için önerilen adımlar şunlardır:  
  
- **Hizmet sözleşmesini oluşturun.** Hizmet arabirimi türlerinizi tanımlayın ve [ServiceContract] özniteliğiyle işaretleyin. Müşterilerin [OperationContract] ile aramalarına izin verilecek tüm yöntemleri işaretleyin.  
  
- **Veri sözleşmesini oluşturun.** Sunucu ve istemci arasında değiş tokuş edilecek veri türlerini tanımlayın ve bunları [DataContract] özniteliğiyle işaretleyin. İstemcinin kullanmasına izin verilecek tüm alanları ve özellikleri [DataMember] ile işaretleyin.  
  
- **Hata sözleşmesini oluşturun (isteğe bağlı).** Hatalarla karşılaşıldığında sunucu ve istemci arasında değiş tokuş edilecek türleri oluşturun. Serileştirilebilir hale getirmek için bu türleri [DataContract] ve [DataMember] ile işaretleyin. [OperationContract] ile işaretlediğiniz tüm hizmet işlemleri için, hangi hataları geri getirebileceklerini belirtmek için bunları [Hata Sözleşmesi] ile işaretleyin.  
  
- **Hizmeti yapılandırın ve barındırın.** Hizmet sözleşmesi oluşturulduktan sonra, bir sonraki adım, hizmeti bir bitiş noktasında ortaya çıkarmak için bir bağlama yapılandırmaktır. Daha fazla bilgi için [Bkz. Uç Noktalar: Adresler, Ciltler ve Sözleşmeler.](./feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 Bir Remoting uygulaması WCF'ye geçirildikten sonra ,.NET Remoting'e olan bağımlılıkları kaldırmak yine de önemlidir. Bu, Remoting güvenlik açıklarının uygulamadan kaldırılmasını sağlar. Bu adımlar şunlardır:  
  
- **MarshalByRefObject kullanımını durdurun.** MarshalByRefObject türü yalnızca Remoting için vardır ve WCF tarafından kullanılmaz. Alt sınıf MarshalByRefObject kaldırılmalıdır veya değiştirilmelidir herhangi bir uygulama türleri.  
  
- **[Serializable] ve ISerializable kullanımını durdurun.** [Serializable] öznitelik ve ISerializable arabirimi başlangıçta güvenilen ortamlarda türleri serileştirmek için tasarlanmıştır ve Remoting tarafından kullanılır. WCF serileştirmesi, [DataContract] ve [DataMember] ile işaretlenmiş türlere dayanır. Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanmak ve ISerializable veya [Serializable] kullanmak için değiştirilmelidir.  
  
### <a name="migration-scenarios"></a>Geçiş Senaryoları  
 Şimdi WCF'de aşağıdaki ortak Remoting senaryolarının nasıl gerçekleştirileceğine bakalım:  
  
1. Sunucu istemciye bir nesne yan değer döndürür  
  
2. Sunucu istemciye bir nesne by-reference döndürür  
  
3. İstemci sunucuya bir nesneyi göre değer gönderir  
  
> [!NOTE]
> WCF'de istemciden sunucuya nesne gönderme izni verilmez.  
  
 Bu senaryoları okurken,.NET Remoting için temel arabirimlerimizin aşağıdaki örnek gibi göründüğünü varsayalım. .NET Remoting uygulaması burada önemli değildir, çünkü yalnızca eşdeğer işlevselliği uygulamak için WCF'nin nasıl kullanılacağını göstermek istiyoruz.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Senaryo 1: Hizmet Nesneyi Değere Göre Döndürür  
 Bu senaryo, bir nesneyi istemciye değer olarak döndüren bir sunucuyu gösterir. WCF nesneleri her zaman sunucudan değer olarak döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmetinin nasıl oluşturulabildiğini açıklar.  
  
1. WCF hizmeti için ortak arabirim tanımlayarak başlayın ve [ServiceContract] özniteliği ile işaretleyin. İstemcimizin çağıracağı sunucu tarafındaki yöntemleri tanımlamak için [OperationContract] kullanırız.  
  
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
  
2. Bir sonraki adım, bu hizmet için veri sözleşmesi oluşturmaktır. Bunu, [DataContract] özniteliği ile işaretlenmiş sınıflar (arabirimler değil) oluşturarak yapıyoruz. Hem istemci hem de sunucu tarafından görülebilmesini istediğimiz tek tek özellikler veya alanlar [DataMember] ile işaretlenir. Türemiş türlerine izin verilmesini istiyorsak, bunları tanımlamak için [KnownType] özniteliğini kullanmalıyız. WCF'nin bu hizmet için seri hale getirilmesine veya seri hale getirilmesine izin verecek tek türleri, hizmet arabirimindeki ler ve bu "bilinen türler"dir. Bu listede olmayan başka bir tür değiştirme girişimi reddedilecektir.  
  
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
  
3. Ardından, hizmet arabirimi için uygulama sağlar.  
  
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
  
4. WCF hizmetini çalıştırmak için, belirli bir WCF bağlama kullanarak bu hizmet arabirimini belirli bir URL'de ortaya çıkaran bir bitiş noktası beyan etmemiz gerekir. Bu genellikle sunucu projesinin web.config dosyasına aşağıdaki bölümleri ekleyerek yapılır.  
  
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
  
5. WCF hizmeti daha sonra aşağıdaki kodla başlatılabilir:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Bu ServiceHost başlatıldığında, uygun sözleşme, bağlama ve bitiş noktası kurmak için web.config dosyasını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için [bkz.](./configuring-services-using-configuration-files.md) Sunucuyu başlatma bu stil kendi kendine barındırma olarak bilinir. WCF hizmetlerini barındırmak için diğer seçenekler hakkında daha fazla bilgi edinmek için [Barındırma Hizmetleri'ne](./hosting-services.md)bakın.  
  
6. İstemci projenin app.config hizmetin bitiş noktası için eşleşen bağlayıcı bilgileri bildirmelidir. Visual Studio'da bunu yapmanın en kolay yolu, app.config dosyasını otomatik olarak güncelleştiren **Hizmet Başvurusu Ekle'yi**kullanmaktır. Alternatif olarak, bu aynı değişiklikler el ile eklenebilir.  
  
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
  
     **Hizmet Başvurusu Ekle'yi**kullanma hakkında daha fazla bilgi için [bkz.](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
7. Artık müşteriden WCF servisini arayabiliriz. Bunu, bu hizmet için bir kanal fabrikası oluşturarak, bir kanal isteyerek ve doğrudan o kanalda istediğimiz yöntemi arayarak yapıyoruz. Bunu yapabiliriz, çünkü kanal hizmetin arabirimini uygular ve bizim için temel istek/yanıt mantığını işler. Bu yöntem çağrısından gelen iade değeri, sunucunun yanıtının deserialized kopyasıdır.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 WCF tarafından sunucudan istemciye döndürülen nesneler her zaman değere göredir. Nesneler, sunucu tarafından gönderilen verilerin seri olarak kopyalanır. İstemci, geri aramayoluyla sunucu kodu çağırma tehlikesi olmadan bu yerel kopyalarda yöntemleri çağırabilir.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Senaryo 2: Sunucu Başvuruya Göre Bir Nesneyi Döndürür  
 Bu senaryo, istemciye başvuru yla bir nesne sağlayan sunucuyu gösterir. .NET Remoting'de bu işlem, başvuru tarafından serihale getirilmiş olan MarshalByRefObject'ten türetilen herhangi bir tür için otomatik olarak işlenir. Bu senaryoya örnek olarak, birden çok istemcinin bağımsız oturumlu sunucu tarafı nesnelerine sahip olmasını sağlamaktır. Daha önce de belirtildiği gibi, bir WCF hizmeti tarafından döndürülen nesneler her zaman değere göredir, bu nedenle başvuru saladeği doğrudan <xref:System.ServiceModel.EndpointAddress10> eşdeğeri yoktur, ancak bir nesne kullanarak başvuru salatiğine benzer bir şey elde etmek mümkündür. Bu, istemci tarafından sunucuda oturum dolu bir by-reference nesnesi elde etmek için kullanılabilecek serileştirilebilir bir yan değer nesnesidir. Bu, bağımsız oturumlu sunucu tarafı nesneleri ile birden çok istemciye sahip olma senaryosunu sağlar.  
  
1. İlk olarak, oturum oluşturan nesnenin kendisine karşılık gelen bir WCF hizmet sözleşmesi tanımlamamız gerekir.  
  
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
    > Oturum oluşturan nesnenin [ServiceContract] ile işaretlendiğini ve bu nedenle normal bir WCF hizmet arabirimi yaptığına dikkat edin. SessionMode özelliğinin ayarlanması, bunun oturum lu bir hizmet olacağını gösterir. WCF'de oturum, iki uç nokta arasında gönderilen birden çok iletiyi ilişkilendirme yoludur. Bu, istemci bu hizmete bağlantı ulaştığında istemci ve sunucu arasında bir oturum oluşturulacağı anlamına gelir. İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafındaki nesnenin tek bir benzersiz örneğini kullanır.  
  
2. Sonra, bu hizmet arabiriminin uygulanmasını sağlamamız gerekir. [ServiceBehavior] ile ifade ederek ve InstanceContextMode ayarlayarak, WCF'ye her oturum için bu türbenzersiz bir örnek kullanmak istediğimizi söyleriz.  
  
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
  
3. Şimdi bu oturumlu nesnenin bir örneğini elde etmek için bir yol gerekir. Bunu, Bir EndpointAddress10 nesnesi döndüren başka bir WCF hizmet arabirimi oluşturarak yapıyoruz. Bu, istemcinin oturum oluşturabilecek nesneyi oluşturmak için kullanabileceği bir bitiş noktasının serileştirilebilir biçimidir.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     Ve bu WCF hizmetini uyguluyoruz:  
  
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
  
     Bu uygulama, oturumlu nesneler oluşturmak için bir singleton kanal fabrika tutar. GetInstanceAddress() çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adresi etkili bir şekilde işaret eden bir EndpointAddress10 nesnesi oluşturur. EndpointAddress10 yalnızca istemciye göre döndürülebilen bir veri türüdür.  
  
4. Aşağıdaki örnekte gösterildiği gibi aşağıdaki iki şeyi yaparak sunucunun yapılandırma dosyasını değiştirmemiz gerekir:  
  
    1. Oturum \<açan nesnenin bitiş noktasını açıklayan bir istemci> bölümü bildirin. Sunucu da bu durumda bir istemci olarak hareket eder, çünkü bu gereklidir.  
  
    2. Fabrika ve oturum alagelen nesne için uç noktalarını bildirin. Bu, istemcinin EndpointAddress10'u elde etmek ve oturum lu kanalı oluşturmak için hizmet bitiş noktalarıyla iletişim kurmasına izin vermek için gereklidir.  
  
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
  
     Ve sonra şu hizmetleri başlatabiliriz:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. İstemciyi, projesinin app.config dosyasında aynı uç noktaları beyan ederek yapılandırıyoruz.  
  
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
  
6. Bu oturumlu nesneyi oluşturmak ve kullanmak için istemci aşağıdaki adımları yapmalıdır:  
  
    1. ISessionBoundFactory hizmetiiçin bir kanal oluşturun.  
  
    2. Bir EndpointAddress10 almak için bu hizmeti çağırmak için bu kanalı kullanın.  
  
    3. Oturum lu bir nesne elde etmek için bir kanal oluşturmak için EndpointAddress10'u kullanın.  
  
    4. Birden çok aramada aynı örnek olarak kaldığını göstermek için oturuma uygun nesneyle etkileşimkurun.  
  
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
  
 WCF nesneleri her zaman değere göre döndürür, ancak EndpointAddress10'u kullanarak referans semantik eşdeğerini desteklemek mümkündür. Bu, istemcinin oturum lu bir WCF hizmeti örneği istemesine izin verir ve bundan sonra diğer WCF hizmetleri gibi onunla etkileşimkurabilir.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Senaryo 3: İstemci Sunucuya Bir By-Value Örneği Gönderir  
 Bu senaryo, istemcinin sunucuya değer bazında ilkel olmayan bir nesne örneği gönderdiğini gösterir. WCF nesneleri yalnızca değere göre gönderdiğinden, bu senaryo normal WCF kullanımını gösterir.  
  
1. Senaryo 1'deki aynı WCF Hizmetini kullanın.  
  
2. İstemciyi yeni bir yan değer nesnesi (Müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesneyi ona göndermek için kullanın.  
  
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
  
     Müşteri nesnesi seri hale getirilecek ve sunucuya gönderilir ve bu nesnenin yeni bir kopyasına dönüştürülür.  
  
    > [!NOTE]
    > Bu kod, türetilmiş bir tür (PremiumCustomer) göndermeyi de gösterir. Hizmet arabirimi bir Müşteri nesnesi bekler, ancak Müşteri sınıfındaki [KnownType] özniteliği premiumcustomer'a da izin verildiğini belirtir. WCF, bu hizmet arabirimi aracılığıyla başka bir türü serihale veya deserialize etme girişimlerini başarısız alacaktır.  
  
 Normal WCF veri değişimleri değere göredir. Bu, bu veri nesnelerinden birine çağrı yöntemlerinin yalnızca yerel olarak yürütüleceğini garanti eder – diğer katmanda kod çağırmaz. Sunucudan döndürülen by-reference nesneleri gibi *from* bir şey elde etmek mümkün olsa da, istemcinin bir ara başvuru nesnesini *sunucuya* geçirmesi mümkün değildir. İstemci ve sunucu arasında ileri geri görüşme gerektiren bir senaryo, çift yönlü bir hizmet kullanılarak WCF'de elde edilebilir. Daha fazla bilgi için [Çift Yönlü Hizmetler'e](./feature-details/duplex-services.md)bakın.  
  
## <a name="summary"></a>Özet  
 .NET Remoting, yalnızca tam güvenilen ortamlarda kullanılmak üzere tasarlanmış bir iletişim çerçevesidir. Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir. Yeni uygulamalar oluşturmak için kullanılmamalıdır. Tam tersine, WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir. Microsoft, varolan Remoting uygulamalarının WCF veya ASP.NET Web API'sını kullanmak üzere geçirilmelerini önerir.
