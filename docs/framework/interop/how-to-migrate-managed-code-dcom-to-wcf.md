---
title: 'Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fad8a73c41379cac7523db6266951b8abab26e27
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626289"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme
Windows Communication Foundation (WCF) önerilen ve güvenli Dağıtılmış Bileşen Nesne Modeli (DCOM) üzerinden sunucular ve istemciler dağıtılmış bir ortamda arasındaki çağrıların yönetilen kod için seçimdir. Bu makale nasıl kod DCOM'dan WCF'ye aşağıdaki senaryolar için geçirme için.  
  
- Uzak Hizmet, bir nesneyi değere göre istemciye döndürür.  
  
- İstemci bir nesneyi değere göre uzak hizmetine gönderir.  
  
- Uzak Hizmet, bir nesne başvuru tarafından istemciye döndürür.  
  
 Güvenlik nedeniyle, bir nesne başvuruya göre istemciden hizmete gönderme WCF'de izin verilmez. İstemci ve sunucu arasında sürekli bir konuşma gerektiren bir senaryo, bir çift yönlü hizmet kullanarak WCF'de gerçekleştirilebilir.  Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 WCF hizmetleri ve istemciler için bu hizmetleri oluşturma hakkında daha fazla ayrıntı için bkz. [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md), [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [istemci derleme](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>DCOM örnek kod  
 Bu senaryolar için WCF kullanan gösterilmiştir DCOM arabirimleri aşağıdaki yapıya sahiptir:  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Hizmet bir nesne tarafından değeri döndürür.  
 Bu senaryo için bir değere göre istemcinin sunucudan geçirilen nesneye yöntemi döndürür ve bir hizmeti çağrı yapmak. Bu senaryo, COM çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 Bu senaryoda, istemci uzak hizmetten bir nesneyi seri durumdan çıkarılmış bir kopyasını alır. İstemci hizmete geri çağırmaya gerek kalmadan bu yerel bir kopya ile etkileşim kurabilir.  Diğer bir deyişle, istemci yerel kopya yöntemler çağrıldığında hizmeti herhangi bir yolla dahil olacaktır değil garanti edilir. Aşağıdaki adımlar, normal bir WCF hizmeti oluşturma açıklar. Bu nedenle WCF her zaman nesneleri hizmetten değere göre döndürür.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>1. Adım: WCF hizmet arabirimi tanımlayın  
 WCF hizmeti için ortak bir arabirim tanımlayın ve kendisiyle işaretlemek [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliği.  İstemciler için kullanıma sunmak istediğiniz yöntemlerini işaretlemek [<xref:System.ServiceModel.OperationContractAttribute>] özniteliği. Aşağıdaki örnek, bir istemci çağırabilirsiniz arabirim yöntemleri ve sunucu tarafı arabirimi tanımlamak için bu öznitelikler kullanarak gösterir. Bu senaryo için kullanılan yöntem kalın olarak gösterilir.  
  
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
  
### <a name="step-2-define-the-data-contract"></a>2. Adım: Veri sözleşmesi tanımlayın  
 Ardından, nasıl veri hizmet ve istemcileri arasında değiş tokuş anlatmaktadır hizmeti için bir veri sözleşmesi oluşturmanız gerekir.  Veri sözleşmede açıklanan sınıfları ile işaretlenmemelidir [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliği. Hem istemci hem de sunucu görünür istediğiniz alanlar ve özellikler ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliği. Türetilen bir sınıfta izin verilmesi için veri anlaşması türleri istiyorsanız tanımlamalıdır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliği. WCF yalnızca serileştirmek veya hizmet arabirimi türlerinde ve bilinen türleri olarak tanımlanan türler seri durumdan. Bilinen bir tür değil bir tür kullanmayı denerseniz, bir özel durum oluşur.  
  
 Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [veri sözleşmeleri](../../../docs/framework/wcf/samples/data-contracts.md).  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a>3. Adım: WCF hizmet ekleme  
 Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmet sınıfı uygulamalıdır.  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>4. Adım: Hizmet ve istemci yapılandırma  
 Bir WCF hizmeti çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL'den bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmeniz gerekir. Bağlama istemciler ve sunucu iletişim kurmak için taşıma, kodlama ve protokolü ayrıntılarını belirtir. Genellikle hizmet projesinin yapılandırma dosyasında (web.config) bağlamaları ekleyin. Aşağıdaki örnek hizmeti için bir bağlayıcı giriş gösterir:  
  
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
  
 Ardından, hizmet tarafından belirtilen bağlama bilgileri eşleşecek şekilde istemciyi yapılandırmak gerekir. Bunu yapmak için istemci uygulama yapılandırma (app.config) dosyasına aşağıdakileri ekleyin.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>5. Adım: Hizmet çalıştırma  
 Son olarak, bunu bir konsol uygulamasında aşağıdaki satırları hizmet uygulamasına ekleme ve uygulama başlatma Self barındırabilirsiniz. Bir WCF Hizmeti uygulamasını barındırmak için kullanabileceğiniz diğer yöntemler hakkında daha fazla bilgi için [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>6. Adım: Hizmet istemciden çağırın  
 İstemciden hizmeti çağırmak için hizmeti için kanal fabrikası oluşturma ve doğrudan çağırmak sağlayacak bir kanal istek gerekir `GetCustomer` yöntemi doğrudan istemci. Kanal, hizmetin arabirimi uygulayan ve temel alınan istek/yanıt mantığını sizin yerinize çözer.  Bu yöntem çağrısının dönüş değerini hizmet yanıt seri durumdan çıkarılmış kopyasıdır.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>İstemci bir değere göre nesne sunucuya gönderir.  
 Bu senaryoda, bir nesneye sunucuya istemci gönderir değere göre. Bu, sunucu nesne seri durumdan çıkarılmış bir kopyasını aldığından anlamına gelir.  Sunucu üzerinde bu kopyayı yöntemleri çağırabilir ve istemci koda hiçbir geri çağırma yok garanti. Daha önce belirtildiği gibi normal WCF değişimleri veri değere göre ' dir.  Bu garanti Bu nesnelerden birini metotları çağırma yerel olarak yalnızca yürütür – istemci kodu çağırma kullanılamaz.  
  
 Bu senaryo aşağıdaki COM yöntem çağrısını temsil eder:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır. Ayrıca, hizmet ve istemci aynı şekilde yapılandırılır. Bu örnekte, nesne gönderin ve aynı şekilde çalıştırmak için bir kanal oluşturulur. Ancak, bu örnekte, bir nesneyi değere göre geçirme hizmetini çağıran bir istemci oluşturacaksınız. İstemci hizmet sözleşmesindeki çağıracak hizmet yöntemi kalın olarak gösterilir:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Değere göre nesne gönderen istemciye kod ekleyin  
 Aşağıdaki kodun gösterdiği istemci yeni bir değere göre müşteri nesnesi oluşturur nasıl ile iletişim kurmak için bir kanal oluşturur `ICustomerManager` hizmet ve müşteri nesnesi için gönderir.  
  
 Müşteri nesnesi seri hale getirilmiş ve burada, hizmet tarafından bu nesne yeni bir kopyasını seri durumda hizmetine gönderilir.  Hizmetine çağrı yapan, bu nesne üzerinde herhangi bir yöntem yalnızca yerel olarak yürütülür sunucusunda. Bu kod gönderme türetilmiş bir türü göstermektedir dikkat edin önemlidir (`PremiumCustomer`).  Hizmet sözleşmesi bekliyor bir `Customer` nesne, ancak hizmet veri sözleşme kullanır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] belirtmek için özniteliği `PremiumCustomer` da izin verilir.  WCF serileştirmek veya bu hizmet arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>Hizmet başvuruya göre bir nesne döndürür.  
 Bu senaryo için istemci uygulaması uzak hizmet çağrıda bulunur ve istemci hizmeti başvuru tarafından geçirilen nesneyi yöntemi döndürür.  
  
 Daha önce belirtildiği gibi WCF hizmetleri değere göre her zaman nesnesi döndürür.  Ancak, kullanarak benzer bir sonuç elde edebileceğiniz <xref:System.ServiceModel.EndpointAddress10> sınıfı.  <xref:System.ServiceModel.EndpointAddress10> Sunucuda kapatamaması başvuru tarafından nesnesini almak için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir.  
  
 Bu senaryoda gösterildiği WCF başvuruya göre nesnesinde davranışını DCOM farklıdır.  DCOM, sunucunun bir başvuruya göre nesne istemciye doğrudan döndürebilir ve istemcinin sunucuda yürütülür nesnenin yöntemleri çağırabilir.  WCF'de, ancak döndürülen nesne olduğundan her zaman değere göre.  İstemci tarafından temsil edilen bu değere göre nesne almalıdır <xref:System.ServiceModel.EndpointAddress10> ve kendi başvuru tarafından kapatamaması nesnesi oluşturmak için bunu kullanın.  İstemci yöntem çağrılarını kapatamaması nesnesindeki sunucuda yürütülür. Diğer bir deyişle, bu başvuruya göre wcf'de kapatamaması olacak şekilde yapılandırıldığında normal bir WCF Hizmeti nesnedir.  
  
 WCF'de, oturum, birden çok ileti iki uç nokta arasında gönderilen ilişkilendirme bir yoludur.  Bu, istemci bu hizmet için bir bağlantı alır, sonra oturumu istemci ve sunucu arasında kurulur, anlamına gelir.  İstemci bu oturumla içinde için tüm etkileşimler bir tek benzersiz bir sunucu tarafı nesne örneği kullanın. Ağ bağlantısı yönelik istek/yanıt desenlerini kapatamaması WCF sözleşmeleri benzerdir.  
  
 Bu senaryo aşağıdaki DCOM yöntemi tarafından temsil edilir.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>1. Adım: Uygulama ve Sessionful WCF hizmet arabirimi tanımlayın  
 İlk olarak, kapatamaması nesne içeren bir WCF Hizmeti arabirimi tanımlayın.  
  
 Bu kodda kapatamaması nesne ile işaretlenmiş `ServiceContract` özniteliği normal bir WCF Hizmeti arabirimi tanımlar.  Ayrıca, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği kapatamaması hizmet olacaktır belirtmek için ayarlanır.  
  
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
  
 Hizmet [ServiceBehavior] özniteliği ile işaretli ve her oturum için benzersiz bir örnek bu türde oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions için kendi InstanceContextMode özelliğini ayarlayın.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>2. Adım: WCF factory hizmeti kapatamaması nesnesi tanımlayın  
 Kapatamaması nesnesini oluşturan hizmet tanımlı ve uygulanan gerekir. Aşağıdaki kod, bunun nasıl yapılacağını gösterir. Veren başka bir WCF hizmeti bu kod oluşturur bir <xref:System.ServiceModel.EndpointAddress10> nesne.  Bu bir uç nokta can seri hale getirilebilir bir tür, tam oturum nesnesi oluşturmak için kullanın.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Aşağıda, bu hizmet uygulamasıdır. Bu uygulama kapatamaması nesneleri oluşturmak için singleton kanal fabrikası tutar.  Zaman `GetInstanceAddress` olan çağrılır, bir kanal oluşturur ve oluşturur bir <xref:System.ServiceModel.EndpointAddress10> bu kanal ile ilişkili uzak adresini işaret eden bir nesne.   <xref:System.ServiceModel.EndpointAddress10> İstemci tarafından değeri olarak döndürülebilecek bir veri türü var.  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>3. Adım: Yapılandırma ve WCF hizmetlerini başlatma  
 Bu hizmetler barındırmak için sunucu yapılandırma dosyasında (web.config) aşağıdaki eklemeler olmanız gerekir.  
  
1. Ekleme bir `<client>` kapatamaması nesne için uç nokta açıklayan bölümü.  Bu senaryoda, sunucu da bir istemci olarak davranır ve bu ayarı etkinleştirmek için yapılandırılması gerekir.  
  
2. İçinde `<services>` bölümünde, Fabrika ve sessionful nesne için hizmet uç noktalarını bildirir.  Bu hizmet uç noktaları ile iletişim kurmak, almak istemci sağlar <xref:System.ServiceModel.EndpointAddress10> ve oturum kanalı oluşturun.  
  
 Bu ayarlarla örnek bir yapılandırma dosyası aşağıda verilmiştir:  
  
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
  
 Barındırılan hizmet için bir konsol uygulaması için aşağıdaki satırları ekleyin ve uygulamayı başlatın.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>4. Adım: İstemciyi yapılandırma ve hizmet çağrısı  
 Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girdileri yaparak WCF hizmetleri ile iletişim kuracak istemci yapılandırın.  
  
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
  
 Hizmeti çağırmak için aşağıdakileri yapmak için istemci kodu ekleyin:  
  
1. Bir kanal oluşturmaya `ISessionBoundFactory` hizmeti.  
  
2. Çağrılacak kanalı kullanmaya `ISessionBoundFactory` elde bir hizmet bir <xref:System.ServiceModel.EndpointAddress10> nesne.  
  
3. Kullanım <xref:System.ServiceModel.EndpointAddress10> kapatamaması bir nesne elde etmek için bir kanal oluşturmak için.  
  
4. Çağrı `SetCurrentValue` ve `GetCurrentValue` arasında birden çok çağrı yöntemleri aynı nesne örneği kaldığı göstermek için kullanılır.  
  
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

- [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Hizmetleri Tasarlama ve Uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [İstemci Derleme](../../../docs/framework/wcf/building-clients.md)
- [Çift Yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md)
