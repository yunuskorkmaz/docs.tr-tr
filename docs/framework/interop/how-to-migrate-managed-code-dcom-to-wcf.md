---
title: "Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d97a7d855d6c5ccd0545d8bf95ebe7bcece88656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme
Windows Communication Foundation (WCF), güvenli ve önerilen seçenek yönetilen kod çağrıları sunucular ve istemciler dağıtılmış bir ortama arasında Dağıtılmış Bileşen Nesne Modeli (DCOM) üzerinden içindir. Bu makalede gösterilmektedir nasıl kod DCOM'dan WCF'ye aşağıdaki senaryolar için geçirme için.  
  
-   Uzak Hizmet istemciye bir nesne tarafından-değeri döndürür  
  
-   İstemci bir nesne tarafından-değeri uzak hizmetine gönderir.  
  
-   Uzak Hizmet bir nesne başvuru tarafından istemciye döndürür.  
  
 Güvenlik nedeniyle, bir nesne başvuru tarafından istemciden hizmete gönderme WCF içinde izin verilmiyor. İstemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo çift yönlü hizmetini kullanarak WCF'de elde edilebilir.  Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 WCF hizmetleri ve istemciler bu hizmetlerin oluşturma hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md), [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [istemci derleme](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>DCOM örnek kod  
 Bu senaryolarda, WCF kullanarak gösterilmiştir DCOM arabirimleri aşağıdaki yapı ayarlanmıştır:  
  
```  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Hizmet bir nesne tarafından-değeri döndürür  
 Bu senaryo için bir değer tarafından sunucudan istemciye geçirilir nesne yöntemi döndürür ve bir hizmet için bir çağrı olun. Bu senaryo aşağıdaki COM çağrısını temsil eder:  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 Bu senaryoda, istemci uzak hizmetinden bir nesne seri durumdan çıkarılmış bir kopyasını alır. İstemci hizmete geri çağırma olmadan bu yerel bir kopya ile etkileşim kurabilirsiniz.  Diğer bir deyişle, istemci yerel kopya yöntemler çağrıldığında hizmet herhangi bir şekilde dahil olacaktır değil garanti edilmez. Aşağıdaki adımlar, normal bir WCF hizmeti oluşturma açıklamaktadır şekilde WCF her zaman nesneleri hizmetinden değere göre döndürür.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>1. adım: WCF Hizmeti arabirimi tanımlama  
 WCF hizmeti için ortak bir arabirim tanımlayın ve ile işaretleyin [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliği.  İstemcilerle kullanıma sunmak istediğiniz yöntemleri işaretleme [<xref:System.ServiceModel.OperationContractAttribute>] özniteliği. Aşağıdaki örnek, bir istemci çağırabilirsiniz arabirim yöntemleri ve sunucu tarafı arabirimi tanımlamak için bu öznitelikleri kullanma gösterir. Bu senaryo için kullanılan yöntem kalın olarak gösterilir.  
  
```  
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
  
### <a name="step-2-define-the-data-contract"></a>2. adım: veri sözleşmesi tanımlayın  
 Sonraki nasıl veri hizmet ve istemcileri arasında alınıp verilecek anlatmaktadır hizmeti için bir veri sözleşmesi oluşturmanız gerekir.  Veri sözleşmesi açıklanan sınıflar ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliği. Tek tek özellikleri veya hem istemci hem de sunucu görünür istediğiniz alanları ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliği. İzin verilmesi için veri sözleşmesindeki sınıfından türetilmiş türler istiyorsanız tanımlamalıdır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliği. WCF yalnızca serileştirmek veya hizmet arayüzündeki türleri ve bilinen türleri olarak tanımlanan türler seri durumdan. Bilinen bir türe sahip olmayan bir tür kullanmayı denerseniz, bir özel durum meydana gelir.  
  
 Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [veri sözleşmeleri](../../../docs/framework/wcf/samples/data-contracts.md).  
  
```  
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
  
### <a name="step-3-implement-the-wcf-service"></a>3. adım: WCF Hizmeti uygulama  
 Ardından, önceki adımda tanımlanan arabirimini uygulayan WCF hizmet sınıfı uygulamanız gerekir.  
  
```  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>4. adım: hizmet ve istemci yapılandırma  
 Bir WCF hizmetini çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL, bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmeniz gerekir. Bağlama istemciler ve sunucu iletişim kurmak Aktarım, kodlama ve protokol ayrıntılarını belirtir. Genellikle hizmet projesinin yapılandırma dosyasında (web.config) bağlamaları ekleyin. Aşağıdaki örnek hizmeti için bir bağlama girişi gösterir:  
  
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
  
 Ardından, istemci hizmeti tarafından belirtilen bağlama bilgileri eşleşecek şekilde yapılandırmanız gerekir. Bunu yapmak için aşağıdaki istemci uygulaması (app.config) yapılandırma dosyasına ekleyin.  
  
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
  
