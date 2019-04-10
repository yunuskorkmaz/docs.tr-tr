---
title: İleti Denetçileri
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: c9d2c47a816e7fd8c5d219009128ed530564b81b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334958"
---
# <a name="message-inspectors"></a>İleti Denetçileri
Bu örnek, uygulama ve hizmet ve istemci ileti denetçileri yapılandırma gösterir.  
  
 Hizmet modeli istemci çalışma zamanı'nda kullanılabilen bir genişletilebilirlik nesnesini bir ileti denetleyicidir ve gönderme çalışma zamanı programlı olarak veya yapılandırma, inceleyin ve iletileri alındıktan sonra veya gönderilmeden önce alter.  
  
 Bu örnek, bir temel istemci ve yapılandırılabilir bir XML Şeması belge kümesine gelen iletileri doğrular hizmet ileti doğrulama mekanizması uygular. Bu örnek, her işlem için iletileri doğrulamaz unutmayın. Kasıtlı bir basitleştirme budur.  
  
## <a name="message-inspector"></a>İleti denetçisi  
 İleti denetçileri uygulama istemci <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi ve hizmet ileti denetçileri uygulama <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> arabirimi. Uygulamalar için her iki tarafın çalışır bir ileti Inspector'ı oluşturmak için tek bir sınıfta birleştirilebilir. Bu örnekte, böyle bir birleşik ileti denetçisi uygular. Inspector'ı geçirme karşı gelen ve giden iletileri doğrulanır şemaları kümesi içinde oluşturulur ve gelen veya giden iletileri olup olmadığı doğrulanır ve denetçisi gönderme veya istemci modunda olup belirtmek geliştiricinin sağlar, hata işleme, bu konunun ilerleyen kısımlarında açıklandığı gibi etkiler.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> önce serisi ve işlem için gönderilen bir ileti alındı, kanal yığını tarafından işlenir ve bir hizmete atanan olduğunda, ancak gönderici tarafından çağrılır. Gelen ileti şifrelenmişse, ileti denetçisi ulaştığında, ileti zaten şifresi çözülür. Yöntem alır `request` inceledi, yönetilen veya değiştirilmesi gerektiği gibi bir ileti veren bir başvuru parametresi'olarak ileti geçirildi. Dönüş değeri herhangi bir nesne olabilir ve geçirilen bir bağıntı durum nesnesi olarak kullanılan <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> geçerli iletiye yanıt döndürdüğünde hizmet. Bu örnekte <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> özel, yerel yöntemi iletinin (doğrulama) İnceleme Temsilciler `ValidateMessageBody` ve hiçbir bağıntı durum nesnesi döndürür. Bu yöntem geçersiz ileti hizmetine geçirmenizi sağlar.  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> bir yanıt gelen ileti işlenirken bir istemciye ya da tek yönlü iletileri, söz konusu olduğunda gönderilmeye hazır olduğunda çağrılır. Bu bağımsız olarak MEP simetrik, çağrılan saymak uzantılar sağlar. Olduğu gibi <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, iletinin bir başvuru parametresi geçirilir ve inceledi, değiştirilebilir veya değiştirildi. Bu örnekte gerçekleştirilen iletinin doğrulama için yeniden temsilci `ValidMessageBody` yöntemi, ancak doğrulama hatalarını işlenmesi biraz farklı bu durumda.  
  
 Hizmette bir doğrulama hatası meydana gelirse `ValidateMessageBody` yöntem <xref:System.ServiceModel.FaultException>-türetilen özel durum. İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bu özel durumlar nerede bunlar otomatik olarak SOAP hataları dönüştürülür ve istemciye geçişli hizmet modeli altyapısı içine koyabilirsiniz. İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> özel durumları gerekir değil put altyapısına ileti denetçisi çağrılmadan önce dönüştürülmesi, hizmet tarafından oluşturulan hata özel durum oluştuğu için. Bu nedenle aşağıdaki uygulama bilinen yakalar `ReplyValidationFault` özel durumu ve yanıt iletisi bir açık hata iletisi ile değiştirir. Bu yöntem geçersiz ileti hizmet uygulaması tarafından döndürülür sağlar.  
  
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
  
 İstemci ileti Inspector'ı çok benzer. Gelen uygulanması gereken iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> olan <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> ileti istemci uygulaması veya işlem biçimlendirici oluşan olduğunda çağrılır. İleti dağıtıcısı ileti denetçileri ile yalnızca olarak inceledi ya da tamamen değiştirildi. Bu örnekte, temsilci denetçisi aynı yerel `ValidateMessageBody` da gönderme ileti denetçileri için kullanılan bir yardımcı yöntemi.  
  
 Davranış arasındaki hizmet ve istemci doğrulama (oluşturucu içinde belirtildiği gibi) istemci doğrulama kullanıcı kodu yerel olarak gerçekleştirildiği ve bir hizmet hatası nedeniyle değil yerleştirilir yerel özel durum oluşturur farktır. Genellikle, hizmet dağıtıcı denetçiler hataları atar ve istemci Inspectors özel durumlar kuralıdır.  
  
 Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulama geçersiz ileti hizmetine gönderilmesini sağlar.  
  
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
  
 `AfterReceiveReply` Uygulama hizmetinden alınan geçersiz ileti için istemci kullanıcı kodu geçirilen sağlar.  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Bu iletiyi denetçisi kalbidir `ValidateMessageBody` yöntemi. İşini gerçekleştirmek için bir doğrulama sarmaladığı <xref:System.Xml.XmlReader> gövdesi içerik alt ağacı geçirilen iletisinin geçici bir çözüm. Okuyucu, bir dizi ileti Inspector'ı tutan şemaları ile doldurulur ve doğrulama geri çağırma başvuran bir temsilci için `InspectionValidationHandler` yanı sıra bu yöntem tanımlanır. Doğrulamayı gerçekleştirmek için ileti ardından okuma ve bir stream destekli belleğe biriktirilir <xref:System.Xml.XmlDictionaryWriter>. Geri çağırma yöntemi, bir doğrulama hata veya uyarı işlemde oluşursa çağrılır.  
  
 Eğer hiç Hata oluşmazsa, yeni bir ileti özgün iletiden üst bilgilerini ve özelliklerini kopyalar ve tarafından Sarmalanan bellek stream'de şimdi doğrulanmış bilgi kümesi kullanan oluşturulan bir <xref:System.Xml.XmlDictionaryReader> ve değiştirme iletiye eklenir.  
  
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
  
 `InspectionValidationHandler` Doğrulayarak yöntemi çağrıldığında <xref:System.Xml.XmlReader> zaman şeması doğrulama hatası veya uyarısı meydana gelir. Aşağıdaki uygulama yalnızca hatalarla çalışır ve tüm uyarıları yok sayar.  
  
 İlk konusuna göre bir doğrulama eklemesine olası görünebilir <xref:System.Xml.XmlReader> doğrulama iletiye olanak tanır ve ileti Inspector, ileti işleme ve iletiyi arabelleğe alma olmadan gerçekleşir. Geçersiz XML düğümüyle algılandığında, beklenmeyen davranışla sonuçlanarak ancak bu geri çağırma doğrulama istisnalarını hizmete yere atar anlamına gelir altyapı ya da kullanıcı kod modeli. Arabelleğe alma yaklaşımı geçersiz iletileri kullanıcı kodundan tamamıyla ayrıntılarından korur.  
  
 Daha önce bahsedildiği gibi istemci ve hizmet işleyici tarafından oluşturulan özel durumları farklıdır. Özel durumları türetilmiştir hizmette <xref:System.ServiceModel.FaultException>, istemcide normal özel durumları özel durumlardır.  
  
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
 İleti denetçileri istemci çalışma zamanı veya gönderme çalışma zamanı uzantılarıdır. Bu tür uzantılar kullanarak yapılandırılan *davranışları*. Bir davranış için varsayılan yapılandırmanın değiştirilmesine veya uzantılarını (örneğin, ileti denetçileri) ekleyerek service model çalışma zamanı davranışını değiştiren bir sınıftır.  
  
 Aşağıdaki `SchemaValidationBehavior` davranışı istemciye bu örneğe ait ileti denetçisi ekleyin veya çalışma zamanı dağıtım için kullanılan bir sınıftır. Her iki durumda da yerine temel uygulamasıdır. İçinde <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> ve <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, ileti denetçisi oluşturulur ve eklenen <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> ilgili çalışma zamanı koleksiyonu.  
  
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
>  Bu belirli davranış öznitelik olarak çift değil ve bu nedenle bildirimli olarak bir hizmet türünün bir sözleşme türü eklenemiyor. Bu şema koleksiyonu bir öznitelik bildirimi yüklenemiyor ve bu öznitelik bir fazladan yapılandırma konumuna (örneğin için uygulama ayarları) başvuran yapılandırma öğesi oluşturma anlamına gelir çünkü bir tasarım kararıdır hizmet modeli yapılandırma geri kalanı ile tutarlı değil. Bu nedenle, bu davranış yalnızca kesin bir hizmet modeli yapılandırma uzantısı ve kod aracılığıyla eklenebilir.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>İleti Inspector'ı yapılandırma ekleme  
 Uygulama yapılandırma dosyasında bir uç noktada özel bir davranışı yapılandırmak için hizmet modeli yapılandırma oluşturmak uygulayıcılar gerektirir *uzantı öğesi* türetilen bir sınıf tarafından temsil edilen <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>. Bu uzantı ardından hizmet modeli yapılandırma bölümü uzantıları için bu bölümde açıklanan aşağıdaki uzantı için gösterildiği gibi eklenmesi gerekir.  
  
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
  
 Uzantıları, uygulama ya da en yaygın seçenektir, ASP.NET yapılandırma dosyası veya makine yapılandırma dosyasına eklenebilir.  
  
 Uzantı yapılandırma kapsamına eklendiğinde davranışı aşağıdaki kodda gösterildiği bir davranışı yapılandırmasına eklenebilir. Davranış, gerektiği gibi birden fazla uç nokta için uygulanabilir yeniden kullanılabilir öğeleri yapılandırmalardır. Belirli bir davranışı olmasını uygular burada yapılandırılan çünkü <xref:System.ServiceModel.Description.IEndpointBehavior>, bunu yalnızca yapılandırma dosyasındaki ilgili yapılandırma bölümünde geçerlidir.  
  
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
  
 `<schemaValidator>` İleti Inspector'ı yapılandıran öğesi destekli `SchemaValidationBehaviorExtensionElement` sınıfı. İki Boolean ortak özellikler adlı sınıfı gösterir `ValidateRequest` ve `ValidateReply`. Bunların her ikisi de ile işaretlenmiş bir <xref:System.Configuration.ConfigurationPropertyAttribute>. Bu öznitelik kod özellikleri önceki XML yapılandırma öğesinde görülebilir XML öznitelikleri arasındaki bağlantı oluşturur. Sınıfı ayrıca bir özelliğe sahiptir `Schemas` ayrıca ile işaretlenmiş <xref:System.Configuration.ConfigurationCollectionAttribute> ve türü `SchemaCollection`, ayrıca parçası olan bu belgedeki kısaltma belirtilmemişse ancak bu örnek. Koleksiyon ve koleksiyon öğesi sınıfı ile birlikte bu özellik `SchemaConfigElement` yedekler `<schemas>` önceki yapılandırma kod parçacığında öğesi ve bir koleksiyon şema doğrulama kümesine eklemeye izin verir.  
  
 Geçersiz kılınan `CreateBehavior` yöntemi bir istemci veya bir uç nokta oluştururken çalışma zamanı yapılandırma verilerini değerlendirirken, bu yapılandırma verilerini davranışı nesnesine dönüştürür.  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a>İleti denetçileri kesin ekleme  
 (Bu örnekte, daha önce bahsedilen nedeni desteklenmiyor) öznitelikler ve yapılandırma yoluyla, davranışları oldukça kolay kesin kod kullanarak bir istemci ve hizmet çalışma zamanına eklenebilir dışında. Bu örnekte, bu istemci ileti Inspector'ı test etmek için istemci uygulamasında gerçekleştirilir. `GenericClient` Sınıfı türetilen <xref:System.ServiceModel.ClientBase%601>, kullanıcı kodu için uç nokta yapılandırması sunar. İstemci örtük olarak açılmadan önce uç nokta yapılandırması, örneğin aşağıdaki kodda gösterildiği gibi davranışları ekleyerek değiştirilebilir. Hizmette davranış ekleme, burada gösterilen istemci teknik büyük ölçüde eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
