---
title: İleti Denetçileri
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 05dbee820a002feb1f2a1672220be0c4a397f952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="message-inspectors"></a>İleti Denetçileri
Bu örnek, uygulama ve hizmet ve istemci ileti denetçileri yapılandırma gösterilmektedir.  
  
 Bir ileti denetçisi hizmet modelinin istemci çalışma zamanında kullanılan bir genişletilebilirlik nesne ve gönderme çalışma zamanı program aracılığıyla veya yapılandırma ve inceleyin ve iletileri alındıktan sonra veya gönderilmeden önce değiştirmek.  
  
 Bu örnek, bir temel istemci ve gelen iletileri bir dizi yapılandırılabilir XML Şeması belgeler karşı doğrular hizmet ileti doğrulama mekanizması uygular. Bu örnekte her bir işlemin iletileri doğrulamaz unutmayın. Bu kasıtlı basitleştirme olur.  
  
## <a name="message-inspector"></a>İleti denetçisi  
 İstemci ileti denetçiler uygulama <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi ve hizmet ileti denetçiler uygulama <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> arabirimi. Uygulamaları için iki tarafı da çalışır bir ileti denetçisi oluşturmak için tek bir sınıfta birleştirilebilir. Bu örnek, bu tür bir birleştirilmiş ileti denetçisi uygular. Inspector göre gelen ve giden iletiler doğrulanma şemaları kümesinde geçirme oluşturulur ve gelen veya giden iletiler olup olmadığı doğrulanır ve Inspector gönderme veya istemci modunda olup olmadığını belirlemek Geliştirici sağlar; hata işleme, bu konunun ilerleyen bölümlerinde açıklandığı gibi etkiler.  
  
```  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Tüm hizmet (gönderen) iletiyi denetçisi iki uygulamalıdır <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntemleri <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> seri durumdan ve işlem için gönderilen önce bir ileti alındı, kanal yığını tarafından işlenen ve bir hizmete atanan olduğunda, ancak gönderici tarafından çağrılır. Gelen ileti şifrelenmişse, ileti denetçisi ulaştığında, ileti zaten şifresi çözülür. Yöntemi alır `request` ileti geçirilen Denetlenmekte, yönetilebilir veya gerektiğinde yerini iletiye sağlayan bir başvuru parametre olarak. Dönüş değeri gibi herhangi bir nesne olabilir ve geçirilen bağıntı durumu nesnesi olarak kullanılan <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> hizmeti geçerli iletiye yanıt döndüğünde. Bu örnekte <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> özel, yerel yöntemine iletisinin denetleme (doğrulama) Temsilciler `ValidateMessageBody` ve hiçbir bağıntı durum nesnesi döndürür. Bu yöntem geçersiz ileti hizmete geçmesini sağlar.  
  
```  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> bir yanıt gelen ileti işlendiğinde bir istemciye ya da tek yönlü iletileri, söz konusu olduğunda gönderilmek üzere hazır olduğunda çağrılır. Bu bağımsız olarak MEP simetrik, çağrılan saymak uzantılar sağlar. İle <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, ileti başvuru parametre olarak geçirilir ve Denetlenmekte, değiştirilebilir veya değiştirildi. Bu örnekte gerçekleştirilen ileti doğrulama yeniden için temsilci `ValidMessageBody` yöntemi, ancak doğrulama hatalarının işlenmesini biraz farklı bu durumda.  
  
 Hizmette bir doğrulama hatası oluşursa, `ValidateMessageBody` yöntemi atar <xref:System.ServiceModel.FaultException>-özel durumları türetilmiş. İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bu özel durumlar burada bunlar otomatik olarak SOAP hataları dönüştürülen ve istemciye geçişli hizmet modeli altyapısı içine koyabilirsiniz. İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> özel durumlar gerekir değil put altyapısını, ileti denetçisi çağrılmadan önce hizmeti tarafından oluşturulan hataya özel durumları dönüştürme oluştuğundan. Bu nedenle aşağıdaki uygulama bilinen yakalar `ReplyValidationFault` özel durumu ve yanıt iletisi bir açık hata iletisi ile değiştirir. Bu yöntem geçersiz ileti hizmeti uygulaması tarafından döndürülür sağlar.  
  