### <a name="step-5-run-the-service"></a>5. adım: hizmet çalıştırma  
 Son olarak, bunu bir konsol uygulamasında aşağıdaki satırları hizmet uygulamasına ekleme ve uygulama başlatma Self barındırabilir. Bir WCF Hizmeti uygulamasını barındırmak için diğer yolları hakkında daha fazla bilgi için [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>6. adım: hizmet istemciden çağırın.  
 Hizmeti istemciden çağırmak için bir kanal fabrikası hizmeti oluşturmanız ve doğrudan çağırmak sağlayacak bir kanal istemek için gereken `GetCustomer` doğrudan istemciden yöntemi. Kanal hizmetin arabirimini uygulayan ve temel alınan istek/yanıt mantığı işler.  Bu yöntem çağrısının dönüş değerini, hizmet yanıtı seri durumdan çıkarılmış kopyasıdır.  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>İstemci bir değer tarafından nesnesi sunucuya gönderir.  
 Bu senaryoda, bir nesneye sunucuya istemci gönderir tarafından değeri. Bu, sunucunun nesne seri durumdan çıkarılmış bir kopyasını alacak anlamına gelir.  Sunucu yöntemleri Bu kopyada çağırabilir ve istemci koda hiçbir geri çağırma olduğu garanti. Daha önce belirtildiği gibi verileri normal WCF alışverişleri değer tarafından şunlardır.  Bu garanti Bu nesnelerden birini yöntemleri çağırma yerel olarak yalnızca yürütür – istemci kodu çağırma kullanılamaz.  
  
 Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır. Ayrıca, istemci ve hizmet aynı şekilde yapılandırılır. Bu örnekte, nesne göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur. Ancak, bu örnekte, bir nesne tarafından-değeri geçirme hizmeti çağıran bir istemci oluşturur. İstemci hizmet sözleşmesinde çağıracak hizmet yöntemi kalın olarak gösterilir:  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Bir değer tarafından nesnesi gönderir istemci kodu ekleyin  
 Aşağıdaki kod gösterdiği istemci yeni bir değer tarafından müşteri nesnesi oluşturur nasıl ile iletişim kurmak için bir kanal oluşturur `ICustomerManager` hizmet ve müşteri nesnesi gönderir.  
  
 Müşteri nesnesi seri hale getirilmiş ve burada bu hizmet tarafından söz konusu nesne yeni bir kopyasını seri durumdan olan hizmete gönderilen.  Hizmet çağrıları bu nesne üzerinde herhangi bir yöntem yalnızca yerel olarak yürütecek sunucusunda. Bu kod türetilmiş bir tür gönderme gösterir dikkate almak önemlidir (`PremiumCustomer`).  Hizmet sözleşmesi bekliyor bir `Customer` nesne ancak hizmet verileri sözleşme kullanır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliğini belirtmek için `PremiumCustomer` de izin verilir.  WCF serileştirmek veya bu hizmeti arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.  
  
```  
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
  
## <a name="the-service-returns-an-object-by-reference"></a>Hizmet başvuruya göre bir nesne döndürür  
 Bu senaryo için istemci uygulaması uzak hizmet için bir çağrı yapar ve yöntem başvuru hizmetinden istemci tarafından geçirilen bir nesne döndürür.  
  
 Daha önce belirtildiği gibi WCF hizmetleri zaman nesnesi tarafından dönüş değeri.  Ancak, kullanarak benzer bir sonuç elde edebilirsiniz <xref:System.ServiceModel.EndpointAddress10> sınıfı.  <xref:System.ServiceModel.EndpointAddress10> Sunucuda süre sonuyla başvuru tarafından nesnesi edinmek için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir.  
  
 Bu senaryoda gösterildiği WCF tarafından başvuru nesnesinde davranışını DCOM farklıdır.  DCOM, sunucu tarafından başvuru nesnesi istemciye doğrudan döndürebilir ve istemci sunucuda yürütmek o nesnenin yöntemleri çağırabilirsiniz.  WCF'de, ancak döndürülen nesne olduğundan her zaman tarafından-değeri.  İstemci tarafından temsil edilen bu değer tarafından nesnesi almalıdır <xref:System.ServiceModel.EndpointAddress10> ve kendi süre sonuyla başvuru tarafından nesnesi oluşturmak için kullanabilirsiniz.  İstemci yöntem çağrılarını süre sonuyla nesnesinde sunucuda yürütün. Diğer bir deyişle, bu başvuru tarafından WCF süre sonuyla olacak şekilde yapılandırıldığında normal bir WCF Hizmeti nesnedir.  
  
 WCF'de, bir oturum iki uç noktaları arasında gönderilen birden fazla ileti bağıntı bir yoludur.  Bu, bir istemci bu hizmet için bir bağlantı alır sonra bir oturum istemci ve sunucu arasında kurulacak olduğunu anlamına gelir.  İstemci bu tek oturum içinde kendi etkileşimler için sunucu tarafı nesnesi tek bir benzersiz örneğini kullanın. Süre sonuyla WCF sözleşmeleri bağlantı odaklı ağ istek/yanıt desenlerini benzerdir.  
  
 Bu senaryo aşağıdaki DCOM yöntemi tarafından temsil edilir.  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>1. adım: uygulama ve Sessionful WCF Hizmeti arabirimi tanımlayın  
 İlk olarak, süre sonuyla nesnesini içeren bir WCF Hizmeti arabirimi tanımlayın.  
  
 Bu kodda süre sonuyla nesnesi ile işaretlenen `ServiceContract` normal bir WCF Hizmeti arabirimi tanımlayan özniteliği.  Ayrıca, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği süre sonuyla bir hizmet olarak göstermek için ayarlanır.  
  
```  
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
  
 Hizmet [ServiceBehavior] özniteliğiyle işaretlenmiş ve bu tür benzersiz bir örnek her oturum için oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions için kendi InstanceContextMode özelliğini ayarlayın.  
  
```  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>2. adım: süre sonuyla nesnesi için WCF Fabrika hizmeti tanımlayın  
 Süre sonuyla nesnesi oluşturur hizmet tanımlı ve uygulanması gerekir. Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir. Bu kod döndürür başka bir WCF Hizmeti oluşturur bir <xref:System.ServiceModel.EndpointAddress10> nesnesi.  Bu seri hale getirilebilir bir uç nokta can biçimidir oturum tam nesnesi oluşturmak için kullanın.  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Bu hizmet uygulaması aşağıdadır. Bu uygulama süre sonuyla nesneleri oluşturmak için bir singleton kanal fabrikası tutar.  Zaman `GetInstanceAddress` olan adlı bir kanal oluşturur ve oluşturur bir <xref:System.ServiceModel.EndpointAddress10> bu kanal ile ilişkili uzak adresine işaret eden nesne.   <xref:System.ServiceModel.EndpointAddress10>İstemci tarafından değerinin döndürülen bir veri türüdür.  
  
```  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Adım 3: Yapılandırma ve WCF hizmetlerini başlatın  
 Bu hizmetler barındırmak için sunucu yapılandırma dosyasında (web.config) aşağıdaki eklemeler yapmak gerekir.  
  
1.  Ekleme bir `<client>` süre sonuyla nesne için uç noktaya açıklayan bölümü.  Bu senaryoda, sunucu da bir istemci olarak davranır ve bu ayarı etkinleştirmek için yapılandırılması gerekir.  
  
2.  İçinde `<services>` bölümünde, hizmet uç noktaları Fabrika ve sessionful nesnesinin bildirin.  Bu hizmet uç noktaları ile iletişim kurmak için alma istemci sağlar <xref:System.ServiceModel.EndpointAddress10> ve süre sonuyla kanal oluşturun.  
  
 Bu ayarlarla örnek bir yapılandırma dosyası aşağıdadır:  
  
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
  
 Self Servis barındırmak için bir konsol uygulaması için aşağıdaki satırları ekleyin ve uygulamayı başlatın.  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>4. adım: istemciyi Yapılandırma ve hizmet çağırın  
 Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girdileri yaparak WCF hizmetleri ile iletişim kurmak için istemci yapılandırın.  
  
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
  
 Hizmetini çağırmak için aşağıdakileri yapmak için istemci kodu ekleyin:  
  
1.  Bir kanal oluşturmak `ISessionBoundFactory` hizmet.  
  
2.  Çağrılacak kanalı kullanmaya `ISessionBoundFactory` bir elde hizmet bir <xref:System.ServiceModel.EndpointAddress10> bbject.  
  
3.  Kullanım <xref:System.ServiceModel.EndpointAddress10> bir süre sonuyla nesnesi elde etmek için bir kanal oluşturmak için.  
  
4.  Çağrı `SetCurrentValue` ve `GetCurrentValue` aynı nesne örneğini kaldığı göstermek için yöntemleri arasında birden fazla çağrı kullanılır.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Hizmetleri Tasarlama ve Uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [İstemci Derleme](../../../docs/framework/wcf/building-clients.md)  
 [Çift Yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md)
