---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: f1ff6d099ad0aee0c17b011000fe78f961293a82
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039769"
---
# <a name="dispatch-by-body-element"></a>Gövde Öğesine göre Dağıt
Bu örnek, işlemler için gelen iletileri atamaya yönelik alternatif algoritmanın nasıl uygulanacağını gösterir.  
  
 Varsayılan olarak, hizmet modeli dağıtıcısı iletinin WS-Addressing "Action" başlığına veya HTTP SOAP isteğindeki eşdeğer bilgilere göre gelen bir ileti için uygun işleme yöntemini seçer.  
  
 WS-ı temel 1,1 profilini izleyen bazı SOAP 1,1 Web Hizmetleri yığınları, Işlem URI 'sine bağlı olarak ileti göndermez, bunun yerine SOAP gövdesinin içindeki ilk öğenin XML nitelenmiş adına göre. Benzer şekilde, bu yığınların istemci tarafı, SOAP 1,1 belirtiminin izin verdiği boş veya rastgele bir HTTP SoapAction üst bilgisine sahip iletiler gönderebilir.  
  
 İletilerin yöntemlere nasıl dağıtıldığı şeklini değiştirmek için örnek <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> `DispatchByBodyElementOperationSelector`üzerinde genişletilebilirlik arabirimini uygular. Bu sınıf, ileti gövdesinin ilk öğesine göre işlemleri seçer.  
  
 Sınıf oluşturucusu, `XmlQualifiedName` ve dizeleri çiftleriyle doldurulmuş bir sözlük bekler ve nitelenmiş adların, SOAP gövdesinin ilk alt öğesinin adını ve dizeler eşleşen işlem adını gösterir. , `defaultOperationName` Bu sözlükte eşleştirilemez tüm iletileri alan işlemin adıdır:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>arabirim üzerinde yalnızca bir yöntem olduğundan, uygulamalar derleme için oldukça basittir: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Bu yöntemin işi, gelen bir iletiyi incelemek ve geçerli uç nokta için hizmet sözleşmesindeki bir yöntemin adına eşit olan bir dize döndürmek içindir.  
  
 Bu örnekte, işlem Seçici <xref:System.Xml.XmlDictionaryReader> , kullanarak <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>gelen iletinin gövdesini alır. Bu yöntem, geçerli öğenin adı ve ad alanı URI 'sini almak için yeterli olması ve daha sonra ilgili işlemi ' dan aramak için kullanılan bir `XmlQualifiedName` ile birleştirmek üzere ileti gövdesinin ilk alt öğesi için okuyucuyu zaten konumlandırır. işlem seçiciyle tutulan sözlük.  
  
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
  
 İleti gövdesine <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövde içeriğine erişim sağlayan diğer yöntemlerden birine erişmek iletinin "okuma" olarak işaretlenmesine neden olur, bu da iletinin daha fazla işlem için geçersiz olduğu anlamına gelir. Bu nedenle, işlem Seçicisi aşağıdaki kodda gösterilen yöntemiyle gelen iletinin bir kopyasını oluşturur. İnceleme sırasında okuyucunun konumu değişmediğinden, ileti özelliklerinin ve ileti üstbilgilerinin de kopyalandığı yeni oluşturulan ileti tarafından başvuru yapılabilir ve bu durum özgün iletinin tam bir kopyasına neden olur:  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a>Bir hizmete Işlem seçici ekleme  
 Hizmet gönderme işlemi seçicileri Windows Communication Foundation (WCF) dağıtıcısına yönelik uzantılardır. Çift yönlü sözleşmelerin geri çağırma kanalında Yöntemler seçmek için, burada açıklanan gönderme işlemi seçicileri gibi çok daha fazla çalışan ancak bu örnekte açıkça kapsanmayan istemci işlem seçicileri de vardır.  
  
 Çoğu hizmet modeli uzantısı gibi, dağıtım işlemi seçicileri, davranışlar kullanılarak dağıtıcıya eklenir. *Davranış* , dağıtım çalışma zamanına (veya istemci çalışma zamanına) bir veya daha fazla uzantı ekleyen veya ayarlarını değiştiren bir yapılandırma nesnesidir.  
  
 İşlem seçicileri sözleşme kapsamı içerdiğinden, burada uygulanacak uygun davranış ' dır <xref:System.ServiceModel.Description.IContractBehavior>. Aşağıdaki kodda gösterildiği gibi arabirim türetilmiş bir <xref:System.Attribute> sınıfta uygulandığından, davranış herhangi bir hizmet sözleşmesine bildirimli olarak eklenebilir. <xref:System.ServiceModel.ServiceHost> Her açıldığında ve dağıtım çalışma zamanı yapılandırıldığında, sözleşmeler, işlemler ve hizmet uygulamalarında öznitelik olarak bulunan ya da hizmet yapılandırmasındaki öğe olarak bulunan tüm davranışlar otomatik olarak eklenir ve daha sonra istenirse uzantılara katkıda bulunun veya varsayılan yapılandırmayı değiştirin.  
  
 Kısaltma için aşağıdaki kod alıntısı yalnızca yönteminin <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>uygulanmasını gösterir ve bu örnekteki dağıtıcı için yapılandırma değişikliklerini etkiler. Diğer yöntemler, hiçbir iş yapmadan arayan tarafa döntiğinden gösterilmez.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama, hizmet uç noktasındaki <xref:System.ServiceModel.Description.OperationDescription> <xref:System.ServiceModel.Description.ContractDescription>öğeler üzerinde yineleme yaparak, işlem seçicisinin arama sözlüğünü ayarlar. Ardından, her işlem açıklaması `DispatchBodyElementAttribute` davranışın varlığı için incelenir, bu örnekte de bir <xref:System.ServiceModel.Description.IOperationBehavior> uygulama da tanımlanır. Bu sınıf aynı zamanda bir davranış olsa da pasif olur ve dağıtım çalışma zamanında hiçbir yapılandırma değişikliğini etkin bir şekilde katkıda bulunmaz. Tüm yöntemleri herhangi bir eylem yapmadan çağırana döner. İşlem davranışı yalnızca yeni dağıtım mekanizması için gerekli olan meta verilerin, yani örneğin bir işlem yerine geçen gövde öğesinin tam adı seçildiğinde ilgili işlemlerle ilişkilendirilebilen şekilde bulunur.  
  
 Böyle bir davranış bulunursa, XML nitelenmiş adından (`QName` özellik) ve işlem adından (`Name` özellik) oluşturulan bir değer çifti sözlüğe eklenir.  
  
 Sözlük doldurulduktan sonra, bu bilgilerle yeni `DispatchByBodyElementOperationSelector` bir oluşturulur ve dağıtım çalışma zamanının işlem Seçicisi olarak ayarlanır:  
  
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
  