```  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 İstemci ileti denetçisi çok benzer. Gelen uygulanmalı iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> olan <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> ileti istemci uygulaması veya işlem biçimlendirici tarafından oluşan olduğunda çağrılır. İleti dağıtıcısı ileti denetçileri ile henüz olarak Denetlenmekte veya tamamen değiştirilir. Bu örnekte, denetçisi temsilciler aynı yerel `ValidateMessageBody` gönderme ileti denetçileri için de kullanılır yardımcı yöntemi.  
  
 Davranış (oluşturucuda belirtildiği şekilde) istemci ve hizmet doğrulama arasında istemci doğrulama kullanıcı koda yerel olarak gerçekleştirildiği için ve bir hizmet hatası nedeniyle değil put yerel özel durumları oluşturur farktır. Genellikle, hizmet dağıtıcısı denetçiler hataları throw ve istemci denetçiler özel durumlar oluşturma kuralıdır.  
  
 Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulaması sağlar geçersiz ileti hizmetine gönderilir.  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 `AfterReceiveReply` Uygulama hizmetinden alınan hiçbir geçersiz ileti için istemci kullanıcı koduna geçirilen sağlar.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Bu belirli ileti denetçisinin Kalp olan `ValidateMessageBody` yöntemi. Kendi işlerini yapmak için bir doğrulama sarmaladığı <xref:System.Xml.XmlReader> gövde içerik alt ağaç geçirilen iletinin geçici. Okuyucu ileti denetçisi tutan şemaları kümesi ile doldurulur ve doğrulama geri çağırma başvuran bir temsilci Ayarla `InspectionValidationHandler` yanı sıra bu yöntem tanımlanır. Doğrulamayı gerçekleştirmek için ileti ardından okuma ve bir akış destekli belleğe Biriktiricideki <xref:System.Xml.XmlDictionaryWriter>. Bir doğrulama hata veya uyarı işleminde ortaya çıkarsa, geri çağırma yöntemi çağrılır.  
  
 Herhangi bir hata oluşursa, yeni bir ileti özellikleri ve üstbilgileri özgün iletiden kopyalar ve şimdi doğrulanmış bilgi tarafından Sarmalanan bellek akışında kullanan oluşturulan bir <xref:System.Xml.XmlDictionaryReader> ve değiştirme iletiye eklendi.  
  
```  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 `InspectionValidationHandler` Doğrulayarak yöntemi çağrıldığında <xref:System.Xml.XmlReader> şema doğrulama hata veya uyarı olduğunda oluşur. Aşağıdaki uygulama yalnızca hatalarla çalışır ve tüm uyarıları yok sayar.  
  
 İlk konusuna göre bir doğrulama eklemesine olası görünebilir <xref:System.Xml.XmlReader> doğrulama ileti denetçisi ve let iletisine, ileti işleme ve ileti arabelleğe alma olmadan gerçekleşir. Geçersiz XML düğümlerini algılandığında, beklenmeyen bir davranışa kaynaklanan ancak, bu geri çağırma doğrulama istisnalarını hizmete yere atar anlamına gelir altyapı veya kullanıcı kodu model. Arabelleğe alma yaklaşım geçersiz iletileri kullanıcı kodundan tamamen ayrıntılarından korur.  
  
 Daha önce ele alındığı gibi istemci ile hizmet arasında işleyici tarafından oluşturulan özel durumlar değişir. Özel durumlar türetilir hizmette <xref:System.ServiceModel.FaultException>, istemcide normal özel durumları durumlardır.  
  
