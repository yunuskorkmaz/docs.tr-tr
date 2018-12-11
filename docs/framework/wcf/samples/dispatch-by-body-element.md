---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 58d505770a495e5e423104b9fb912d088ca56f86
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143167"
---
# <a name="dispatch-by-body-element"></a>Gövde Öğesine göre Dağıt
Bu örnek nasıl gelen iletiler için işlemler atamak için başka bir algoritma uygulanacağını gösterir.  
  
 Varsayılan olarak, hizmet modeli dağıtıcı iletinin WS-Addressing üzerinde temel gelen ileti için uygun işleme yöntemi seçer "Action" üst bilgi veya HTTP SOAP isteğinin eşdeğer bilgileri.  
  
 WS izlemeyin yığınları bazı SOAP 1.1 Web Hizmetleri-ı Basic Profile 1.1 yönergeleri eylem URİ'SİNDE dayalı ancak bunun yerine SOAP gövdesi içindeki ilk öğeyi XML tam adı temel iletileri gönderme değil. Benzer şekilde, istemci tarafı bu yığınlarının SOAP 1.1 belirtiminde verilmişti bir boş veya rastgele HTTP SoapAction başlık iletileri gönderebilir.  
  
 Yöntemlere iletileri gönderilen şeklini değiştirmek için örnek uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> genişletilebilirlik arabirimdeki `DispatchByBodyElementOperationSelector`. Bu sınıf operations ileti gövdesinin ilk öğeye göre seçer.  
  
 Sınıf oluşturucu çiftleri ile doldurulmuş bir sözlük bekliyor `XmlQualifiedName` ve dizeler yapabildiği nitelenmiş adlar SOAP gövdesi ilk alt adını belirtmek ve dizeleri eşleşen işlem adı belirtin. `defaultOperationName` Karşı bu sözlük eşleşen tüm iletiler alan işlem adıdır:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulamalarıdır arabirimde yalnızca bir yöntem olarak oluşturmak çok basittir: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Bu yöntemin işi, bir gelen iletiyi incelemek ve geçerli uç nokta hizmet sözleşmesindeki yöntemin adı eşittir bir dize döndürecek şekilde silinir.  
  
 Bu örnekte, işlem Seçici edinme bir <xref:System.Xml.XmlDictionaryReader> gelen ileti gövdesi kullanarak kullanıcının <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Geçerli öğenin adını ve ad alanı URI almak ve bunları birleştirmek yeterlidir, böylece bu yöntem okuyucu zaten ileti gövdesinin ilk alt yerleştirir. bir `XmlQualifiedName` ardından kullanılan karşılık gelen işlemi bakmak işlem Seçici tarafından tutulan sözlüğü.  
  
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
  
 İleti gövdesi ile erişme <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövdesi içeriğe erişim neden olan iletiyi bir daha ayrıntılı işleme için geçersiz olduğu anlamına gelir "okundu" olarak işaretlenecek iletinin sağlayan diğer yöntemlerden herhangi birini. Bu nedenle, işlem Seçici, aşağıdaki kodda gösterilen yöntemi ile gelen iletinin bir kopyasını oluşturur. Okuyucunun konumu denetim turu sırasında değiştirilmediğinden olduğundan, özgün iletinin tam bir kopyası sonuçları yeni oluşturulan ileti için ileti özelliklerinde ve ileti üst da kopyalanır, tarafından başvurulabilir:  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a>Bir işlem Seçici için bir hizmet ekleme  
 Hizmet dağıtma işlemi Seçici Windows Communication Foundation (WCF) dağıtıcısı uzantılarıdır. Çift yönlü sözleşmeler geri çağırma kanalı yöntemlerini seçmek için de vardır çok gönderme işlemi Seçici burada açıklanan, ancak bu açıkça Bu örnekte kapsanmaz iş istemci işlemi seçicileri.  
  
 Çoğu hizmet modeli uzantıları gibi gönderme işlemi Seçici davranışları dağıtıcı eklenir. A *davranışı* gönderme çalışma zamanı (veya istemci çalışma zamanı) bir veya daha fazla uzantıları ekler ya da aksi takdirde ayarlarını değiştirir yapılandırma nesnesi.  
  
 İşlem Seçici anlaşması kapsamında olduğundan, burada uygulamak için uygun bir davranıştır <xref:System.ServiceModel.Description.IContractBehavior>. Arabirim üzerinde uygulandığından bir <xref:System.Attribute> türetilmiş sınıf aşağıdaki kodda gösterildiği gibi davranışı bildirimli olarak bir hizmet sözleşmeye eklenebilir. Her bir <xref:System.ServiceModel.ServiceHost> açılır ve gönderme çalışma zamanı oluşturulmuştur, tüm davranışları sözleşmeleri, işlemler ve hizmet uygulamaları özniteliklerinde olarak veya hizmet yapılandırma öğesi olarak otomatik olarak eklenir ve daha sonra istenir bulunamadı Uzantıları katkıda bulunan veya varsayılan yapılandırmayı değiştirebilirsiniz.  
  
 Konuyu uzatmamak amacıyla, aşağıdaki kod alıntı yöntemin uygulanmasını yalnızca gösterir <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, hangi etkiler yapılandırma değişikliklerini bu dağıtıcı için. Bunlar herhangi bir iş yapmadan çağırana döndürmesi için diğer yöntemler gösterilmez.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> işlem Seçici arama Sözlüğü'kurmak ayarlar üzerinden yineleme tarafından uygulama <xref:System.ServiceModel.Description.OperationDescription> service uç noktasının öğelerinde <xref:System.ServiceModel.Description.ContractDescription>. Her bir işlem açıklaması varlığını ardından inceledi `DispatchBodyElementAttribute` davranışı, uygulaması <xref:System.ServiceModel.Description.IOperationBehavior> Ayrıca bu örnekte tanımlanan. Bu sınıf bir davranış da olsa da, pasif ve etkin bir şekilde gönderme çalışma zamanı yapılandırma değişiklikleri gereksinimdir. Tüm yöntemleri, çağırana tüm eylemleri döndürür. Böylece meta veriler için bir işlem seçildiğinde, oluşumunu ile ilgili işlemler ilişkilendirilebilir yeni dağıtım mekanizması, yani body öğesi üzerinde tam adı gerekli işlemi davranış yalnızca bulunmaktadır.  
  
 Böyle bir davranış bulunursa, değer çifti oluşturulan XML tam adı (`QName` özelliği) ve işlem adı (`Name` özelliği) sözlüğe eklenir.  
  
 Sözlük, yeni bir doldurulduktan sonra `DispatchByBodyElementOperationSelector` bu bilgilerle oluşturulur ve gönderme zamanının işlem Seçici ayarlayın:  
  
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
  
