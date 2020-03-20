---
title: 'Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181385"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme
Windows Communication Foundation (WCF), dağıtılmış bir ortamda sunucular ve istemciler arasında yönetilen kod çağrıları için Dağıtılmış Bileşen Nesne Modeli (DCOM) yerine önerilen ve güvenli bir seçimdir. Bu makalede, aşağıdaki senaryolar için dcom'dan WCF'ye kodu nasıl geçirtilebilirsiniz.  
  
- Uzak hizmet, bir nesneyi istemciye göre döndürür  
  
- İstemci uzak hizmete bir nesneyi by-value gönderir  
  
- Uzak hizmet istemciye bir nesne by-reference döndürür  
  
 Güvenlik nedenleriyle, istemciden hizmete bir nesne nin gönderilmesine WCF'de izin verilmez. İstemci ve sunucu arasında ileri geri görüşme gerektiren bir senaryo, çift yönlü bir hizmet kullanılarak WCF'de elde edilebilir.  Çift yönlü hizmetler hakkında daha fazla bilgi için [Bkz. Çift Yönlü Hizmetler.](../wcf/feature-details/duplex-services.md)  
  
 WCF hizmetleri ve bu hizmetler için istemcioluşturma hakkında daha fazla bilgi için, [Temel WCF Programlama,](../wcf/basic-wcf-programming.md) [Tasarım ve Hizmetleri Uygulama](../wcf/designing-and-implementing-services.md)ve Bina [İstemcibölümü'ne](../wcf/building-clients.md)bakın.  
  
## <a name="dcom-example-code"></a>DCOM örnek kodu  
 Bu senaryolar için, WCF kullanılarak resimlenen DCOM arabirimleri aşağıdaki yapıya sahiptir:  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a>Hizmet nesneyi değere göre döndürür  
 Bu senaryo için, bir hizmete çağrı yaparsınız ve bu yöntem sunucudan istemciye göre geçirilen bir nesneyi döndürür. Bu senaryo aşağıdaki COM çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 Bu senaryoda, istemci uzak hizmetten bir nesnenin deserialized kopyasını alır. İstemci, hizmete geri çağırmadan bu yerel kopyayla etkileşim kurabilir.  Başka bir deyişle, istemci, yerel kopyadaki yöntemler çağrıldığında hizmetin hiçbir şekilde dahil olmayacağını garanti edecektir. WCF nesneleri her zaman hizmetten değere göre döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmeti oluşturmayı açıklar.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Adım 1: WCF hizmet arabirimini tanımlayın  
 WCF hizmeti için ortak bir arabirim tanımlayın ve []<xref:System.ServiceModel.ServiceContractAttribute>özniteliğiyle işaretleyin.  [ ]<xref:System.ServiceModel.OperationContractAttribute>özniteliği ile istemcilere maruz bırakmak istediğiniz yöntemleri işaretleyin. Aşağıdaki örnek, sunucu tarafı arabirimini ve istemcinin çağırabileceği arabirim yöntemlerini tanımlamak için bu öznitelikleri kullanır. Bu senaryo için kullanılan yöntem kalın olarak gösterilir.  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a>Adım 2: Veri sözleşmesini tanımlama  
 Ardından, hizmet ve istemcileri arasında verilerin nasıl değiş tokuş edileceğini açıklayan bir veri sözleşmesi oluşturmanız gerekir.  Veri sözleşmesinde açıklanan sınıflar [ ]<xref:System.Runtime.Serialization.DataContractAttribute>özniteliği ile işaretlenmelidir. Hem istemci hem de sunucu tarafından görülebilmesini istediğiniz tek<xref:System.Runtime.Serialization.DataMemberAttribute>tek özellikler veya alanlar [ ] özniteliği ile işaretlenmelidir. Veri sözleşmesinde bir sınıftan türetilen türlerin izin verilmesini istiyorsanız,<xref:System.Runtime.Serialization.KnownTypeAttribute>bunları [ ] özniteliğiyle tanımlamanız gerekir. WCF yalnızca hizmet arabirimindeki türleri ve bilinen türler olarak tanımlanan türleri serihale veya deserialize eder. Bilinen bir tür olmayan bir tür kullanmaya çalışırsanız, bir özel durum oluşur.  
  
 Veri sözleşmeleri hakkında daha fazla bilgi için [Bkz. Veri Sözleşmeleri.](../wcf/samples/data-contracts.md)  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a>Adım 3: WCF hizmetini uygulayın  
 Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmet sınıfını uygulamanız gerekir.  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a>Adım 4: Hizmeti ve istemciyi yapılandır  
 Bir WCF hizmetini çalıştırmak için, belirli bir WCF bağlama kullanarak bu hizmet arabirimini belirli bir URL'de gösteren bir bitiş noktası bildirmeniz gerekir. Bağlama, istemcilerin ve sunucunun iletişim kurması için aktarım, kodlama ve protokol ayrıntılarını belirtir. Genellikle hizmet projesinin yapılandırma dosyasına (web.config) bağlamalar eklersiniz. Aşağıdaki örnek hizmet için bağlayıcı bir giriş gösterir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ardından, istemciyi hizmet tarafından belirtilen bağlama bilgileriyle eşleşecek şekilde yapılandırmanız gerekir. Bunu yapmak için, istemcinin uygulama yapılandırmasına (app.config) aşağıdakileri ekleyin.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Adım 5: Hizmeti çalıştırın  
 Son olarak, servis uygulamasına aşağıdaki satırları ekleyerek ve uygulamayı başlatarak konsol uygulamasında kendi kendine barındırabilirsiniz. Bir WCF hizmet uygulaması barındırmak için diğer yollar hakkında daha fazla bilgi için, [Hosting Hizmetleri](../wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Adım 6: Hizmeti istemciden arayın  
 Hizmeti istemciden aramak için, hizmet için bir kanal fabrikası oluşturmanız ve `GetCustomer` yöntemi doğrudan istemciden doğrudan aramanızı sağlayacak bir kanal istemeniz gerekir. Kanal, hizmetin arabirimini uygular ve sizin için temel istek/yanıt mantığını işler.  Bu yöntem çağrısından gelen iade değeri, hizmet yanıtının deserialized kopyasıdır.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>İstemci sunucuya bir by-value nesnesi gönderir  
 Bu senaryoda, istemci sunucuya bir nesne gönderir, yan değer. Bu, sunucunun nesnenin deserialized kopyasını alacağı anlamına gelir.  Sunucu bu kopyadaki yöntemleri arayabilir ve istemci koduna geri arama yapılmadığını garanti edebilir. Daha önce de belirtildiği gibi, normal WCF veri değişimleri ayrı değerdir.  Bu, bu nesnelerden birinde arama yöntemlerinin yalnızca yerel olarak yürütüleceğini garanti eder – istemciye kod çağırmaz.  
  
 Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır. Buna ek olarak, istemci ve hizmet aynı şekilde yapılandırılacaktır. Bu örnekte, nesneyi göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur. Ancak, bu örnek için, bir nesneyi değere göre geçirerek hizmeti çağıran bir istemci oluşturursunuz. İstemcinin hizmet sözleşmesinde çağıracağı hizmet yöntemi kalın olarak gösterilir:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Bir yan değer nesnesi gönderen istemciye kod ekleme  
 Aşağıdaki kod, istemcinin yeni bir yan değer müşteri nesnesi nasıl oluşturduğunu, `ICustomerManager` hizmetle iletişim kurmak için bir kanal oluşturduğunu ve müşteri nesnesini bu nesneye nasıl gönderdiğini gösterir.  
  
 Müşteri nesnesi seri hale getirilecek ve hizmete gönderilir ve bu nesnenin yeni bir kopyasına hizmet tarafından deserialized.  Hizmetin bu nesne üzerinde çağırdığı tüm yöntemler yalnızca sunucuda yerel olarak yürütülür. Bu kodun türetilmiş bir türü ( )`PremiumCustomer`göndermeyi gösterdiğini unutmayın.  Hizmet sözleşmesi bir `Customer` nesne bekler, ancak hizmet<xref:System.Runtime.Serialization.KnownTypeAttribute>veri söylecisi de izin `PremiumCustomer` verildiğini belirtmek için [ ] özniteliğini kullanır.  WCF, bu hizmet arabirimi aracılığıyla başka bir türü serileştirme veya deserialize etme girişimlerinde başarısız olur.  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a>Hizmet başvuru ile bir nesne döndürür  
 Bu senaryo için, istemci uygulaması uzak hizmeti bir çağrı yapar ve yöntem istemciye hizmetten başvuru ile geçirilen bir nesne döndürür.  
  
 Daha önce de belirtildiği gibi, WCF hizmetleri her zaman nesneyi değerolarak döndürer.  Ancak, <xref:System.ServiceModel.EndpointAddress10> sınıfı kullanarak benzer bir sonuç elde edebilirsiniz.  Sunucuda <xref:System.ServiceModel.EndpointAddress10> oturum dolusu ara başvuru nesnesi elde etmek için istemci tarafından kullanılabilecek serileştirilebilir bir by-value nesnesidir.  
  
 Bu senaryoda gösterilen WCF'deki başvuru nesnesinin davranışı DCOM'dan farklıdır.  DCOM'da, sunucu bir başvuru nesnesini doğrudan istemciye döndürebilir ve istemci bu nesnenin sunucuda yürüten yöntemlerini çağırabilir.  Ancak WCF'de döndürülen nesne her zaman değer eve dir.  İstemci, temsil edilen bu yan <xref:System.ServiceModel.EndpointAddress10> değer nesnesini almalı ve kendi oturumlu by-reference nesnesini oluşturmak için kullanmalıdır.  İstemci yöntemi sunucuda oturum nesnesi yürütme çağırır. Başka bir deyişle, WCF'deki bu başvuru nesnesi, oturum lu olarak yapılandırılan normal bir WCF hizmetidir.  
  
 WCF'de oturum, iki uç nokta arasında gönderilen birden çok iletiyi ilişkilendirme yoludur.  Bu, istemci bu hizmete bağlantı ulaştığında istemci ve sunucu arasında bir oturum oluşturulacağı anlamına gelir.  İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafındaki nesnenin tek bir benzersiz örneğini kullanır. Oturumlu WCF sözleşmeleri, bağlantı yönelimli ağ isteği/yanıt kalıplarına benzer.  
  
 Bu senaryo aşağıdaki DCOM yöntemi yle temsil edilir.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Adım 1: Oturumlu WCF hizmet arabirimini ve uygulamasını tanımlayın  
 İlk olarak, oturum nesnesi içeren bir WCF hizmet arabirimi tanımlayın.  
  
 Bu kodda, oturum oluşturan nesne, `ServiceContract` onu normal bir WCF hizmet arabirimi olarak tanımlayan öznitelik ile işaretlenir.  Buna ek <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> olarak, özellik bir oturum hizmeti olacağını belirtmek için ayarlanır.  
  
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
  
 Aşağıdaki kod hizmet uygulamasını gösterir.  
  
 Hizmet [ServiceBehavior] özniteliği ile işaretlenir ve instanceContextMode özelliği her oturum için bu tür benzersiz bir örnek oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions olarak ayarlanır.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Adım 2: Oturum daki nesne için WCF fabrika hizmetini tanımlayın  
 Oturum oluşturabilen nesneyi oluşturan hizmet tanımlanmalı ve uygulanmalıdır. Aşağıdaki kod, bunun nasıl yapılacağını gösterir. Bu kod, bir nesneyi döndüren başka bir <xref:System.ServiceModel.EndpointAddress10> WCF hizmeti oluşturur.  Bu, oturum dolu nesneyi oluşturmak için kullanabileceği bir bitiş noktasının serileştirilebilir biçimidir.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Bu hizmetin uygulanması aşağıda veda edileb'dir. Bu uygulama, oturumlu nesneler oluşturmak için bir singleton kanal fabrika tutar.  Çağrıldığında, `GetInstanceAddress` bir kanal oluşturur ve <xref:System.ServiceModel.EndpointAddress10> bu kanalla ilişkili uzak adrese işaret eden bir nesne oluşturur.   <xref:System.ServiceModel.EndpointAddress10>istemciye göre değer olarak döndürülebilen bir veri türüdür.
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Adım 3: WCF hizmetlerini yapılandırın ve başlatın  
 Bu hizmetleri barındırmak için sunucunun yapılandırma dosyasına (web.config) aşağıdaki eklemeleri yapmanız gerekir.  
  
1. Oturum `<client>` açan nesnenin bitiş noktasını açıklayan bir bölüm ekleyin.  Bu senaryoda, sunucu da bir istemci olarak hareket eder ve bunu etkinleştirmek için yapılandırılmalıdır.  
  
2. `<services>` Bölümde, fabrika ve oturum nesnesi için hizmet bitiş noktalarını bildirin.  Bu, istemcinin hizmet uç noktalarıyla iletişim <xref:System.ServiceModel.EndpointAddress10> kurmasını, oturum alabilme kanalını edinmesini ve oluşturmasını sağlar.  
  
 Aşağıdaki bu ayarları ile örnek bir yapılandırma dosyasıdır:  
  
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
  
 Hizmeti kendi kendine barındırmak için bir konsol uygulamasına aşağıdaki satırları ekleyin ve uygulamayı başlatın.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Adım 4: İstemciyi yapılandırın ve hizmeti arayın  
 Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girişleri yaparak istemciyi WCF hizmetleriyle iletişim kuracak şekilde yapılandırın.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
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
  
 Hizmeti aramak için aşağıdakileri yapmak için kodu istemciye ekleyin:  
  
1. `ISessionBoundFactory` Hizmetiçin bir kanal oluşturun.  
  
2. `ISessionBoundFactory` Bir <xref:System.ServiceModel.EndpointAddress10> nesne elde etmek için hizmet çağırmak için kanalı kullanın.  
  
3. <xref:System.ServiceModel.EndpointAddress10> Oturum lu bir nesne elde etmek için kanal oluşturmak için kullanın.  
  
4. Çağrı `SetCurrentValue` ve `GetCurrentValue` yöntemleri göstermek için aynı nesne örneği birden çok arama arasında kullanılır kalır.  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../wcf/basic-wcf-programming.md)
- [Hizmetleri Tasarlama ve Uygulama](../wcf/designing-and-implementing-services.md)
- [İstemci Derleme](../wcf/building-clients.md)
- [Çift Yönlü Hizmetler](../wcf/feature-details/duplex-services.md)