```  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Davranış  
 İleti denetçileri istemci çalışma zamanı veya gönderme çalışma zamanı uzantılarıdır. Bu tür uzantılar kullanılarak yapılandırılmış olan *davranışları*. Bir davranış için (örneğin, ileti denetçileri) uzantıları ekleme veya varsayılan yapılandırmayı değiştirme tarafından hizmet modeli çalışma zamanı davranışını değiştiren bir sınıftır.  
  
 Aşağıdaki `SchemaValidationBehavior` için kullanılır. Bu örneği ait ileti denetçisi istemciye ekleyin veya çalışma zamanı gönderme davranışı bir sınıftır. Her iki durumda da yerine temel uygulamasıdır. İçinde <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> ve <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, ileti denetçisi oluşturulur ve eklenen <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> ilgili çalışma zamanı koleksiyonu.  
  
```  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
>  Bu belirli davranışı bir özniteliği olarak çift değil ve bu nedenle bildirimli olarak bir hizmet türünün anlaşma türünü eklenemiyor. Şema koleksiyonu bir öznitelik bildiriminde yüklenemiyor ve bu öznitelik (örneğin için uygulama ayarları) bir ek yapılandırma konuma başvuran yapılandırma öğesi oluşturma anlamına gelir çünkü yapılan tasarım kararı budur hizmet modeli yapılandırma geri kalanı ile tutarlı değil. Bu nedenle, bu davranış yalnızca imperatively bir hizmet modeli yapılandırma uzantısı ve kod aracılığıyla eklenebilir.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Yapılandırma yoluyla ileti denetçisi ekleme  
 Uygulama yapılandırma dosyasında bir uç noktada özel davranışı yapılandırmak için hizmet modeli yapılandırma oluşturmak Implementers gerektirir *uzantı öğesi* türetilmiş bir sınıf tarafından temsil edilen <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Bu uzantı sonra uzantıları için hizmet modeli yapılandırma bölümü için bu bölümde ele alınan aşağıdaki uzantısı gösterildiği gibi eklenmesi gerekir.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 Uzantılar uygulama ya da en yaygın seçimdir, ASP.NET yapılandırma dosyası veya makine yapılandırma dosyası eklenebilir.  
  
 Uzantısı yapılandırma kapsamına eklendiğinde, aşağıdaki kodda gösterildiği gibi bir davranış yapılandırma davranışı eklenebilir. Davranış, gerektiği gibi birden çok uç nokta uygulanabilir yeniden kullanılabilir öğeleri bağlantılardır. Olmasını belirli davranışı uygular burada yapılandırılan çünkü <xref:System.ServiceModel.Description.IEndpointBehavior>, yalnızca yapılandırma dosyasındaki ilgili yapılandırma bölümünde geçerli olduğundan.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 `<schemaValidator>` İleti denetçisi yapılandırır öğesi tarafından desteklenen `SchemaValidationBehaviorExtensionElement` sınıfı. Sınıf adlı iki Boole ortak özellikleri kullanıma sunan `ValidateRequest` ve `ValidateReply`. Bunların her ikisi de ile işaretlenmiş bir <xref:System.Configuration.ConfigurationPropertyAttribute>. Bu öznitelik kod özellikleri ve önceki XML yapılandırma öğesinde görülebilir XML öznitelikleri arasındaki bağlantıyı meydana gelir. Sınıfı ayrıca bir özelliğe sahiptir `Schemas` ek olarak işaretlenen ile <xref:System.Configuration.ConfigurationCollectionAttribute> ve türü `SchemaCollection`, olduğu da kısaltma bu belgeden belirtilmemişse ancak bu örnek bir parçası. Bu özellik koleksiyonu ve koleksiyon öğesi sınıfı ile birlikte `SchemaConfigElement` yedekler `<schemas>` önceki yapılandırma parçacığı öğesinde ve şemalar topluluğu doğrulama kümesine eklemeye izin verir.  
  
 Geçersiz kılınan `CreateBehavior` yöntemi bir istemci veya uç yapılar gibi çalışma zamanı yapılandırma verilerini değerlendirirken, bu yapılandırma verilerini bir davranış nesnesine dönüştürür.  
  
```  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>İleti denetçileri Imperatively ekleme  
 (Bu örnekte önceden bildirdi nedeni desteklenmez) öznitelikleri ve yapılandırma yoluyla, davranışları oldukça kolaylıkla kesinlik temelli kod kullanarak bir istemci ve hizmet çalışma zamanı için eklenebilir dışında. Bu örnekte, bu istemci ileti denetçisi test etmek için istemci uygulamasında gerçekleştirilir. `GenericClient` Sınıfı türetilir <xref:System.ServiceModel.ClientBase%601>, kullanıcı kodu için uç nokta yapılandırması kullanıma sunar. İstemci örtük olarak açılmadan önce uç nokta yapılandırması, örneğin aşağıdaki kodda gösterildiği gibi davranışları ekleyerek değiştirilebilir. Hizmette davranışı eklemek, burada gösterilen istemci teknik büyük ölçüde eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.  
  
```  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a>Ayrıca Bkz.
