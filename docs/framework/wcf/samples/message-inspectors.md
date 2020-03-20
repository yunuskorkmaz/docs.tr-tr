---
title: İleti Denetçileri
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 705401a182d5d816bc2682f5f21ff09ca95f21c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144454"
---
# <a name="message-inspectors"></a>İleti Denetçileri
Bu örnek, istemci ve hizmet iletisi denetçilerinin nasıl uygulanacağını ve yapılandırılabildiğini gösterir.  
  
 İleti denetçisi, hizmet modelinin istemci çalışma zamanında ve gönderme çalışma saatinde veya yapılandırma yoluyla kullanılabilecek ve iletileri alındıktan sonra veya gönderilmeden önce inceleyip değiştirebilen bir genişletilebilirlik nesnesidir.  
  
 Bu örnek, gelen iletileri yapılandırılabilir XML Şema belgelerine karşı doğrulayan temel bir istemci ve hizmet iletisi doğrulama mekanizması uygular. Bu örnek her işlem için iletileri doğrulamaz unutmayın. Bu kasıtlı bir basitleştirmedir.  
  
## <a name="message-inspector"></a>İleti Denetçisi  
 İstemci ileti <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> denetçileri arabirimi uygular <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ve hizmet iletisi denetmenleri arabirimi uygular. Uygulamalar, her iki taraf için de çalışan bir ileti denetçisi oluşturmak için tek bir sınıfa birleştirilebilir. Bu örnek böyle bir leştirilmiş ileti denetçisi uygular. Denetçi, gelen ve giden iletilerin doğrulandığı bir dizi şema da oluşturulur ve geliştiricinin gelen veya giden iletilerin doğrulanıp doğrulanmadığını ve denetçinin sevk veya istemci modunda olup olmadığını belirlemesine olanak tanır, bu konunun daha sonra tartışılan hata işleme etkiler.  
  
```csharp
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
  
 Herhangi bir hizmet (sevk irsaliyesi) ileti denetçisi iki <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntem <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>bir ileti alındığı, kanal yığını tarafından işlendiği ve bir hizmete atandığı, ancak seri çözülmeden ve bir işleme gönderilmeden önce sevk eden tarafından çağrılır. Gelen ileti şifrelenmişse, ileti denetçisi ne zaman ulaşırsa iletinin şifresi zaten çözülür. Yöntem, iletinin `request` denetlenmesini, işlenmesini veya gerektiği gibi değiştirilmesine olanak tanıyan bir başvuru parametresi olarak iletinin geçirilmesini sağlar. İade değeri herhangi bir nesne olabilir ve hizmet geçerli iletiye <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> bir yanıt verdiğinde geçirilen bir korelasyon durumu nesnesi olarak kullanılır. Bu örnekte, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> iletinin denetimini (doğrulanmasını) özel, `ValidateMessageBody` yerel yönteme devreder ve hiçbir korelasyon durumu nesnesini döndürür. Bu yöntem, hizmete geçersiz iletilerin geçmemesini sağlar.  
  
```csharp  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>bir yanıt istemciye geri gönderilmeye hazır olduğunda veya gelen ileti işlendiğinde tek yönlü iletiler söz konusu olduğunda çağrılır. Bu uzantıları ne olursa olsun MEP, simetrik olarak adlandırılan saymak için izin verir. Olduğu <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>gibi, ileti bir başvuru parametresi olarak geçirilir ve denetlenebilir, değiştirilebilir veya değiştirilebilir. Bu örnekte gerçekleştirilen iletinin doğrulaması yine `ValidMessageBody` yönteme devredilir, ancak doğrulama hatalarının işlenmesi bu durumda biraz farklıdır.  
  
 Hizmette bir doğrulama hatası oluşursa, `ValidateMessageBody` <xref:System.ServiceModel.FaultException>yöntem türetilmiş özel durumlar atar. Bu <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>istisnalar, otomatik olarak SOAP hatalarına dönüştürülüp istemciye aktarılan servis modeli altyapısına konulabilir. Hizmet <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> tarafından atılan hata özel durumlarının dönüşümü ileti denetçisi çağrılmadan önce oluştuğundan, özel durumlar altyapıya konulmamalıdır. Bu nedenle, aşağıdaki `ReplyValidationFault` uygulama bilinen özel durumu yakalar ve yanıt iletisi açık bir hata iletisi ile değiştirir. Bu yöntem, hizmet uygulaması tarafından geçersiz iletilerin döndürülmesini sağlar.  
  
