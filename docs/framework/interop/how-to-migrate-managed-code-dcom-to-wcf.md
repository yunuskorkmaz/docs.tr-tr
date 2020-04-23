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
Windows Communication Foundation (WCF) dağıtılmış bir ortamdaki sunucular ve istemciler arasındaki yönetilen kod çağrıları için dağıtılmış bileşen nesne modeli (DCOM) üzerinde önerilen ve güvenli seçenektir. Bu makalede, aşağıdaki senaryolar için DCOM 'dan WCF 'ye nasıl kod geçirebileceğiniz gösterilmektedir.  
  
- Uzak hizmet, istemciye bir nesne değeri döndürür  
  
- İstemci, uzak hizmete bir nesne olarak değer gönderir  
  
- Uzak hizmet, istemciye başvuruya göre bir nesne döndürür  
  
 Güvenlik nedenleriyle, istemciden hizmete bir nesne başvuruya göre gönderilmesi WCF 'de buna izin verilmez. Bir çift yönlü hizmet kullanılarak, istemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo WCF 'de elde edilebilir.  Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [çift yönlü hizmetler](../wcf/feature-details/duplex-services.md).  
  
 Bu hizmetler için WCF Hizmetleri ve istemcileri oluşturma hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../wcf/basic-wcf-programming.md), [Hizmetleri tasarlama ve uygulama](../wcf/designing-and-implementing-services.md)ve [istemci oluşturma](../wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>DCOM örnek kodu  
 Bu senaryolar için, WCF kullanılarak gösterilen DCOM arabirimleri aşağıdaki yapıya sahiptir:  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Hizmet bir nesne değere göre döndürüyor  
 Bu senaryo için, bir hizmet çağrısı yaparsınız ve IT yöntemi sunucudan istemciye değer ile geçirilen bir nesne döndürür. Bu senaryo aşağıdaki COM çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 Bu senaryoda istemci, uzak hizmetten bir nesnenin serisi kaldırılmış bir kopyasını alır. İstemci, hizmete geri çağrı yapmadan bu yerel kopyayla etkileşime geçebilir.  Diğer bir deyişle, istemci garanti edilir çünkü yerel kopyada Yöntemler çağrıldığında hizmetin hiçbir şekilde ilgili olmaması gerekir. WCF her zaman değere göre hizmetten nesneleri döndürür, bu nedenle aşağıdaki adımlarda normal bir WCF hizmeti oluşturma açıklanır.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>1. Adım: WCF hizmeti arabirimini tanımlama  
 WCF hizmeti için bir ortak arabirim tanımlayın ve [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliğiyle işaretleyin.  İstemcilere göstermek istediğiniz yöntemleri [<xref:System.ServiceModel.OperationContractAttribute>] özniteliğiyle işaretleyin. Aşağıdaki örnek, bir istemcinin çağırabilmesi için sunucu tarafı arabirimi ve arabirim yöntemlerini tanımlamak üzere bu özniteliklerin kullanımını gösterir. Bu senaryo için kullanılan yöntem kalın olarak gösterilmiştir.  
  
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
  
### <a name="step-2-define-the-data-contract"></a>2. Adım: veri sözleşmesini tanımlama  
 Daha sonra hizmet için bir veri sözleşmesi oluşturmanız gerekir, bu, hizmetin ve istemcilerinin arasında verilerin nasıl değiş tokuş olacağını anlatmaktadır.  Veri sözleşmesinde açıklanan sınıflar [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliğiyle işaretlenmelidir. Hem istemci hem de sunucu için görünür olmasını istediğiniz bireysel özellikler veya alanlar [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliğiyle işaretlenmelidir. Veri sözleşmesindeki bir sınıftan türetilmiş türlerin izin verilmesini istiyorsanız, bunları [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliğiyle belirlemeniz gerekir. WCF yalnızca hizmet arabirimindeki türleri ve bilinen türler olarak tanımlanan türleri seri hale getir veya seri durumdan çıkaracaktır. Bilinen bir tür olmayan bir türü kullanmaya çalışırsanız, bir özel durum oluşur.  
  
 Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [veri sözleşmeleri](../wcf/samples/data-contracts.md).  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a>3. Adım: WCF hizmetini uygulama  
 Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmeti sınıfını uygulamalısınız.  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>4. Adım: hizmeti ve istemciyi yapılandırma  
 Bir WCF hizmetini çalıştırmak için belirli bir WCF bağlamasını kullanarak bu hizmet arabirimini belirli bir URL 'de kullanıma sunan bir uç nokta bildirmeniz gerekir. Bir bağlama, iletişim kuracak istemciler ve sunucu için Aktarım, kodlama ve protokol ayrıntılarını belirtir. Genellikle, hizmet projesinin yapılandırma dosyasına (Web. config) bağlama eklersiniz. Aşağıda örnek hizmet için bir bağlama girişi gösterilmektedir:  
  
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
  
 Ardından, istemciyi, hizmet tarafından belirtilen bağlama bilgileriyle eşleşecek şekilde yapılandırmanız gerekir. Bunu yapmak için, istemcinin uygulama yapılandırma (App. config) dosyasına aşağıdakini ekleyin.  
  
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
  
### <a name="step-5-run-the-service"></a>5. Adım: hizmeti çalıştırma  
 Son olarak, hizmet uygulamasına aşağıdaki satırları ekleyerek ve uygulamayı başlatarak bir konsol uygulamasında kendi kendine barındırabilirsiniz. Bir WCF hizmet uygulamasını [barındırma hizmetleri, barındırma hizmetleri](../wcf/hosting-services.md)hakkında daha fazla bilgi için.  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>6. Adım: istemciden hizmeti çağırma  
 Hizmeti istemciden çağırmak için, hizmet için bir kanal fabrikası oluşturmanız ve bir kanal istemeniz gerekir. Bu, doğrudan istemciden doğrudan bir `GetCustomer` yöntemi çağırmasını sağlar. Kanal, hizmetin arabirimini uygular ve temel alınan istek/yanıt mantığını sizin için işler.  Bu yöntem çağrısından gelen dönüş değeri, hizmet yanıtının Serisi kaldırılan kopyasıdır.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>İstemci sunucuya bir değere göre nesnesi gönderiyor  
 Bu senaryoda, istemci sunucuya bir nesne gönderir ve değeri göre. Bu, sunucunun, serisi kaldırılan nesnenin bir kopyasını alacağı anlamına gelir.  Sunucu söz konusu kopyada yöntemleri çağırabilir ve istemci koduna geri çağırma olmadığı garantisini alabilir. Daha önce belirtildiği gibi, verilerin normal WCF değişimlerinin değeri şunlardır.  Bu, bu nesnelerden birine çağırma yöntemlerinin yalnızca yerel olarak yürütüldüğünden emin olur; istemcide kod çağırmaz.  
  
 Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimini ve veri sözleşmesini kullanır. Ayrıca, istemci ve hizmet aynı şekilde yapılandırılır. Bu örnekte, nesneyi göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur. Ancak, bu örnekte, bir nesneyi değere göre geçirerek hizmeti çağıran bir istemci oluşturacaksınız. İstemcinin hizmet sözleşmesinde çağırabilecek hizmet yöntemi kalın olarak gösterilmiştir:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>İstemciye değer nesnesi gönderen istemciye kod ekleme  
 Aşağıdaki kod, istemcinin yeni bir değerli müşteri nesnesi nasıl oluşturduğunu gösterir, `ICustomerManager` hizmetle iletişim kurmak için bir kanal oluşturur ve müşteri nesnesini bu sunucuya gönderir.  
  
 Müşteri nesnesi serileştirilir ve hizmete gönderilir; burada hizmet tarafından bu nesnenin yeni bir kopyasına kaydedilir.  Bu nesne üzerindeki hizmet çağrılarının her türlü yöntemi yalnızca sunucuda yerel olarak yürütülür. Bu kodun türetilmiş bir türün (`PremiumCustomer`) gönderilmesini gösterdiğine dikkat edin.  Hizmet sözleşmesi bir `Customer` nesne bekler, ancak hizmet veri sözleşmesi de izin verildiğini belirtmek<xref:System.Runtime.Serialization.KnownTypeAttribute> `PremiumCustomer` için [] özniteliğini kullanır.  WCF, bu hizmet arabirimi aracılığıyla başka herhangi bir türü seri hale getirmeye veya seri durumdan çıkarmasına çalışır.  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>Hizmet, başvuruya göre bir nesne döndürüyor  
 Bu senaryo için, istemci uygulaması uzak hizmete bir çağrı yapar ve yöntemi hizmetten istemciye başvuru ile geçirilen bir nesne döndürür.  
  
 Daha önce belirtildiği gibi, WCF Hizmetleri nesneyi her zaman değere göre döndürür.  Ancak, <xref:System.ServiceModel.EndpointAddress10> sınıfını kullanarak benzer bir sonuç elde edebilirsiniz.  , <xref:System.ServiceModel.EndpointAddress10> İstemci tarafından sunucuda bir sessionby başvuruya göre nesne elde etmek için kullanılabilecek bir seri hale getirilebilir değer nesnesi.  
  
 Bu senaryoda gösterilen WCF 'deki başvuruya göre nesnesinin davranışı, DCOM 'dan farklıdır.  DCOM 'da, sunucu istemciye doğrudan başvuruya göre bir nesne döndürebilir ve istemci, sunucuda yürütülen bu nesnenin yöntemlerini çağırabilir.  Ancak, WCF 'de döndürülen nesne her zaman değeri ile belirlenir.  İstemci, tarafından <xref:System.ServiceModel.EndpointAddress10> temsil edilen ve kendi sessionby başvuru nesnesini oluşturmak için onu kullanarak bu nesne tarafından temsil etmelidir.  İstemci yöntemi, sunucuda yürütülen oturumsuz nesneye çağrı yapılır. Diğer bir deyişle, WCF 'deki bu başvuruya göre bu nesne, sessionmek üzere yapılandırılmış normal bir WCF hizmetidir.  
  
 WCF 'de oturum, iki uç nokta arasında gönderilen birden fazla iletiyi eş bir şekilde ilişkilendirme yöntemidir.  Bu, bir istemci bu hizmete bir bağlantı edinirse, istemci ile sunucu arasında bir oturum kurulacağı anlamına gelir.  İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafı nesnesinin tek bir benzersiz örneğini kullanır. Oturumsuz WCF sözleşmeleri, bağlantıya dayalı ağ isteği/yanıt desenlerine benzer.  
  
 Bu senaryo, aşağıdaki DCOM yöntemiyle temsil edilir.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>1. Adım: oturumsuz WCF hizmeti arabirimini ve uygulamasını tanımlama  
 İlk olarak, sessionobject nesnesini içeren bir WCF hizmeti arabirimi tanımlayın.  
  
 Bu kodda, sessionobject nesnesi onu normal bir WCF hizmeti arabirimi `ServiceContract` olarak tanımlayan özniteliğiyle işaretlenir.  Buna ek olarak, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği, bir sessionservice olacağını belirtecek şekilde ayarlanır.  
  
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
  
 Aşağıdaki kod, hizmet uygulamasını gösterir.  
  
 Hizmet, [ServiceBehavior] özniteliğiyle işaretlenir ve InstanceContextMode özelliği, her oturum için bu türün benzersiz bir örneğinin oluşturulması gerektiğini belirtmek için InstanceContextMode. PerSessions olarak ayarlanır.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>2. Adım: oturumsuz nesne için WCF fabrikası hizmetini tanımlama  
 Oturumsuz nesneyi oluşturan hizmetin tanımlanması ve uygulanması gerekir. Aşağıdaki kod bunun nasıl yapılacağını gösterir. Bu kod, bir <xref:System.ServiceModel.EndpointAddress10> nesne döndüren başka bir WCF hizmeti oluşturur.  Bu, oturum tam nesnesini oluşturmak için kullanabileceği bir uç noktanın seri hale getirilebilir bir biçimidir.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Bu hizmetin uygulanması aşağıda verilmiştir. Bu uygulama, oturumsuz nesneler oluşturmak için tek bir kanal fabrikası sağlar.  `GetInstanceAddress` Çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adrese <xref:System.ServiceModel.EndpointAddress10> işaret eden bir nesne oluşturur.   <xref:System.ServiceModel.EndpointAddress10>istemciye değere göre döndürülebilecek bir veri türüdür.
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>3. Adım: WCF hizmetlerini yapılandırma ve başlatma  
 Bu hizmetleri barındırmak için, sunucunun yapılandırma dosyasına (Web. config) aşağıdaki eklemeleri yapmanız gerekir.  
  
1. Oturumsuz `<client>` nesnenin bitiş noktasını açıklayan bir bölüm ekleyin.  Bu senaryoda, sunucu istemci olarak da çalışır ve bunu etkinleştirmek üzere yapılandırılması gerekir.  
  
2. `<services>` Bölümünde, fabrika ve oturumsuz nesne için hizmet uç noktalarını bildirin.  Bu, istemcinin hizmet uç noktaları ile iletişim kurmasını sağlar, alın <xref:System.ServiceModel.EndpointAddress10> ve Oturumsuz kanalı oluşturur.  
  
 Aşağıdaki ayarlara sahip örnek bir yapılandırma dosyası aşağıda verilmiştir:  
  
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
  
 Bir konsol uygulamasına, hizmeti kendinden barındırmak ve uygulamayı başlatmak için aşağıdaki satırları ekleyin.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>4. Adım: istemciyi yapılandırma ve hizmeti çağırma  
 İstemcisini, projenin uygulama yapılandırma dosyasında (App. config) aşağıdaki girişleri yaparak WCF hizmetleriyle iletişim kuracak şekilde yapılandırın.  
  
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
  
 Hizmeti çağırmak için, aşağıdakileri yapmak üzere istemciye kodu ekleyin:  
  
1. `ISessionBoundFactory` Hizmete bir kanal oluşturun.  
  
2. Bir `ISessionBoundFactory` <xref:System.ServiceModel.EndpointAddress10> nesne elde eden hizmeti çağırmak için kanalı kullanın.  
  
3. Oturumsuz <xref:System.ServiceModel.EndpointAddress10> bir nesne almak için bir kanal oluşturmak için kullanın.  
  
4. Ve yöntemlerini `SetCurrentValue` çağırarak `GetCurrentValue` , birden çok çağrıda aynı nesne örneğinin kullanıldığını göstermek için ve yöntemlerini çağırın.  
  
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