## <a name="implementing-the-service"></a>Uygulama hizmeti  
 Bu örnekte doğrudan uygulanan davranışını nasıl kablo iletilerden yorumlanır ve gönderilen, hizmet sözleşmesinin bir işlev olan etkiler. Sonuç olarak, davranışı kullanmak için seçtiği herhangi bir hizmet uygulaması, hizmet sözleşmesi düzeyinde bildirilmesi gerekir.  
  
 Örnek Proje hizmeti geçerli `DispatchByBodyElementBehaviorAttribute` sözleşme davranışa `IDispatchedByBody` hizmet sözleşmesi ve etiketleri her iki işlem `OperationForBodyA()` ve `OperationForBodyB()` ile bir `DispatchBodyElementAttribute` işlemi davranışı. Bu sözleşme uygulayan bir hizmet için bir hizmet konağı açık olduğunda bu meta veriler daha önce anlatıldığı dağıtıcı oluşturucusu tarafından seçilir.  
  
 İşlem Seçici ileti gövdesi öğesinde yalnızca temel gönderir ve "Action" yoksayar olduğundan, döndürülen yanıtı "Action" başlığındaki joker atayarak denetlemek için çalışma zamanı bildirmek için gereklidir "*" için `ReplyAction` özelliği <xref:System.ServiceModel.OperationContractAttribute>. Ayrıca, "Action" özelliği için joker karakter olarak ayarlanmış bir varsayılan işlemi için gerekli olan "\*". Varsayılan işlemi dağıtılamaz ve olmayan tüm iletiler alan bir `DispatchBodyElementAttribute`:  
  
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
  
 Örnek hizmet uygulaması oldukça basittir. Her yöntem alınan ileti bir yanıt iletisi sarmalar ve istemciye geri görüntülemektedir.  
  
## <a name="running-and-building-the-sample"></a>Çalıştıran ve örnek oluşturma  
 Örneği çalıştırdığınızda, işlem yanıt gövdesi içeriğini (biçimlendirilmiş) aşağıdaki çıktıya benzer bir istemci konsol penceresinde görüntülenir.  
  
 İstemci hizmete üç iletileri, gövde öğesi adlandırılan içerik gönderir. `bodyA`, `bodyB`, ve `bodyX`sırasıyla. Önceki Açıklama ve gösterilen hizmet sözleşmesini ertelenmiş olarak gelen ileti ile `bodyA` öğesi tekrarlanarak gönderilen `OperationForBodyA()` yöntemi. İleti için hiçbir açık gönderim hedefi olduğundan `bodyX` body öğesi ileti gönderilen için `DefaultOperation()`. Her hizmet işlemleri yöntemi belirli bir öğenin içine alınan ileti gövdesi sarmalar ve, giriş ilişkilendirin ve bu örnek için açıkça iletileri çıkış yapılır döndürür:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Ayrıca Bkz.
