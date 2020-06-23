---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
description: WCF kullanmak için .NET Remoting kullanan bir uygulamayı geçirmeyi öğrenin. WCF 'de birkaç genel uzaktan iletişim senaryosu gerçekleştirebilirsiniz.
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: f6f526db09806008314980b71233b208d25359fc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246161"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>.NET Uzaktan İletişimden WCF'ye Taşınma
Bu makalede, .NET Remoting kullanan bir uygulamanın Windows Communication Foundation (WCF) kullanmak üzere nasıl geçirileceği açıklanır. Bu ürünler arasındaki benzer kavramları karşılaştırır ve daha sonra WCF 'de birkaç genel uzaktan Iletişim senaryosu gerçekleştirmeyi açıklar.  
  
 .NET uzaktan Iletişim yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür. İstemci ve sunucu arasında ayrı güven düzeylerini koruyamadığından, karma güven ortamlarında güvenli değildir. Örneğin, hiç bir .NET Remoting uç noktasını Internet 'e veya güvenilmeyen istemcilere sunmamanız gerekir. Mevcut uzaktan Iletişim uygulamalarının daha yeni ve daha güvenli teknolojilere geçirilmesi önerilir. Uygulamanın tasarımı yalnızca HTTP kullanıyorsa ve yeniden karşılaşırsanız, ASP.NET Web API 'SI önerilir. Daha fazla bilgi için bkz. ASP.NET Web API. Uygulama SOAP 'yi temel alıyorsa veya TCP gibi http olmayan protokoller gerektiriyorsa, WCF önerilir.  

## <a name="comparing-net-remoting-to-wcf"></a>.NET uzaktan iletişimini WCF ile karşılaştırma  
 Bu bölüm, .NET uzaktan Iletişim uygulamasının temel yapı taşlarını WCF eşdeğerlerine göre karşılaştırır. Bu yapı taşlarını daha sonra WCF 'de bazı yaygın istemci-sunucu senaryoları oluşturmak için kullanacağız. Aşağıdaki grafik, .NET uzaktan Iletişim ve WCF arasındaki önemli benzerlikleri ve farklılıkları özetler.  
  
||.NET uzaktan iletişim|WCF|  
|-|-------------------|---------|  
|Sunucu türü|Alt sınıf MarshalByRefObject|[ServiceContract] özniteliğiyle işaretle|  
|Hizmet işlemleri|Sunucu türündeki ortak Yöntemler|[OperationContract] özniteliğiyle işaretle|  
|Serileştirme|ISerializable veya [Serializable]|DataContractSerializer veya XmlSerializer|  
|Geçirilen nesneler|Değere göre veya başvuruya göre|Yalnızca değere göre|  
|Hatalar/özel durumlar|Herhangi bir serileştirilebilir özel durum|FaultContract\<TDetail>|  
|İstemci proxy nesneleri|Kesin olarak yazılan saydam proxy 'ler bulunan MarshalByRefObjects adresinden otomatik olarak oluşturulur|Kesin olarak belirlenmiş proxy 'ler, ChannelFactory kullanılarak isteğe bağlı olarak oluşturulur\<TChannel>|  
|Platform gerekli|Hem istemci hem de sunucu Microsoft OS ve .NET kullanmalıdır|Platformlar arası|  
|İleti biçimi|Özel|Sektör standartları (SOAP, WS-*, vb.)|  
  
### <a name="server-implementation-comparison"></a>Sunucu uygulama karşılaştırması  
  
#### <a name="creating-a-server-in-net-remoting"></a>.NET uzaktan Iletişim kutusunda sunucu oluşturma  
 .NET uzaktan Iletişim sunucusu türleri MarshalByRefObject 'den türetilmelidir ve istemcinin çağırabilmesine ve aşağıdaki gibi arama yöntemlerini tanımlamalıdır:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu sunucu türünün genel yöntemleri, istemcilerin kullanabildiği ortak sözleşme olur.  Sunucunun ortak arabirimi ve onun uygulamasıyla arasında ayrım yoktur, her ikisini de bir tür işler.  
  
 Sunucu türü tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi istemciler için kullanılabilir hale getirilebilir:  
  
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
  
 Yapılandırma dosyalarını kullanma dahil, uzaktan Iletişim türünü sunucu olarak kullanılabilir hale getirmek için birçok yol vardır. Bu yalnızca bir örnektir.  
  