## <a name="implementing-the-service"></a>Hizmeti uygulama  
 Bu örnekte uygulanan davranış, hizmet sözleşmesinin bir işlevi olan, iletişimdeki iletilerin nasıl yorumlandığını ve yapıldığını doğrudan etkiler. Sonuç olarak, davranışı kullanmayı seçen hizmet uygulamalarında hizmet sözleşmesi düzeyinde bildirilmelidir.  
  
 `DispatchByBodyElementBehaviorAttribute` Örnek proje hizmeti, sözleşme davranışını `IDispatchedByBody` hizmet sözleşmesine uygular ve iki işlemin `OperationForBodyA()` her birini ve `OperationForBodyB()` bir `DispatchBodyElementAttribute` işlem davranışını Etiketler. Bu sözleşmeyi uygulayan bir hizmetin hizmet ana bilgisayarı açıldığında, bu meta veriler, daha önce açıklandığı gibi dağıtıcı Oluşturucusu tarafından alınır.  
  
 İşlem Seçici yalnızca ileti gövdesi öğesine bağlı olarak ve "eylem" öğesini yok saydığından, çalışma zamanına "*" joker karakterini "*" `ReplyAction` özelliğine atayarak döndürülen yanıtlara "eylem" üst bilgisini denetlemez şekilde söylemek gerekir <xref:System.ServiceModel.OperationContractAttribute>. Ayrıca, "\*" joker karakterine ayarlanmış "Action" özelliği olan bir varsayılan işlem olması gerekir. Varsayılan işlem, iletilemez ve ' a `DispatchBodyElementAttribute`sahip olmayan tüm iletileri alır:  
  
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
  
 Örnek hizmet uygulamasının kullanımı basittir. Her yöntem alınan iletiyi bir yanıt iletisine sarar ve istemciye geri bildirir.  
  
## <a name="running-and-building-the-sample"></a>Örnek çalıştırma ve oluşturma  
 Örneği çalıştırdığınızda, işlem yanıtlarının gövde içeriği, istemci konsolu penceresinde aşağıdaki (biçimlendirilen) çıktıya benzer şekilde görüntülenir.  
  
 İstemci, gövde içeriği öğesi sırasıyla, `bodyA` `bodyB`, ve `bodyX`olarak adlandırılan hizmete üç ileti gönderir. Önceki açıklamadan ve hizmet sözleşmesinden ertelenebilir, `bodyA` öğesine sahip gelen ileti `OperationForBodyA()` yöntemine gönderilir. `bodyX` Gövde öğesi olan ileti için açık bir dağıtım hedefi olmadığından ileti `DefaultOperation()`öğesine gönderilir. Hizmet işlemlerinin her biri, alınan ileti gövdesini yönteme özel bir öğeye sarar ve bu örnek için giriş ve çıkış iletilerini açıkça ilişkilendirmek için yapılır.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
