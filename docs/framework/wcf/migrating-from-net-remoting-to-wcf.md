---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b387e100ff881c5394b6a77716a733b3928eae9
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-from-net-remoting-to-wcf"></a>.NET Uzaktan İletişimden WCF'ye Taşınma
Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET uzaktan iletişim kullanan bir uygulamayı geçirmek üzere açıklar. Bu ürünler arasında benzer kavram karşılaştırır ve WCF birkaç ortak Remoting senaryolarda yüklemenin nasıl yapılacağını açıklar.  
  
 .NET uzaktan iletişim yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür. İstemci ve sunucu arasındaki ayrı güven düzeyleri korunamaz olduğundan karma güven ortamlar genelinde güvenli değil. Örneğin, bir .NET uzaktan iletişim uç noktası Internet veya güvenilmeyen istemciler için hiçbir zaman maruz bırakmamalısınız. Varolan Remoting öneririz uygulamalar için daha yeni ve daha güvenli teknolojiler geçirilmiş. Uygulamanın tasarım yalnızca HTTP kullanır ve RESTful ise, ASP.NET Web API öneririz. Daha fazla bilgi için bkz: ASP.NET Web API. Uygulama üzerinde SOAP tabanlı veya Http olmayan protokolleri TCP gibi gerekiyorsa, WCF öneririz.  

## <a name="comparing-net-remoting-to-wcf"></a>.NET uzaktan iletişim için WCF karşılaştırma  
 Bu bölümde, .NET uzaktan iletişim temel yapı taşlarının WCF eşdeğerlerine ile karşılaştırır. Bu yapı taşları daha sonra bazı genel istemci-sunucu senaryolar WCF'de oluşturmak için kullanacağız. Aşağıdaki grafikte ana benzerlikler ve .NET uzaktan iletişim ve WCF arasındaki farklar özetlenmektedir.  
  
||.NET uzaktan iletişim|WCF|  
|-|-------------------|---------|  
|Sunucu türü|Subclass MarshalByRefObject|[ServiceContract] özniteliği ile işaretleme|  
|Hizmet işlemleri|Sunucu türü üzerinde genel yöntemler|[OperationContract] özniteliği ile işaretleme|  
|Serileştirme|ISerializable veya [Serializable]|DataContractSerializer or XmlSerializer|  
|Geçirilen nesneleri|Değer tarafından veya başvuru tarafından|Tarafından yalnızca değeri|  
|Hataları/özel durumlar|Seri hale getirilebilir özel durumları|FaultContract\<TDetail >|  
|İstemci proxy nesneleri|Kesin türü belirtilmiş saydam proxy'leri bulunan MarshalByRefObjects için otomatik olarak oluşturulur|Kesin türü belirtilmiş proxy'leri üretilen isteğe bağlı ChannelFactory kullanma\<TChannel >|  
|Gereken platformu|İstemci ve sunucu Microsoft OS ve .NET kullanmanız gerekir|Platformlar arası|  
|İleti biçimi|Özel|Endüstri standartları (SOAP, WS-*, vb..)|  
  
### <a name="server-implementation-comparison"></a>Sunucu uygulaması karşılaştırma  
  
#### <a name="creating-a-server-in-net-remoting"></a>.NET uzaktan iletişim bir sunucu oluşturma  
 .NET uzaktan iletişim sunucu türleri, MarshalByRefObject öğesinden türetilen ve istemci, aşağıdaki gibi çağırabilirsiniz yöntemleri tanımlayın:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Genel yöntemler bu sunucu türü ortak sözleşme istemciler için kullanılabilir olur.  Sunucunun ortak arabirimi ile uygulaması arasında hiçbir ayrım – bir türü hem de işler.  
  
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
  
 Uzaktan iletişim türünü yapılandırma dosyalarını kullanma da dahil, bir sunucu olarak kullanılabilir hale getirmek için birçok yolu vardır. Bu yalnızca bir örnektir.  
  