#### <a name="creating-a-server-in-wcf"></a>WCF 'de sunucu oluşturma  
 WCF 'deki eşdeğer adım iki tür oluşturmayı içerir--genel "hizmet sözleşmesi" ve somut uygulama. İlki [ServiceContract] ile işaretlenmiş bir arabirim olarak bildirilmiştir. İstemciler için kullanılabilir yöntemler [OperationContract] ile işaretlenir:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucunun uygulanması, aşağıdaki örnekte olduğu gibi ayrı bir somut sınıfta tanımlanmıştır:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Bu türler tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi WCF sunucusu istemciler için kullanılabilir hale getirilebilir:  
  
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
> TCP her iki örnekte de, mümkün olduğunca benzer şekilde devam etmek için kullanılır. HTTP kullanan örnekler için bu konunun ilerleyen kısımlarında yer alarak izlenecek yol-kılavuzlarına bölümüne bakın.  
  
 WCF hizmetlerini yapılandırmak ve barındırmak için birçok yol vardır. Bu, "kendiliğinden konak" olarak bilinen tek bir örnektir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](how-to-define-a-wcf-service-contract.md)  
  
- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)  
  
- [Barındırma Hizmetleri](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>İstemci uygulama karşılaştırması  
  
#### <a name="creating-a-client-in-net-remoting"></a>.NET Remoting 'te Istemci oluşturma  
 .NET uzaktan Iletişim sunucusu nesnesi kullanılabilir duruma getirildikten sonra, aşağıdaki örnekte olduğu gibi istemciler tarafından tüketilebilir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Etkinleştirici. GetObject () öğesinden döndürülen RemotingServer örneği "saydam proxy" olarak bilinir. İstemcideki RemotingServer türü için ortak API 'yi uygular, ancak tüm yöntemler farklı bir işlemde veya makinede çalışan sunucu nesnesini çağırır.  
  
#### <a name="creating-a-client-in-wcf"></a>WCF 'de Istemci oluşturma  
 WCF 'deki eşdeğer adım, ara sunucuyu açıkça oluşturmak için bir kanal fabrikası kullanmayı içerir. Uzaktan Iletişim gibi, proxy nesnesi, aşağıdaki örnekte olduğu gibi, sunucu üzerindeki işlemleri çağırmak için kullanılabilir:  
  
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
  
 Bu örnek, en çok uzaktan Iletişim örneğine benzer olduğundan, kanal düzeyinde programlama gösterir. Ayrıca, Visual Studio 'da istemci programlamayı basitleştirecek kod üreten **hizmet başvurusu Ekle** yaklaşımı de mevcuttur. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [İstemci Kanal Düzeyi Programlama](./extending/client-channel-level-programming.md)  
  
- [Nasıl yapılır: hizmet başvurusu ekleme, güncelleştirme veya kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Serileştirme kullanımı  
 Hem .NET Remoting hem de WCF, nesneleri istemci ile sunucu arasında göndermek için serileştirme kullanır, ancak bu önemli yollarla farklılık gösterir:  
  
1. Bunlar, serileştirildiklerinizi göstermek için farklı serileştiriciler ve kurallar kullanır.  
  
2. .NET uzaktan Iletişim, bir katmanda Yöntem veya özellik erişiminin, güvenlik sınırları genelinde olan diğer katmanda kod yürütmesine olanak tanıyan "başvuruya göre" serileştirmesini destekler. Bu özellik güvenlik açıklarını açığa çıkarır ve uzaktan Iletişim uç noktalarının güvenilmeyen istemcilere hiçbir şekilde gösterilmemesi için önemli nedenlerden biridir.  
  
3. Uzaktan Iletişim tarafından kullanılan serileştirme geri çevrildi (serileştirilmeyen öğeleri açıkça hariç bırakır) ve WCF serileştirme kabul etme (hangi üyelerin serileştirilmek için açıkça işaretlenmesi).  
  
#### <a name="serialization-in-net-remoting"></a>.NET Remoting 'de serileştirme  
 .NET uzaktan Iletişim, istemci ve sunucu arasında nesneleri serileştirmek ve seri durumdan çıkarmak için iki yolu destekler:  
  
- *Değere göre* – nesnenin değerleri katman sınırları genelinde serileştirilir ve diğer katmanda bu nesnenin yeni bir örneği oluşturulur. Bu yeni örneğin yöntemlere veya özelliklerine yapılan çağrılar yalnızca yerel olarak yürütülür ve özgün nesneyi veya katmanı etkilemez.  
  
- *Başvuruya göre* – özel bir "nesne başvurusu" katman sınırları genelinde serileştirilir. Bir katman bu nesnenin yöntemleriyle veya özellikleriyle etkileşime geçtiğinde, özgün katmandaki özgün nesneye geri iletişim kurar. Başvuruya göre nesneler, istemci veya istemciden sunucuya kadar her iki yönde de akabilir.  
  
 Remoting 'teki değer tabanlı türler, [Serializable] özniteliğiyle işaretlenir veya aşağıdaki örnekte olduğu gibi ISerializable uygular:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Başvuruya göre türler, aşağıdaki örnekte olduğu gibi MarshalByRefObject sınıfından türetilir:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Uzaktan Iletişimin başvuru nesnelerinin etkilerini anlamak son derece önemlidir. Herhangi bir katman (istemci veya sunucu) diğer katmana başvuruya göre bir nesne gönderiyorsa, tüm yöntem, nesnenin sahip olduğu katmanda yürütülür. Örneğin, sunucu tarafından döndürülen bir başvuruya göre nesne üzerinde Yöntemler çağıran bir istemci, sunucuda kod yürütür. Benzer şekilde, istemci tarafından sağlanmış bir başvuru nesnesi üzerinde Yöntemler çağıran bir sunucu, kodu istemciye geri yürütür. Bu nedenle, .NET Remoting kullanımı yalnızca tam olarak güvenilen ortamlarda önerilir. Güvenli bir .NET Remoting uç noktasının güvenilir olmayan istemcilere açık olması, uzaktan Iletişim sunucusu saldırılara karşı savunmasız hale getirir.  
  
#### <a name="serialization-in-wcf"></a>WCF 'de serileştirme  
 WCF yalnızca değere göre serileştirme destekler. İstemci ve sunucu arasında Exchange için bir tür tanımlamanın en yaygın yolu aşağıdaki örnekte gibidir:  
  
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
  
 [DataContract] özniteliği bu türü, istemci ile sunucu arasında seri hale getirileve seri durumdan çıkarılacak bir şekilde tanımlar. [DataMember] özniteliği, serileştirme için tek tek özellikleri veya alanları tanımlar.  
  
 WCF, katmanlar arasında bir nesne gönderdiğinde, yalnızca değerleri seri hale getirir ve diğer katmanda nesnenin yeni bir örneğini oluşturur. Nesne değerleri yalnızca yerel olarak oluşur; diğer katmanla aynı şekilde .NET Remoting ile başvuru nesneleriyle iletişim kurmazlar. Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Özel durum Işleme özellikleri  
  
#### <a name="exceptions-in-net-remoting"></a>.NET Remoting 'teki özel durumlar  
 Bir uzak sunucu tarafından oluşturulan özel durumlar serileştirilir, istemciye gönderilir ve başka bir özel durum gibi istemcide yerel olarak oluşturulur. Özel özel durumlar, özel durum türünü alt sınıflama tarafından, [Serializable] ile işaretleyerek oluşturulabilir.   Çoğu Framework özel durumu zaten bu şekilde işaretlenir, bu sayede sunucuda sunucu tarafından oluşturulması, serileştirilmesi ve yeniden oluşturulması sağlanır. Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri istenmeden istemciye daha da açıklanamaz. Bu, uzaktan Iletişimin yalnızca tam güvenilir ortamlarda kullanılması gereken pek çok nedenden biridir.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>WCF 'de özel durumlar ve hatalar  
 WCF, yanlışlıkla bilginin açığa çıkmasına yol açacağından sunucudan istemciye rastgele özel durum türleri döndürülmesine izin vermez. Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, istemci üzerinde genel amaçlı bir FaultException oluşturulmasına neden olur. Bu özel durum, sorunun neden veya nerede oluştuğunu ve bazı uygulamalar için yeterli bilgi taşımaz. İstemciye daha zengin hata bilgilerini iletmeniz gereken uygulamalar, bir hata sözleşmesini tanımlayarak bunu yapın.  
  
 Bunu yapmak için ilk olarak hata bilgilerini taşıyan bir [DataContract] türü oluşturun.  
  
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
  
 Her bir hizmet işlemi için kullanılacak hata sözleşmesini belirtin.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucu, bir FaultException oluşturarak hata koşullarını raporlar.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 İstemci sunucuya bir istek yaptığında hataları normal özel durumlar olarak yakalayabilir.  
  
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
  
 Hata sözleşmeleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.FaultException> ..  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
  
#### <a name="security-in-net-remoting"></a>.NET Remoting 'de güvenlik  
 Bazı .NET uzaktan Iletişim kanalları, kanal katmanında (IPC ve TCP) kimlik doğrulaması ve şifreleme gibi güvenlik özelliklerini destekler. HTTP kanalı, kimlik doğrulaması ve şifreleme için Internet Information Services (IIS) kullanır. Bu desteğe rağmen, .NET Remoting güvenli olmayan bir iletişim protokolünü güvenilir hale getirmek ve yalnızca tam güvenilir ortamlarda kullanmanız gerekir. Internet veya güvenilmeyen istemcilere genel bir uzaktan Iletişim uç noktası sunmaz.  
  
#### <a name="security-in-wcf"></a>WCF'de Güvenlik  
 WCF, .NET uzaktan Iletişim kutusunda bulunan güvenlik açıklarına yönelik güvenlik açıklarını ele almak için göz önünde bulundurularak tasarlanmıştır. WCF hem aktarım hem de ileti düzeyinde güvenlik sağlar ve kimlik doğrulama, yetkilendirme, şifreleme gibi birçok seçenek sunar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Güvenlik](./feature-details/security.md)  
  
- [WCF güvenlik kılavuzu](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>WCF 'ye geçiş  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Neden uzaktan Iletişim 'ten WCF 'ye geçirilir?  
  
- **.NET uzaktan Iletişim, eski bir üründür.** [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)' de açıklandığı gibi, eski bir ürün olarak kabul edilir ve yeni geliştirme için önerilmez. WCF veya ASP.NET Web API 'SI, yeni ve mevcut uygulamalar için önerilir.  
  
- **WCF platformlar arası standartları kullanır.** WCF, platformlar arası birlikte çalışabilirlik ile tasarlanmıştı ve birçok sektör standardını (SOAP, WS-Security, WS-Trust, vb.) destekler. Bir WCF hizmeti, Windows dışındaki işletim sistemlerinde çalışan istemcilerle birlikte çalışabilir. Uzaktan iletişim, birincil olarak hem sunucu hem de istemci uygulamaların bir Windows işletim sisteminde .NET Framework kullanarak çalıştığı ortamlar için tasarlanmıştır.
  
- **WCF yerleşik güvenliğe sahiptir.** WCF güvenlik göz önünde bulundurularak tasarlandı ve kimlik doğrulama, aktarım düzeyi güvenliği, ileti düzeyi güvenlik vb. için birçok seçenek sunar. Uzaktan iletişim, uygulamaların birlikte çalışabilmesini ve güvenilir olmayan ortamlarda güvenli hale getirmek üzere tasarlanmadığı için tasarlanmıştır. WCF hem güvenilen hem de güvenilmeyen ortamlarda çalışacak şekilde tasarlanmıştır.  
  
### <a name="migration-recommendations"></a>Geçiş önerileri  
 .NET uzaktan Iletişim 'dan WCF 'ye geçiş için önerilen adımlar aşağıda verilmiştir:  
  
- **Hizmet sözleşmesini oluşturun.** Hizmet arabirimi türlerinizi tanımlayın ve bunları [ServiceContract] özniteliğiyle işaretleyin. İstemcilerin [OperationContract] ile çağrı yapmasına izin verilecek tüm yöntemleri işaretleyin.  
  
- **Veri sözleşmesini oluşturun.** Sunucu ve istemci arasında değiş tokuş edilecek veri türlerini tanımlayın ve bunları [DataContract] özniteliğiyle işaretleyin. İstemcinin [DataMember] ile kullanmasına izin verilecek tüm alanları ve özellikleri işaretleyin.  
  
- **Hata sözleşmesini oluşturun (isteğe bağlı).** Hatalarla karşılaşıldığında sunucu ile istemci arasında değiş tokuş edilecek türleri oluşturun. Bu türleri seri hale getirilebilir hale getirmek için [DataContract] ve [DataMember] ile işaretleyin. [OperationContract] ile işaretlediğiniz tüm hizmet işlemleri için, hangi hataların dönebileceği göstermek için bunları [FaultContract] ile de işaretleyebilirsiniz.  
  
- **Hizmeti yapılandırın ve barındırın.** Hizmet sözleşmesi oluşturulduktan sonra, bir sonraki adım, hizmeti bir uç noktada kullanıma sunmak için bir bağlama yapılandırmaktır. Daha fazla bilgi için bkz. [uç noktalar: adresler, bağlamalar ve sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Uzaktan Iletişim uygulaması WCF 'ye geçirildiğinde, .NET uzaktan Iletişim üzerinde bağımlılıkları kaldırmak yine de önemlidir. Bu, tüm uzaktan Iletişim açıklarının uygulamadan kaldırılmasını sağlar. Bu adımlar şunları içerir:  
  
- **MarshalByRefObject kullanımını durdur.** MarshalByRefObject türü yalnızca uzaktan Iletişim için bulunur ve WCF tarafından kullanılmaz. Alt sınıf MarshalByRefObject olan herhangi bir uygulama türü kaldırılmalı veya değiştirilmelidir.  
  
- **[Serializable] ve ISerializable kullanımını durdur.** [Serializable] özniteliği ve ISerializable arabirimi, başlangıçta güvenilen ortamlarda türleri seri hale getirmek için tasarlanmıştır ve uzaktan Iletişim tarafından kullanılır. WCF serileştirme, [DataContract] ve [DataMember] ile işaretlenmiş türlere dayanır. Bir uygulama tarafından kullanılan veri türleri ISerializable veya [Serializable] kullanmak için değil [DataContract] kullanacak şekilde değiştirilmelidir.  
  
### <a name="migration-scenarios"></a>Geçiş senaryoları  
 Şimdi, WCF 'de aşağıdaki genel uzaktan Iletişim senaryolarını nasıl gerçekleştireceğinizi görelim:  
  
1. Sunucu istemciye bir nesne değeri döndürür  
  
2. Sunucu, istemciye başvuruya göre bir nesne döndürür  
  
3. İstemci sunucuya bir nesne değere göre gönderir  
  
> [!NOTE]
> İstemciden sunucuya bir nesne başvuruya göre göndermeye, WCF 'de izin verilmez.  
  
 Bu senaryolarla okurken, .NET uzaktan Iletişim için temel arabirimlerimizin aşağıdaki örnekteki gibi göründüğünü varsayın. Yalnızca WCF 'nin eşdeğer işlevselliği uygulamak için nasıl kullanılacağını göstermek istediğimizden, .NET Remoting uygulaması burada önemli değildir.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Senaryo 1: hizmet bir nesne değere göre döndürüyor  
 Bu senaryoda istemciye değerine göre bir nesne döndüren bir sunucu gösterilir. WCF her zaman sunucudan değere göre nesneleri döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmetinin nasıl oluşturulacağını açıklamaktadır.  
  
1. WCF hizmeti için bir ortak arabirim tanımlayarak başlayın ve [ServiceContract] özniteliğiyle işaretleyin. İstemcimizin çağıracağız sunucu tarafı yöntemleri belirlemek için [OperationContract] kullanıyoruz.  
  
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
  
2. Bir sonraki adım, bu hizmet için veri sözleşmesinin oluşturmaktır. Bunu, [DataContract] özniteliğiyle işaretlenmiş sınıflar (arabirimler değil) oluşturarak yapacağız. Hem istemci hem de sunucu için görünür olmasını istediğimiz her bir özellik veya alan [DataMember] ile işaretlenmiş. Türetilmiş türlerin izin verilmesini istiyoruz, bunları tanımlamak için [KnownType] özniteliğini kullanmanız gerekir. WCF, bu hizmet için yalnızca seri hale getirilebilir veya seri durumdan çıkarılan türler hizmet arabirimindeki ve bu "bilinen türler" olur. Bu listede olmayan başka bir türü alışverişi yapılmaya çalışılması reddedilir.  
  
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
  
3. Ardından, hizmet arabirimi için uygulama sağlıyoruz.  
  
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
  
4. WCF hizmetini çalıştırmak için belirli bir WCF bağlamasını kullanarak bu hizmet arabirimini belirli bir URL 'de kullanıma sunan bir uç nokta bildirmemiz gerekir. Bu, genellikle aşağıdaki bölümler sunucu projesinin web.config dosyasına eklenerek yapılır.  
  
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
  
     Bu ServiceHost başlatıldığında, uygun sözleşmeyi, bağlamayı ve uç noktayı kurmak için web.config dosyasını kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak hizmetleri yapılandırma](./configuring-services-using-configuration-files.md). Sunucunun başlatılmasına yönelik bu stil, kendi kendine barındırma olarak bilinir. WCF hizmetlerini barındırmak için diğer seçimler hakkında daha fazla bilgi edinmek için bkz. [barındırma hizmetleri](./hosting-services.md).  
  
6. İstemci projesinin app.config, hizmetin uç noktası için eşleşen bağlama bilgilerini bildirmelidir. Visual Studio 'da bunu yapmanın en kolay yolu, app.config dosyayı otomatik olarak güncelleştirecek **hizmet başvurusu Ekle**kullanmaktır. Alternatif olarak, aynı değişiklikler el ile de eklenebilir.  
  
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
  
     **Hizmet başvurusu Ekle**kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet başvurusu ekleme, güncelleştirme veya kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Artık WCF hizmetini istemciden çağırabiliriz. Bu, söz konusu hizmet için bir kanal fabrikası oluşturup bunu bir kanal için sorarak ve bu kanalda istediğiniz yöntemi doğrudan çağırarak yaptık. Kanal hizmetin arabirimini gerçekleştirdiğinden ve temel alınan istek/yanıt mantığını bizim için işletiğinden bunu yapabiliriz. Bu yöntem çağrısından gelen dönüş değeri, sunucu yanıtının Serisi kaldırılan kopyasıdır.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Sunucudan istemciye WCF tarafından döndürülen nesneler her zaman değere göre yapılır. Nesneler, sunucu tarafından gönderilen verilerin seri durumdan çıkarılmakta. İstemci, geri çağırmalar aracılığıyla sunucu kodu çağırma tehlikiyeti olmadan bu yerel kopyalara Yöntemler çağırabilir.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Senaryo 2: sunucu başvuruya göre bir nesne döndürüyor  
 Bu senaryoda, istemciye başvuruya göre bir nesne sağlayan sunucu gösterilmektedir. .NET uzaktan Iletişim kutusunda, bu, başvuruya göre seri hale getirilen MarshalByRefObject öğesinden türetilen herhangi bir tür için otomatik olarak işlenir. Bu senaryonun bir örneği, birden çok istemcinin bağımsız oturumlı sunucu tarafı nesnelerine sahip olmasını sağlar. Daha önce belirtildiği gibi, bir WCF hizmeti tarafından döndürülen nesneler her zaman değere göre yapılır, bu nedenle bir başvuruya göre nesnenin doğrudan eşdeğeri olmaz, ancak bir nesne kullanarak başvuru semantiğine benzer bir şey elde etmek mümkündür <xref:System.ServiceModel.EndpointAddress10> . Bu, istemci tarafından sunucuda bir sessionby başvuruya göre nesne almak için kullanılabilen, seri hale getirilebilir bir nesne nesnesidir. Bu, bağımsız oturumlarla aynı sunucu tarafı nesneleriyle birden çok istemcisine sahip olan senaryoya izin vermez.  
  
1. İlk olarak, sessionobject nesnesine karşılık gelen bir WCF hizmeti sözleşmesi tanımlamamız gerekir.  
  
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
    > Oturumsuz nesnenin [ServiceContract] ile işaretlendiğine dikkat edin. Bu, normal bir WCF hizmeti arabirimi haline gelir. SessionMode özelliği ayarlandığında, bu bir sessionservice olacağını gösterir. WCF 'de oturum, iki uç nokta arasında gönderilen birden fazla iletiyi eş bir şekilde ilişkilendirme yöntemidir. Bu, bir istemci bu hizmete bir bağlantı edinirse, istemci ile sunucu arasında bir oturum kurulacağı anlamına gelir. İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafı nesnesinin tek bir benzersiz örneğini kullanır.  
  
2. Daha sonra, bu hizmet arabiriminin uygulamasını sağlamamız gerekir. Bunu [ServiceBehavior] ile belirterek ve InstanceContextMode 'i ayarlayarak, her oturum için bu türün benzersiz bir örneğini kullanmak istediğimizi anladık.  
  
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
  
3. Şimdi bu oturumsuz nesnenin bir örneğini elde etmek için bir yol gerekiyor. Bunu, bir EndpointAddress10 nesnesi döndüren başka bir WCF hizmeti arabirimi oluşturarak yapacağız. Bu, istemcinin oturumsuz nesneyi oluşturmak için kullanabileceği bir uç noktanın seri hale getirilebilir bir biçimidir.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     Bu WCF hizmetini uyguladık:  
  
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
  
     Bu uygulama, oturumsuz nesneler oluşturmak için tek bir kanal fabrikası sağlar. GetInstanceAddress () çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adresi etkin bir şekilde işaret eden bir EndpointAddress10 nesnesi oluşturur. EndpointAddress10 yalnızca istemciye değere göre döndürülebilecek bir veri türüdür.  
  
4. Aşağıdaki örnekte gösterildiği gibi aşağıdaki iki şeyi yaparak sunucunun yapılandırma dosyasını değiştirmemiz gerekir:  
  
    1. \<client>Oturumsuz nesnenin bitiş noktasını açıklayan bir bölüm bildirin. Bu durum, sunucu aynı zamanda bir istemci görevi görtiğinden gereklidir.  
  
    2. Fabrika ve oturumsuz nesne için uç noktalar bildirin. Bu, istemcinin EndpointAddress10 almak ve Oturumsuz kanalı oluşturmak için hizmet uç noktalarıyla iletişim kurmasına izin vermek için gereklidir.  
  
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
  
     Bu hizmetleri başlatabiliriz:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. İstemcisini, projenin app.config dosyasında aynı uç noktaları bildirerek yapılandıracağız.  
  
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
  
6. Bu oturumsuz nesneyi oluşturmak ve kullanmak için, istemcinin aşağıdaki adımları yapması gerekir:  
  
    1. ISessionBoundFactory hizmetine bir kanal oluşturun.  
  
    2. Bu kanalı, bir EndpointAddress10 almak için bu hizmeti çağırmak üzere kullanın.  
  
    3. Oturumsuz bir nesne almak için bir kanal oluşturmak için EndpointAddress10 kullanın.  
  
    4. Birden çok çağrıda aynı örnekle kaldığını göstermek için sessionobject nesnesiyle etkileşime geçin.  
  
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
  
 WCF her zaman nesneleri değere göre döndürür, ancak EndpointAddress10 kullanımı aracılığıyla başvuru semantiğinin eşdeğerini desteklemek mümkündür. Bu, istemcinin, diğer herhangi bir WCF hizmeti gibi etkileşime girebileceği bir sessionwcf hizmeti örneği istemesine izin verir.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Senaryo 3: Istemci sunucu a-değer örneği gönderir  
 Bu senaryoda, temel olmayan bir nesne örneğini sunucuya göre sunucusuna gönderen istemci gösterilmektedir. WCF yalnızca değere göre nesneler gönderdiğinden, bu senaryo normal WCF kullanımını gösterir.  
  
1. Senaryo 1 ' de aynı WCF hizmetini kullanın.  
  
2. Yeni bir değere göre nesne oluşturmak için istemcisini kullanın, ıcustomerservice hizmetiyle iletişim kurmak için bir kanal oluşturun ve nesneyi buna gönderin.  
  
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
  
     Müşteri nesnesi serileştirilir ve sunucuya gönderilir ve bu nesnenin yeni bir kopyasına seri hale gelir.  
  
    > [!NOTE]
    > Bu kod ayrıca, türetilmiş bir tür göndermeyi de gösterir (PremiumCustomer). Hizmet arabirimi bir müşteri nesnesi bekliyor, ancak Customer sınıfında [KnownType] özniteliğine de PremiumCustomer de izin verildi. WCF, bu hizmet arabirimi aracılığıyla başka herhangi bir türü serileştirme veya serisini kaldırma girişiminde bulunamaz.  
  
 Normal WCF verileri alışverişi değere göre yapılır. Bu, bu veri nesnelerinden birindeki yöntemlerin çağrılması için yalnızca yerel olarak yürütülür; diğer katmanda kod çağırmaz. *Sunucudan döndürülen başvuru* nesneleri gibi bir şeye ulaşmak mümkün olsa da, bir istemcinin sunucuya başvuruya göre *bir nesne geçirmesi* mümkün değildir. Bir çift yönlü hizmet kullanılarak, istemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo WCF 'de elde edilebilir. Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Özet  
 .NET Remoting, yalnızca tam olarak güvenilen ortamlarda kullanılması amaçlanan bir iletişim çerçevesidir. Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir. Yeni uygulamalar oluşturmak için kullanılmamalıdır. Buna karşılık, WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir. Microsoft, mevcut uzaktan Iletişim uygulamalarının WCF veya ASP.NET Web API 'SI kullanacak şekilde geçirilmesini önerir.