```csharp  
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
  
 İstemci ileti denetçisi çok benzer. Uygulanması gereken iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> . <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>ileti istemci uygulaması veya işlem formatter tarafından oluşturulduğunda çağrılır. Sevk irsaliyesi ileti denetçilerinde olduğu gibi, ileti sadece denetlenebilir veya tamamen değiştirilebilir. Bu örnekte, denetçi, gönderme iletisi denetçileri için de kullanılan aynı yerel `ValidateMessageBody` yardımcı yöntemini devreder.  
  
 İstemci ve hizmet doğrulaması arasındaki davranış farkı (oluşturucuda belirtildiği gibi), istemci doğrulamasının bir hizmet hatası nedeniyle değil, yerel olarak oluştukları için kullanıcı koduna konulan yerel özel durumlar atmasıdır. Genel olarak, kural, servis sevk irsaliyesi müfettişleri hataları atmak ve istemci müfettişleri özel durumlar atmak olduğunu.  
  
 Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulama, hizmete geçersiz ileti gönderilmemesini sağlar.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 Uygulama, `AfterReceiveReply` hizmetten alınan geçersiz iletilerin istemci kullanıcı koduna iletilmesini sağlar.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Bu özel mesaj denetçisinin `ValidateMessageBody` kalbi yöntemdir. Çalışmasını gerçekleştirmek için, geçirilen iletinin <xref:System.Xml.XmlReader> gövde içeriği alt ağacının etrafına doğrulayan bir sarar. Okuyucu, ileti denetçisinin tuttuğu şema kümesiyle doldurulur ve doğrulama geri araması, bu yöntemin yanında tanımlanana atıfta bulunan `InspectionValidationHandler` bir temsilciye ayarlanır. Doğrulamayı gerçekleştirmek için ileti okunur ve bellek akışı destekli bir alana <xref:System.Xml.XmlDictionaryWriter>biriktirilir. İşlemde bir doğrulama hatası veya uyarı oluşursa, geri arama yöntemi çağrılır.  
  
 Hata oluşmaz, özellikleri ve üstbilgileri özgün iletiden kopyalayan ve bellek akışında şimdi doğrulanmış bilgi kümesini kullanan ve bir <xref:System.Xml.XmlDictionaryReader> iletiyi sarıp değiştirilen iletiye eklenen yeni bir ileti oluşturulur.  
  
```csharp  
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
  
 Yöntem, `InspectionValidationHandler` şema doğrulama <xref:System.Xml.XmlReader> hatası veya uyarısı oluştuğunda doğrulama tarafından çağrılır. Aşağıdaki uygulama yalnızca hatalarla çalışır ve tüm uyarıları yok sayar.  
  
 İlk olarak, ileti denetçisi ile <xref:System.Xml.XmlReader> iletiye doğrulama enjekte etmek ve ileti işlenirken ve iletiyi arabelleğe almadan doğrulamanın gerçekleşmesine izin vermek mümkün görünebilir. Ancak bu, bu geri aramanın doğrulama özel durumlarını hizmet modeli altyapısına veya geçersiz XML düğümleri algılanırken kullanıcı koduna bir yere attığı ve öngörülemeyen davranışlara yol açacağı anlamına gelir. Arabelleğe alma yaklaşımı, kullanıcı kodunu geçersiz iletilerden tamamen korur.  
  
 Daha önce de ele alındığı gibi, işleyici tarafından atılan özel durumlar istemci ve hizmet arasında farklılık gösterir. Hizmette, özel <xref:System.ServiceModel.FaultException>durumlar, istemcide istisnalar düzenli özel özel durumlardır.  
  
