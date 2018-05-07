---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: a59f639fc0f1adad48bfda5fd8105340ac004cef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="dispatch-by-body-element"></a>Gövde Öğesine göre Dağıt
Bu örnek, gelen iletileri işlemlerine izin atamak için alternatif bir algoritma uygulamak gösterilmiştir.  
  
 Varsayılan olarak, hizmet modeli dağıtıcısı ileti WS-üzerinde tabanlı adresleme gelen ileti için uygun işleme yöntemi seçer "Eylem" üstbilgi veya HTTP SOAP isteğinin eşdeğer bilgileri.  
  
 WS izlemeyin yığınları bazı SOAP 1.1 Web Hizmetleri-ı temel Profil 1.1 yönergeleri eylem URI üzerinde temel, ancak bunun yerine ilk öğe SOAP gövdesi içinde XML tam adını temel iletileri gönderme değil. Benzer şekilde, bu yığınları istemci tarafı SOAP 1.1 belirtimine göre verilmişti bir boş veya rasgele HTTP SoapAction başlık iletileri gönderebilir.  
  
 Yöntemlere iletileri gönderilen şeklini değiştirmek için örnek uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> genişletilebilirlik arabirimde `DispatchByBodyElementOperationSelector`. Bu sınıf, ileti gövdesinin ilk öğe üzerinde temel işlemleri seçer.  
  
 Sınıf oluşturucu çiftleri ile doldurulan bir sözlük bekliyor `XmlQualifiedName` ve alınabildiği nitelenmiş adlar SOAP gövdesi ilk alt adını belirtmek ve işlem adıyla eşleşen dizeleri belirtmek dizeleri. `defaultOperationName` Bu sözlük karşı eşleşen tüm iletileri alan işlemi adıdır:  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulamaları arabirimde tek bir yöntem olarak oluşturmak çok basit: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Bu yöntemin iş gelen iletiyi incelemek için bir hizmet sözleşmesi yöntemi geçerli uç nokta adına eşit bir dize döndürecek şekilde ise.  
  
 Bu örnekte, işlem Seçici edinir bir <xref:System.Xml.XmlDictionaryReader> gelen ileti gövdesi kullanarak kullanıcının <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Bu yöntem okuyucu böylece geçerli öğenin adını ve ad alanı URI'si almak ve bunları birleştirmek yeterli iletinin gövdesi ilk alt zaten yerleştirir. bir `XmlQualifiedName` sonra kullanılan karşılık gelen işlemi bakmak işlem Seçici tarafından tutulan sözlük.  
  