#### <a name="creating-a-server-in-wcf"></a>WCF'de bir sunucu oluşturma  
 WCF eşdeğer adımda iki tür--genel "hizmet sözleşmesi" ve somut uygulaması oluşturursunuz. İlk [ServiceContract] ile işaretli bir arabirim olarak bildirilir. İstemciler için kullanılabilir yöntemleri [OperationContract] ile işaretli:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Sunucu uygulaması aşağıdaki örnekte gibi ayrı somut sınıfında tanımlanır:  
  
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
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP örneklerin her ikisi de mümkün olduğu kadar benzer tutmak için kullanılır. HTTP kullanan örnekler için bu konunun ilerleyen bölümlerinde senaryo kılavuzlarına başvurun.  
  
 Yapılandırmak için birçok yolu vardır ve WCF hizmetlerini barındırmak için. Bu "kendi kendini barındıran" bilinen yalnızca bir örnektir. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](how-to-define-a-wcf-service-contract.md)  
  
-   [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)  
  
-   [Barındırma Hizmetleri](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>İstemci uygulaması karşılaştırma  
  
#### <a name="creating-a-client-in-net-remoting"></a>.NET uzaktan iletişim içinde bir istemci oluşturma  
 Bir .NET uzaktan iletişim sunucu nesnesi kullanılabilir yapıldıktan sonra istemciler tarafından gibi aşağıdaki örnekte tüketilebilir:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 Activator.GetObject() döndürülen RemotingServer örneği bir "saydam proxy." adı verilir İstemcide RemotingServer türü için genel API'si uygular, ancak farklı bir işlem veya makine çalışan sunucu nesnesi tüm yöntemlerini çağırın.  
  
#### <a name="creating-a-client-in-wcf"></a>WCF'de bir istemci oluşturma  
 WCF'de eşdeğer adımı proxy açıkça oluşturmak için bir kanal fabrikası kullanarak içerir. Proxy nesnesi Remoting gibi aşağıdaki örnekte sunucu üzerindeki işlemler gibi çağırmak için kullanılabilir:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 Bu örnek en Remoting örnektekine benzer olduğundan kanal düzeyinde programlama gösterir. Ayrıca kullanılabilir **hizmet Başvurusu Ekle** yaklaşım Visual Studio'da, programlama istemci basitleştirmek için kod oluşturur. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [İstemci Kanal Düzeyi Programlama](./extending/client-channel-level-programming.md)  
  
-   [Nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Seri hale getirme kullanımı  
 .NET uzaktan iletişim ve WCF istemci ve sunucu arasında nesneleri göndermek için seri hale getirme kullanır, ancak bunlar bu önemli farklar:  
  
1.  Bunlar farklı serileştiricileri ve kuralları ne serileştirmek belirtmek için kullanın.  
  
2.  .NET uzaktan iletişim güvenlik sınırları boyunca olan diğer katmanda, kod yürütmek için bir katmana yöntemi veya özelliği erişim sağlar. "tarafından başvurusu" serileştirme destekler. Bu özellik, güvenlik açıkları gösterir ve neden uzak uç noktaları asla güvenilmeyen istemcilere açılmamalıdır temel nedenlerinden biridir.  
  
3.  Uzaktan iletişim tarafından kullanılan serileştirme çevirin (açıkça dışarıda bırakmak serileştirmek için hangi değil) ve WCF serileştirme kabulü (seri hale getirmek için hangi üyeleri açıkça işaretleyin).  
  
#### <a name="serialization-in-net-remoting"></a>.NET uzaktan iletişim serileştirme  
 .NET uzaktan iletişim seri hale getirmek ve istemci ve sunucu arasında nesneleri seri durumdan için iki yol destekler:  
  
-   *Değere göre* – nesnenin değerlerini katmanı sınırlarında serileştirilen ve söz konusu nesne yeni bir örneğini diğer katmanında oluşturulur. Yöntemleri ya da bu yeni örnek özelliklerini yapılan her çağrı yalnızca yerel olarak yürütün ve özgün nesne veya katmanı etkilemez.  
  
-   *Başvuruya göre* – özel bir "nesne başvurusu" katmanı sınırlarında serileştirilir. Yöntemleri ya da bu nesnenin özellikleri ile bir katman etkileşim kurduğunda özgün katman özgün nesneye geri iletişim kurar. Başvuru tarafından nesneleri herhangi bir yönde – sunucudan istemciye ya da istemciden sunucuya akabilir.  
  
 Remoting değeri tarafından türlerinde [Serializable] özniteliğiyle işaretlenmiş veya ISerializable, aşağıdaki örnekte gibi uygulama:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Başvuru tarafından türleri MarshalByRefObject sınıfından aşağıdaki örnekte gibi türetilen:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Remoting'in başvuru tarafından nesneleri etkilerini anlamak oldukça önemlidir. (İstemci veya sunucu) ya da katmanı için diğer katmanı tarafından başvuru nesnesi gönderirse, tüm yöntem çağrıları geri nesnenin sahibi olan katmanında yürütün. Örneğin, sunucu tarafından döndürülen başvuru tarafından nesnesi üzerinde yöntemleri çağırma istemci kodu sunucuda yürütülür. Benzer şekilde, istemci tarafından sağlanan bir başvuru tarafından nesnesinde yöntemleri çağırma bir sunucu kodu istemci üzerinde yürütülür. Bu nedenle, yalnızca tam güvenilir ortamlar içinde .NET uzaktan iletişim kullanılması önerilir. Güvenilmeyen istemciler için genel bir .NET uzaktan iletişim uç nokta gösterme, bir uzak sunucu saldırılara karşı savunmasız hale getirir.  
  
#### <a name="serialization-in-wcf"></a>WCF'de seri hale getirme  
 WCF yalnızca değer tarafından serileştirme destekler. Aşağıdaki örnekte istemci ve sunucu arasında exchange için bir türü tanımlamak için en yaygın yolu gibidir:  
  
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
  
 [DataContract] özniteliği serileştirilmiş ve istemci ile sunucu arasında seri bu türü biri olarak tanımlar. [DataMember] özniteliği ayrı ayrı özellikler veya alanlar serileştirmek için tanımlar.  
  
 WCF katmanları arasında bir nesne gönderdiğinde, yalnızca değerleri serileştirir ve diğer katmanında nesnesinin yeni bir örneğini oluşturur. Nesnenin değerleriyle herhangi bir etkileşimi yalnızca yerel olarak – ortaya bunlar şekilde .NET uzaktan iletişim başvuru tarafından Nesneleri'ne diğer katmanı ile iletişim kurmazlar. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Serileştirme ve Seri Durumdan Çıkarma](./feature-details/serialization-and-deserialization.md)  
  
-   [Windows Communication Foundation'da seri hale getirme](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a>Özel durum işleme özellikleri  
  
#### <a name="exceptions-in-net-remoting"></a>.NET uzaktan iletişim özel durumları  
 Bir uzak sunucu tarafından oluşturulan özel durumları istemciye gönderilen, serileştirilen ve başka bir özel durum gibi istemci üzerinde yerel olarak oluşturulur. Özel durumları, özel durum türü alt classing ve [Serializable] ile işaretleme tarafından oluşturulabilir.   Çoğu framework özel durumları zaten sıralanabilir ve istemcide yeniden oluşturulması için sunucu tarafından oluşturulan çoğu izin vererek bu şekilde işaretlenir. Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri yanlışlıkla istemciye çıkarılabilecek. Bu, yalnızca tam güvenilir ortamlarında Remoting kullanılması gereken birçok nedenden biri.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Özel durumlar ve WCF hataları  
 WCF bilgilerin yanlışlıkla açığa çıkmasına için sunucudan istemciye döndürülecek rasgele özel durum türleri izin vermiyor. Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, genel amaçlı FaultException istemcide durum oluşturulmasına neden olur. Bu özel durumun neden veya burada bir hata oluştu ve bazı uygulamalar için bu yeterli herhangi bir bilgi taşımaz. Gereken uygulamalar istemci yapmak için daha zengin hata bilgisi bu hataya sözleşmesi tanımlayarak iletişim kurar.  
  
 Bunu yapmak için önce hata bilgilerini taşımak için bir [DataContract] türü oluşturun.  
  
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
  
 Sunucu, bir FaultException atma tarafından hata koşulları bildirir.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 Ve istemcisi sunucuya istekte olduğunda, normal özel durumlar olarak hatalar yakalayabilir.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 Hataya sözleşmeleri hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
  
#### <a name="security-in-net-remoting"></a>.NET uzaktan iletişim güvenliği  
 Bazı .NET uzaktan iletişim kanalları kimlik doğrulama ve şifrelemeyi (IPC ve TCP) kanal katmanında gibi güvenlik özelliklerini destekler. HTTP kanalı, kimlik doğrulama ve şifreleme için Internet Information Services (IIS) kullanır. Bu destek rağmen güvenli olmayan bir iletişim protokolü .NET uzaktan iletişim göz önünde bulundurun ve yalnızca tam güvenilir ortamlar içinde kullanmanız gerekir. Hiçbir zaman İnternet'te veya güvenilmeyen istemciler için genel bir uzak uç nokta kullanıma sunar.  
  
#### <a name="security-in-wcf"></a>WCF'de Güvenlik  
 WCF ile göz önünde bulundurularak, kısmen .NET uzaktan iletişim içinde bulunan güvenlik açıklarına türlerini gidermek için tasarlanmıştır. WCF taşıma ve ileti düzeyinde güvenlik sunar ve kimlik doğrulama, yetkilendirme, şifreleme vb. için birçok seçenek sunar. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Güvenlik](./feature-details/security.md)  
  
-   [WCF Güvenlik Kılavuzu](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Wcf'ye taşınma  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Neden uzaktan iletişimden WCF'ye geçirme?  
  
-   **.NET uzaktan iletişim eski bir üründür.** Bölümünde açıklandığı gibi [.NET uzaktan iletişim](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), eski bir ürün olarak kabul edilir ve yeni geliştirme projeleri için önerilmez. WCF veya ASP.NET Web API yeni ve mevcut uygulamalar için önerilir.  
  
-   **WCF platformlar arası standartlar kullanır.** WCF ile platformlar arası birlikte çalışabilirlik aklınızda tasarlanmıştır ve çoğu endüstri standartları destekler (SOAP, WS-Security, WS-Trust, vs.). Bir WCF Hizmeti Windows dışındaki işletim sistemlerinde çalışan istemcileri ile çalışabilirler. Remoting, birincil sunucu ve istemci uygulamaları bir Windows işletim sisteminde .NET framework kullanılarak çalıştırdığı ortamlar için tasarlanmıştır.  
  
-   **WCF yerleşik güvenlik sahiptir.** WCF güvenlik göz önünde bulundurularak ile tasarlanmıştır ve kimlik doğrulama, taşıma düzeyi güvenliği, ileti düzeyi güvenlik vb. için birçok seçenek sunar. Remoting birlikte çalışmak üzere uygulamalar için kolaylaştırmak için tasarlanmıştır ancak güvenilir olmayan ortamlarda güvenli olacak şekilde tasarlanmamıştır. WCF, güvenilir ve güvenilir olmayan ortamlarda çalışmak üzere tasarlanmıştır.  
  
### <a name="migration-recommendations"></a>Geçiş önerileri  
 .NET uzaktan iletişimden WCF'ye geçirme için önerilen adımları şunlardır:  
  
-   **Hizmet sözleşmesi oluşturun.** Hizmet arabirimi türlerini tanımlayın ve bunları [ServiceContract] özniteliğiyle işaretleyin. İstemciler [OperationContract] ile çağırmak için izin verilecek tüm yöntemleri işaretleyin.  
  
-   **Veri sözleşmesi oluşturun.** İstemci ve sunucu arasında alınıp ve [DataContract] özniteliğiyle işaretlerken veri türlerini tanımlayın. İstemci [DataMember] ile kullanmasına izin tüm alanları ve özellikleri işaretleyin.  
  
-   **Hatalı Sözleşme (isteğe bağlı) oluşturun.** Hatalarla karşılaştığında, istemci ve sunucu arasında alınıp türleri oluşturun. Bu türleriyle [DataContract] ve [DataMember] seri hale getirilebilir yapmak için işaretleyin. [OperationContract] ile işaretli tüm hizmet işlemleri için Ayrıca bunları [bunlar döndürebilir hangi hatalarını belirtmek için FaultContract] ile işaretleyin.  
  
-   **Hizmetini barındırır ve yapılandırın.** Hizmet sözleşmesi oluşturulduktan sonra sonraki adım hizmetin bir uç noktada kullanıma sunmak için bir bağlama yapılandırmaktır. Daha fazla bilgi için bkz: [uç noktalar: adresler, bağlamalar ve sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Remoting uygulama için WCF geçirildikten sonra .NET uzaktan iletişim bağımlılıkları kaldırın hala önemlidir. Bu, herhangi bir uzak açığını uygulamadan kaldırılır sağlar. Bu adımlar şunları içerir:  
  
-   **MarshalByRefObject kullanımını durdur.** MarshalByRefObject türü yalnızca uzaktan iletişim için mevcut ve WCF tarafından kullanılmaz. MarshalByRefObject alt sınıf tüm uygulama türleri kaldırılan veya değiştirilen. MarshalByRefObject türü yalnızca uzaktan iletişim için mevcut ve WCF tarafından kullanılmaz. MarshalByRefObject alt sınıf tüm uygulama türleri kaldırılan veya değiştirilen.  
  
-   **[Serializable] kullanımını ve ISerializable durdur.** [Serializable] özniteliği ve ISerializable arabirimi başlangıçta güvenilen ortamlar içinde türleri serileştirmek için tasarlanmıştır ve bunlar tarafından uzaktan iletişim kullanılır. WCF seri hale getirme [DataContract] ile işaretli türleri ve [DataMember] dayanır. Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir. [Serializable] özniteliği ve ISerializable arabirimi başlangıçta güvenilen ortamlar içinde türleri serileştirmek için tasarlanmıştır ve bunlar tarafından uzaktan iletişim kullanılır. WCF seri hale getirme [DataContract] ile işaretli türleri ve [DataMember] dayanır. Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.  
  
### <a name="migration-scenarios"></a>Geçiş senaryoları  
 Şimdi aşağıdaki ortak Remoting senaryolarda WCF gerçekleştirmek nasıl görelim:  
  
1.  Sunucu istemciye bir nesne tarafından-değeri döndürür  
  
2.  Sunucu istemciye bir nesne başvuru tarafından döndürür  
  
3.  İstemci bir nesne tarafından-değeri sunucusuna gönderir.  
  
> [!NOTE]
>  WCF'de bir nesne başvuru tarafından istemciden sunucuya gönderme izin verilmiyor.  
  
 Bu senaryolar üzerinden okunurken .NET uzaktan iletişim için bizim temel arabirimleri gibi aşağıdaki örneğe varsayalım. .NET uzaktan iletişim uygulaması WCF eşdeğer işlevsellik uygulamak için yalnızca nasıl kullanılacağını göstermek istiyoruz çünkü burada önemli değildir.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Senaryo 1: Hizmet bir nesne değeri döndürür  
 Bu senaryo, bir nesne değeri tarafından istemciye göndermeden bir sunucu gösterir. Aşağıdaki adımlar yalnızca normal bir WCF hizmeti oluşturma açıklamak için WCF her zaman nesneleri sunucudan değere göre döndürür.  
  
1.  WCF hizmeti için ortak bir arabirim tanımlayarak başlatın ve [ServiceContract] özniteliğiyle işaretleyin. [OperationContract] istemci çağıracak sunucu tarafı yöntemlerinin tanımlamak için kullanırız.  
  
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
  
2.  Sonraki adım, bu hizmet için veri sözleşmesi oluşturmaktır. Biz [DataContract] özniteliğiyle işaretlenmiş sınıflar (arabirimler değil) oluşturarak bunu. Ayrı ayrı özellikler veya alanlar hem istemci hem de sunucu görünür istiyoruz [DataMember] ile işaretlenir. İzin verilmesi için türetilen türlerin istiyoruz, biz [KnownType] özniteliği bunları tanımlamak için kullanmanız gerekir. Yalnızca türü WCF serileştirilecek veya bu hizmeti için hizmet arabirimi ve bu "bilinen türlerini" de serisi olanak sağlar. Bu listede olmayan herhangi bir türü exchange çalışılıyor reddedilir.  
  
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
  
3.  Ardından, hizmet arabirimi uygulamasını sağlar.  
  
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
  
4.  WCF hizmetini çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL, bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmek ihtiyacımız. Bu durum genellikle aşağıdaki bölümlerde sunucu projenin web.config dosyasına ekleyerek yapılır.  
  
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
  
5.  WCF hizmet sonra aşağıdaki kodla başlatılabilir:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Bu ServiceHost başlatıldığında, web.config dosyasının uygun sözleşme ve bağlama bitiş noktası kurmak için kullanır. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](./configuring-services-using-configuration-files.md). Sunucu başlatma bu stili kendi kendine barındırma olarak bilinir. WCF hizmetlerini barındırmak için diğer seçenekler hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](./hosting-services.md).  
  
6.  İstemci projenin app.config hizmet uç noktası için eşleşen bağlama bilgileri belirtmesi gerekir. Visual Studio'da bunu yapmanın en kolay yolu kullanmaktır **hizmet Başvurusu Ekle**, hangi otomatik olarak güncelleştirilecek app.config dosyası. Alternatif olarak, aynı değişiklikleri el ile eklenebilir.  
  
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
  
     Kullanma hakkında daha fazla bilgi için **hizmet Başvurusu Ekle**, bkz: [nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7.  Şimdi biz istemciden WCF Hizmeti çağırabilirsiniz. Biz bu hizmet için bir kanal fabrikası oluşturma için bir kanal soran ve doğrudan bu kanalda istiyoruz yöntemi çağırma bunu. Kanal hizmetin arabirimini uygulayan ve bize için temel alınan istek/yanıt mantığı işler çünkü bunu yapabilirsiniz. Bu yöntem çağrısının dönüş değerini sunucunun yanıt seri durumdan çıkarılmış kopyasıdır.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 WCF tarafından sunucudan istemciye döndürülen her zaman değeriyle nesneleridir. Sunucu tarafından gönderilen verileri seri durumdan çıkarılmış kopyalarını nesneleridir. İstemci, sunucu kodu geri çağırma hiçbir tehlike olmadan bu yerel kopyalar üzerinde yöntemleri çağırabilir.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Senaryo 2: Sunucu başvuruya göre bir nesne döndürür  
 Bu senaryo, bir nesne başvurusu tarafından istemciye sağlayan sunucuda gösterir. .NET uzaktan çalışma, bu otomatik olarak MarshalByRefObject öğesinden türetilmiş herhangi bir tür için işlenir başvuru tarafından olduğu seri hale getirilmiş. Bu senaryo örneği süre sonuyla sunucu tarafı nesneleri bağımsız sağlamak birden çok istemciye izin verir. Daha önce belirtildiği gibi bir WCF hizmeti tarafından döndürülen nesne her zaman değer ile bu yüzden bir başvuru olarak nesnesinin doğrudan bir eşdeğer ancak semantiği başvuru olarak kullanılacak benzer bir şey elde etmek olası bir <xref:System.ServiceModel.EndpointAddress10> nesnesi. Bu sunucu üzerindeki bir süre sonuyla başvurusu tarafından nesnesi edinmek için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir. Bu süre sonuyla sunucu tarafı nesneleri bağımsız ile birden çok istemciye sahip olmanın senaryo sağlar.  
  
1.  İlk olarak, biz süre sonuyla nesnenin kendisine karşılık gelen bir WCF Hizmeti sözleşmesi tanımlamanız gerekir.  
  
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
    >  Normal bir WCF Hizmeti arabirimi kolaylaştırarak süre sonuyla nesnesi [ServiceContract] ile işaretli olduğundan, dikkat edin. SessionMode ayarlama özelliği, bir süre sonuyla hizmet olacaktır belirtir. WCF'de, bir oturum iki uç noktaları arasında gönderilen birden fazla ileti bağıntı bir yoludur. Bu, bir istemci bu hizmet için bir bağlantı alır sonra bir oturum istemci ve sunucu arasında kurulacak olduğunu anlamına gelir. İstemci bu tek oturum içinde kendi etkileşimler için sunucu tarafı nesnesi tek bir benzersiz örneğini kullanın.  
  
2.  Ardından, biz bu hizmet arabirimi uyarlamasını sağlamanız gerekir. [ServiceBehavior] ile belirten ve InstanceContextMode ayarını, biz WCF Biz bu tür benzersiz bir örnek bir her oturum için kullanmak istediğiniz söyleyin.  
  
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
  
3.  Şimdi bu süre sonuyla nesne örneği elde etmek için bir yol gerekir. Biz bunu bir EndpointAddress10 nesnesi başka bir WCF Hizmeti arabirimi oluşturarak yapabilirsiniz. Bu istemci süre sonuyla nesnesi oluşturmak için kullanabileceğiniz bir uç nokta seri hale getirilebilir biçimidir.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     Biz bu WCF hizmetini ve uygulamak:  
  
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
  
     Bu uygulama süre sonuyla nesneleri oluşturmak için bir singleton kanal fabrikası tutar. GetInstanceAddress() çağrıldığında bir kanal oluşturur ve etkili bir şekilde bu kanal ile ilişkilendirilen uzak adres işaret eden bir EndpointAddress10 nesnesi oluşturur. EndpointAddress10 istemci tarafından değerinin döndürülebilecek yalnızca bir veri türüdür.  
  
4.  Aşağıdaki örnekte gösterildiği gibi iki şunları yaparak sunucu yapılandırma dosyasını değiştirmek ihtiyacımız var:  
  
    1.  Bildirme bir \<istemci > süre sonuyla nesne için uç noktaya açıklayan bölümü. Bu, sunucunun da bu durumda istemci olarak davrandığı için gereklidir.  
  
    2.  Uç noktaları Fabrika ve sessionful nesnesinin bildirin. Bu istemcinin hizmet uç noktaları ile EndpointAddress10 almaya ve süre sonuyla kanal oluşturmak için iletişim sağlamak gereklidir.  
  
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
  
     Ve ardından Biz bu hizmetleri başlatabilirsiniz:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  Biz, istemci kendi projenin app.config dosyasını aynı Bu uç noktaları bildirerek yapılandırın.  
  
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
  
6.  Oluşturun ve bu süre sonuyla nesnesini kullanmak için istemci aşağıdakileri yapmanız gerekir:  
  
    1.  ISessionBoundFactory hizmet bir kanal oluşturun.  
  
    2.  Bu kanal, bir EndpointAddress10 elde etmek için o hizmetini çağırmak için kullanın.  
  
    3.  Bir süre sonuyla nesnesi elde etmek için bir kanal oluşturmak için EndpointAddress10 kullanın.  
  
    4.  Aynı örneği arasında birden fazla çağrı kalır göstermek için süre sonuyla nesnesi ile etkileşim.  
  
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
  
 WCF, nesneler her zaman değeri döndürür. ancak başvuru tarafından semantiği EndpointAddress10 kullanımı ile denk desteklemek mümkündür. Bu daha sonra onu ile herhangi bir WCF hizmeti gibi etkileşim kurabilen bir süre sonuyla WCF hizmet örneği istemesine izin verir.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Senaryo 3: Sunucu istemcisi, bir değer tarafından örneği gönderir.  
 Bu senaryo, temel olmayan nesne örneği sunucuya değeriyle gönderme istemci gösterir. WCF değeriyle yalnızca nesneleri gönderdiğinden, bu senaryo normal WCF kullanım gösterir.  
  
1.  Senaryo 1 aynı WCF hizmetinden kullanın.  
  
2.  Yeni bir değer tarafından nesnesi (müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesne göndermek için istemci kullanın.  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     Müşteri nesnesi seri hale getirilmiş ve burada söz konusu nesne yeni bir kopyasını serisi ve sunucuya gönderilen.  
  
    > [!NOTE]
    >  Bu kod ayrıca türetilmiş bir tür (PremiumCustomer) gönderme gösterir. Hizmet arabirimi müşteri nesnesi bekliyor, ancak müşteri sınıfı [KnownType] öznitelikte PremiumCustomer de izin gösterilir. WCF serileştirmek veya bu hizmeti arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.  
  
 Normal WCF alışverişleri veri tarafından değerlerdir. Bu garanti altına alır. Bu veri nesneleri birinde yöntemlerini çağırma, yalnızca yerel olarak yürütür – kod bir katman çağırma kullanılamaz. Başvuru tarafından döndürülen nesne gibi bir şey elde etmek mümkün olmakla birlikte *gelen* sunucu tarafından başvuru nesnesi geçirmek için bir istemci yoktur *için* sunucu. İstemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo çift yönlü hizmetini kullanarak WCF'de elde edilebilir. Daha fazla bilgi için bkz: [çift yönlü Hizmetler](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Özet  
 .NET uzaktan iletişim, yalnızca tam güvenilir ortamlarında kullanılmak üzere bir iletişim çerçevedir. Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir. Yeni uygulama oluşturmak için kullanılmamalıdır. Buna karşılık, WCF göz önünde bulundurularak ile tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir. Microsoft, varolan önerir uzaktan iletişim uygulamalarını geçirilirken WCF veya ASP.NET Web API kullanın.