```csharp  
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
 İleti denetçileri istemci çalışma zamanı veya sevk çalışma zamanı uzantıları vardır. Bu tür uzantılar *davranışlar*kullanılarak yapılandırılır. Davranış, varsayılan yapılandırmayı değiştirerek veya uzantılar (ileti baslayışları gibi) ekleyerek hizmet modelinin çalışma zamanı davranışını değiştiren bir sınıftır.  
  
 Aşağıdaki `SchemaValidationBehavior` sınıf, bu örneğin ileti denetçisini istemciye veya sevk çalışma süresine eklemek için kullanılan davranıştır. Uygulama her iki durumda da oldukça basittir. Içinde <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>ve , ileti denetçisi <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> oluşturulur ve ilgili çalışma zamanı nın koleksiyonuna eklenir.  
  
```csharp
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
> Bu özel davranış bir öznitelik olarak iki katına çıkmaz ve bu nedenle bir hizmet türünün sözleşme türüne bildirimsel olarak eklenemez. Şema koleksiyonu bir öznitelik bildirimine yüklenemediği ve bu öznitelikte fazladan bir yapılandırma konumuna (örneğin uygulama ayarlarına) atıfta bulunulduğu için bu, bir yapılandırma öğesi oluşturma anlamına geldiği için alınan bir yan tasarım kararıdır. hizmet modeli yapılandırmasının geri kalanıyla tutarlı değildir. Bu nedenle, bu davranış yalnızca zorunlu olarak kod ve hizmet modeli yapılandırma uzantısı yoluyla eklenebilir.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Yapılandırma yoluyla İleti Denetçisi ekleme  
 Uygulama yapılandırma dosyasındaki bir bitiş noktasında özel bir davranışı yapılandırmak için, hizmet modeli uygulayıcıların türetilen <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>bir sınıf tarafından temsil edilen bir yapılandırma uzantısı *öğesi* oluşturmasını gerektirir. Bu uzantı, bu bölümde açıklanan aşağıdaki uzantıda gösterildiği gibi uzantılar için hizmet modelinin yapılandırma bölümüne eklenmelidir.  
  
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
  
 Uzantılar, en yaygın seçenek olan uygulama veya ASP.NET yapılandırma dosyasına veya makine yapılandırma dosyasına eklenebilir.  
  
 Uzantı yapılandırma kapsamına eklendiğinde, davranış aşağıdaki kodda gösterildiği gibi davranış yapılandırmasına eklenebilir. Davranış yapılandırmaları, gerektiğinde birden çok uç noktaya uygulanabilen yeniden kullanılabilir öğelerdir. Burada yapılandırılacak belirli bir davranış <xref:System.ServiceModel.Description.IEndpointBehavior>uygulandığından, yalnızca yapılandırma dosyasındaki ilgili yapılandırma bölümünde geçerlidir.  
  
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
  
 İleti `<schemaValidator>` denetçisini yapılandıran öğe `SchemaValidationBehaviorExtensionElement` sınıf tarafından desteklenir. Sınıf adlı `ValidateRequest` iki Boolean ortak `ValidateReply`özellikleri ortaya çıkarır ve . Bunların her ikisi de <xref:System.Configuration.ConfigurationPropertyAttribute>bir . Bu öznitelik, önceki XML yapılandırma öğesinde görülebilen kod özellikleri ile XML öznitelikleri arasındaki bağlantıyı oluşturur. Sınıf ayrıca ek `Schemas` olarak işaretlenmiş <xref:System.Configuration.ConfigurationCollectionAttribute> bir özelliği vardır ve `SchemaCollection`türü , aynı zamanda bu örneğin bir parçası olan ancak kısalık için bu belgeden atlanan. Bu özellik, koleksiyon ve koleksiyon `SchemaConfigElement` öğesi sınıfıyla birlikte önceki yapılandırma snippet'indeki öğeyi `<schemas>` geri verir ve doğrulama kümesine şema koleksiyonu eklemeye olanak tanır.  
  
 Geçersiz kılınan `CreateBehavior` yöntem, çalışma zamanı bir istemci veya bitiş noktası oluştururken yapılandırma verilerini değerlendirirken yapılandırma verilerini davranış nesnesine dönüştürür.  
  
```csharp
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
  
## <a name="adding-message-inspectors-imperatively"></a>Zorunlu Olarak İleti Denetçisi Ekleme  
 Öznitelikler (daha önce atıfta bulunulan nedenlerle bu örnekte desteklenmeyen) ve yapılandırma dışında, davranışlar zorunlu kod kullanılarak istemci ve hizmet çalışma süresine kolayca eklenebilir. Bu örnekte, bu istemci ileti denetçisi sınamak için istemci uygulamasında yapılır. <xref:System.ServiceModel.ClientBase%601>Sınıf, `GenericClient` uç nokta yapılandırmasını kullanıcı koduna gösteren türetilmiştir. İstemci örtülü olarak açılmadan önce, örneğin aşağıdaki kodda gösterildiği gibi davranışlar eklenerek uç nokta yapılandırması değiştirilebilir. Hizmetteki davranışın eklenmesi büyük ölçüde burada gösterilen istemci tekniğine eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.  
  
```csharp  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