```  
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
  
 İleti gövdesi erişme <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ya da ileti gövdesi içeriğe erişmeye neden iletinin ileti herhangi başka bir işleme için geçersiz olduğu anlamına gelir "Okuma" olarak işaretlenmiş sağlayan diğer yöntemlerden herhangi birini. Bu nedenle, işlem Seçici aşağıdaki kodda gösterildiği yöntemiyle gelen iletinin bir kopyasını oluşturur. Okuyucunun konumu İnceleme sırasında değiştirilmedi çünkü orijinal iletinin tam bir kopyasını sonuçları yeni oluşturulan ileti için ileti özellikleri ve ileti üstbilgilerini de kopyalanır, tarafından başvurulabilir:  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Bir hizmet için bir işlem seçici ekleme  
 Hizmeti dağıtma işlemi seçiciler Windows Communication Foundation (WCF) dağıtıcı uzantıları. Çift yönlü sözleşmeler geri çağırma kanalda yöntemlerini seçmek için de vardır çok gönderme işlemi seçiciler burada açıklanan ancak, bu örnekte açıkça kapsanmayan gibi iş istemci işlemi seçicileri.  
  
 Çoğu hizmet modeli uzantıları gibi gönderme işlemi seçiciler davranışları kullanarak dağıtıcısı eklenir. A *davranışı* gönderme çalışma zamanı (veya istemci çalışma zamanı) bir veya daha fazla uzantıları ekler veya aksi halde ayarlarını değiştirir yapılandırma nesnesi.  
  
 İşlem Seçici sözleşmesi kapsamına sahip olduğundan, burada uygulamak için uygun davranıştır <xref:System.ServiceModel.Description.IContractBehavior>. Arabirim üzerinde uygulanır çünkü bir <xref:System.Attribute> türetilmiş sınıf aşağıdaki kodda gösterildiği gibi davranışı bildirimli olarak hiçbir hizmet sözleşmesine eklenebilir. Her bir <xref:System.ServiceModel.ServiceHost> açılır ve gönderme çalışma zamanı oluşturulmuştur, tüm davranışları sözleşmeler, işlemleri ve hizmet uygulamaları özniteliklerinde veya hizmet yapılandırma öğesi olarak otomatik olarak eklenir ve daha sonra istenir bulundu Uzantıları katkıda veya varsayılan yapılandırmayı değiştirin.  
  
 Konuyu uzatmamak amacıyla, aşağıdaki kod Alıntısı yöntemin kullanımı yalnızca gösterir <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, hangi etkiler yapılandırma değişikliklerinin bu örnekteki dağıtıcı için. Herhangi bir iş yapmadan çağırana döndürmeleri çünkü diğer yöntemleri gösterilmez.  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama ayarlayan işlem Seçici arama sözlük üzerinden yineleme tarafından <xref:System.ServiceModel.Description.OperationDescription> hizmet uç noktanın öğelerinde <xref:System.ServiceModel.Description.ContractDescription>. Her işlem açıklaması varlığını ardından Denetlenmekte `DispatchBodyElementAttribute` davranışı, uygulaması <xref:System.ServiceModel.Description.IOperationBehavior> Bu örnek ayrıca tanımlanan. Bu sınıf bir davranış da olsa da, pasif ve etkin olarak gönderme çalışma zamanı için herhangi bir yapılandırma değişikliği katkıda değil. Tüm yöntemlerinden herhangi bir eylem bırakmadan çağırana döndürür. Böylece bir işlem seçildiğinde, geçişi ile ilgili işlemleri ilişkilendirilebilir yeni gönderme mekanizması için yani body öğesinde tam adını meta verileri gerekli işlemi davranışı yalnızca bulunmaktadır.  
  
 Bu tür bir davranış bulunursa, değer çifti oluşturulan XML tam adı (`QName` özelliği) ve işlem adı (`Name` özelliği) sözlüğe eklenir.  
  
 Sözlük, yeni bir doldurulduktan sonra `DispatchByBodyElementOperationSelector` bu bilgilerle oluşturulur ve gönderme çalışma zamanı işlem Seçici ayarlayın:  
  
```  
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
 Bu örnekte doğrudan uygulanan davranışını nasıl kablo iletilerden yorumlanır ve dağıtılan, hizmet sözleşmesi işlevinin olduğu etkiler. Sonuç olarak, davranışı kullanmak için seçtiği herhangi bir hizmet uygulaması hizmet sözleşmesi düzeyinde üzerindeki bildirilmelidir.  
  
 Örnek Proje hizmeti geçerlidir `DispatchByBodyElementBehaviorAttribute` sözleşme davranışına `IDispatchedByBody` hizmet sözleşmesi ve etiketlerinin her iki işlem `OperationForBodyA()` ve `OperationForBodyB()` ile bir `DispatchBodyElementAttribute` işlemi davranışı. Bu sözleşme uygulayan bir hizmet için bir hizmet konak açıldığında, bu meta veriler daha önce anlatıldığı dağıtıcısı Oluşturucu tarafından kayıt.  
  
 İşlem Seçici ileti gövdesi öğesinde yalnızca tabanlı gönderir ve "Eylem" yoksayar olduğundan, döndürülen yanıt "Eylem" başlığında joker atayarak denetlemek için çalışma zamanı bildirmek için gereklidir "*" için `ReplyAction` özelliği <xref:System.ServiceModel.OperationContractAttribute>. Ayrıca, "Eylem" özelliği için joker karakter olarak ayarlanmış bir varsayılan işlemi sahip olması gereken "\*". Varsayılan işlemi gönderilen olamaz ve sahip olmayan tüm iletileri alan bir `DispatchBodyElementAttribute`:  
  
```  
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
  
 Örnek hizmet uygulaması basittir. Her yöntem alınan ileti yanıt iletisine sarmalar ve istemciye görüntülemektedir.  
  
## <a name="running-and-building-the-sample"></a>Çalıştıran ve örnek oluşturma  
 Örneği çalıştırdığınızda, işlem yanıt gövdesi içeriğini aşağıdaki (biçimlendirilmiş) çıktıyı benzer istemci konsol penceresinde görüntülenir.  
  
 İstemci üç iletileri hizmetine, gövde öğesi adlandırılan içerik gönderir `bodyA`, `bodyB`, ve `bodyX`sırasıyla. Önceki Açıklama ve gösterilen hizmet sözleşmesini ertelenmiş olarak gelen ileti ile `bodyA` öğesi gönderilen için `OperationForBodyA()` yöntemi. İleti için hiçbir açık gönderme hedef olduğundan `bodyX` ileti body öğesi gönderilen için `DefaultOperation()`. Her hizmet işlemlerinin yönteme belirli bir öğenin içine alınan ileti gövdesi sarmalar ve, giriş ilişkilendirmek ve bu örnek için açıkça iletileri çıkış yapılır döndürür:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Ayrıca Bkz.
