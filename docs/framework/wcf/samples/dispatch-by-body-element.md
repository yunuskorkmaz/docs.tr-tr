---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183720"
---
# <a name="dispatch-by-body-element"></a>Gövde Öğesine göre Dağıt
Bu örnek, gelen iletileri işlemlere atamak için alternatif bir algoritmanın nasıl uygulanacağını gösterir.  
  
 Varsayılan olarak, hizmet modeli gönderici, iletinin WS Adresleme "Eylem" üstbilgisini veya HTTP SOAP isteğindeki eşdeğer bilgileri temel alan gelen ileti için uygun işleme yöntemini seçer.  
  
 WS-I Temel Profil 1.1 yönergelerine uymayan bazı SOAP 1.1 Web hizmetleri yığınları, Action URI'ye dayalı iletiler göndermez, daha çok SOAP gövdesi içindeki ilk öğenin XML nitelikli adını temel eder. Aynı şekilde, bu yığınların istemci tarafı, SOAP 1.1 belirtimi tarafından izin verilen boş veya rasgele http SoapAction üstbilgisini içeren iletiler gönderebilir.  
  
 İletilerin yöntemlere gönderilme biçimini değiştirmek için, örnek. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> `DispatchByBodyElementOperationSelector` Bu sınıf, ileti gövdesinin ilk öğesini temel alan işlemleri seçer.  
  
 Sınıf oluşturucu, nitelikli adlar SOAP `XmlQualifiedName` gövdesinin ilk alt adını gösterir ve dizeleri eşleşen işlem adını gösterir, çiftleri ve dizeleri ile doldurulur bir sözlük bekliyor. Bu `defaultOperationName` sözlükle eşleştirilemeyen tüm iletileri alan işlemin adı:  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>arabirimde tek bir yöntem olduğu için uygulamalar oluşturmak <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>çok kolaydır: . Bu yöntemin işi, gelen bir iletiyi denetlemek ve geçerli bitiş noktası için hizmet sözleşmesinde bir yöntemin adı eşit bir dize döndürmektir.  
  
 Bu örnekte, işlem seçici kullanarak <xref:System.Xml.XmlDictionaryReader> <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>gelen iletinin gövdesi için bir elde eder. Bu yöntem zaten okuyucuyu iletinin gövdesinin ilk çocuğuna konumlandırır, böylece geçerli öğenin adını ve ad alanı `XmlQualifiedName` URI'yi almak ve bunları işlem seçicitarafından tutulan sözlükten karşılık gelen işlemi aramak için kullanılan bir şekilde birleştirmek yeterlidir.  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 İleti gövdesine <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövde içeriğine erişim sağlayan diğer yöntemlerden herhangi biriyle erişmek, iletinin "okundu" olarak işaretlenmesine neden olur, bu da iletinin başka bir işlem için geçersiz olduğu anlamına gelir. Bu nedenle, işlem seçici aşağıdaki kodda gösterilen yöntemle gelen iletinin bir kopyasını oluşturur. Denetim sırasında okuyucunun konumu değiştirilmedığından, ileti özelliklerinin ve ileti üstbilgilerinin de kopyalandığı yeni oluşturulan iletiyle başvurulabilir ve bu da özgün iletinin tam bir klonu ile sonuçlanır:  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Hizmete İşlem Seçici Ekleme  
 Servis gönderme işlemi seçicileri, Windows Communication Foundation (WCF) göndericisinin uzantılarıdır. Çift yönlü sözleşmelerin geri arama kanalında yöntemleri seçmek için, burada açıklanan gönderme işlemi seçicilerine çok benzeyen, ancak bu örnekte açıkça kapsanmayan istemci işlem seçicileri de vardır.  
  
 Çoğu hizmet modeli uzantıları gibi, sevkiyat işlemi seçicileri de davranışları kullanarak sevk irsaliyesine eklenir. *Davranış,* sevk çalışma süresine (veya istemci çalışma süresine) bir veya daha fazla uzantı ekleyen veya ayarlarını başka şekilde değiştiren bir yapılandırma nesnesidir.  
  
 İşlem seçicileri sözleşme kapsamına sahip olduğundan, burada <xref:System.ServiceModel.Description.IContractBehavior>uygulanacak uygun davranış . Arabirim, aşağıdaki kodda <xref:System.Attribute> gösterildiği gibi türetilmiş bir sınıfüzerinde uygulandığından, davranış bildirimolarak herhangi bir hizmet sözleşmesine eklenebilir. A <xref:System.ServiceModel.ServiceHost> açıldığında ve sevk çalışma zamanı oluşturulsa, sözleşmelerde, işlemlerde ve hizmet uygulamalarında öznitelikler olarak veya hizmet yapılandırmasındaki öğe olarak bulunan tüm davranışlar otomatik olarak eklenir ve daha sonra uzantılara katkıda bulunmaları veya varsayılan yapılandırmayı değiştirmeleri istenir.  
  
 Kısaltma için, aşağıdaki kod alıntısı yalnızca bu <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>örnekteki sevkiyatçının yapılandırma değişikliklerini etkileyen yöntemin uygulanmasını gösterir. Diğer yöntemler gösterilmez, çünkü herhangi bir çalışma yapmadan arayanın geri dönmesine neden olurlar.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama, hizmet bitiş noktasının <xref:System.ServiceModel.Description.OperationDescription> öğeleri üzerinde yineleyerek işlem seçici için arama <xref:System.ServiceModel.Description.ContractDescription>sözlüğü ayarlar. Daha sonra, her işlem açıklaması `DispatchBodyElementAttribute` davranışın varlığı için <xref:System.ServiceModel.Description.IOperationBehavior> denetlenir, bu örnekte de tanımlanan bir uygulama. Bu sınıf aynı zamanda bir davranış olsa da, pasiftir ve sevkiyat çalışma süresine etkin olarak yapılandırma değişiklikleri sağlamaz. Tüm yöntemleri herhangi bir işlem yapmadan arayanın geri döner. İşlem davranışı yalnızca, yeni sevkiyat mekanizması için gerekli meta verilerin, yani bir işlemin oluşumunun seçildiği gövde öğesinin nitelikli adı, ilgili işlemlerle ilişkilendirilebilsin diye vardır.  
  
 Böyle bir davranış bulunursa, XML nitelikli adından`QName` (özellik) oluşturulan`Name` bir değer çifti ve işlem adı (özellik) sözlüğe eklenir.  
  
 Sözlük dolduruldıktan sonra, bu `DispatchByBodyElementOperationSelector` bilgilerle yeni bir yapı oluşturulur ve sevk çalışma zamanının işlem seçicisi olarak ayarlanır:  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>Hizmetin Uygulanması  
 Bu örnekte uygulanan davranış, doğrudan kablodan gelen iletilerin nasıl yorumlandığını ve gönderildiğini etkiler, bu da hizmet sözleşmesinin bir işlevidir. Sonuç olarak, davranışı kullanmayı seçen herhangi bir hizmet uygulamasında hizmet sözleşmesi düzeyinde bildirilmelidir.  
  
 Örnek proje hizmeti, `DispatchByBodyElementBehaviorAttribute` sözleşme davranışını `IDispatchedByBody` hizmet sözleşmesine uygular ve `OperationForBodyA()` `OperationForBodyB()` her `DispatchBodyElementAttribute` iki işlemi ve bir işlem davranışını etiketler. Bu sözleşmeyi uygulayan bir hizmetin hizmet ana bilgisayarı açıldığında, bu meta veriler daha önce açıklandığı gibi gönderen oluşturucu tarafından alınır.  
  
 İşlem seçici yalnızca ileti gövdesi öğesine göre gönderip "Eylem"i yok saydığından, döndürülen yanıtlardaki "Eylem" üstbilgisini özelliğine "*" `ReplyAction` joker karakter atayarak denetlemememi için çalışma zamanı nın belirtilmesi <xref:System.ServiceModel.OperationContractAttribute>gerekir. Ayrıca, joker "\*"" olarak ayarlanmış "Eylem" özelliğine sahip varsayılan bir işlem olması gerekir. Varsayılan işlem, gönderilmeyen ve şu `DispatchBodyElementAttribute`gibi olmayan tüm iletileri alır:  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 Örnek hizmet uygulaması basittir. Her yöntem alınan iletiyi bir yanıt iletisine sarar ve istemciye geri döndürer.  
  
## <a name="running-and-building-the-sample"></a>Numunenin Çalıştırılve Yapılmı  
 Örneği çalıştırdığınızda, işlem yanıtlarının gövde içeriği istemci konsol penceresinde aşağıdaki (biçimlendirilmiş) çıktıya benzer şekilde görüntülenir.  
  
 İstemci, gövde içeriği öğesi adı `bodyA` `bodyB`,, ve `bodyX`, sırasıyla adlı hizmete üç ileti gönderir. Önceki açıklama ve gösterilen hizmet sözleşmesinden ertelenebileceği gibi, `bodyA` öğeyle gelen ileti `OperationForBodyA()` yönteme gönderilir. `bodyX` Gövde öğesi ile ileti için açık bir gönderme hedefi olmadığından, ileti `DefaultOperation()`. Hizmet işlemlerinin her biri alınan ileti gövdesini yönteme özgü bir öğeye sarar ve bu örnek için giriş ve çıktı iletilerini açıkça ilişkilendirmek için yapılan iletileri döndürür:  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
