---
title: Dağıtıcıları Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 653b22adb5ed53c9c3eb44db598ad5d1c50ff1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808244"
---
# <a name="extending-dispatchers"></a>Dağıtıcıları Genişletme
Temel alınan kanalları dışında gelen iletileri çekme, bunları yöntem çağrılarına uygulama kodundaki içine çevirme ve sonuçları çağırana geri göndermek için dağıtıcıları sorumludur. Dağıtıcı uzantıları bu işleme değiştirmenize izin verin.  İnceleme veya iletileri veya parametreleri içeriğini değiştirme ileti veya parametre denetçiler uygulayabilirsiniz.  İletileri işlemleri yönlendirilir veya başka bir işlevsellik sağlamak şekilde değiştirebilirsiniz.  
  
 Bu konuda nasıl kullanılacağını açıklar <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları bir Windows Communication Foundation (WCF) hizmet uygulaması bir dağıtıcı varsayılan yürütme davranışını değiştirmek için müdahale veya iletileri, parametreleri değiştirin veya döndürmek için değerleri önce veya sonra gönderme veya kanal katmandan alınıyor. Eşdeğer istemci çalışma zamanı ileti işleme hakkında daha fazla bilgi için bkz: [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md). Rol anlamak için <xref:System.ServiceModel.IExtensibleObject%601> türleri çeşitli çalışma zamanı özelleştirme nesneleri arasında paylaşılan durumu erişirken yürütebilir, bkz: [genişletilebilen nesneler](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dağıtıcıları  
 Hizmet modeli katmanını geliştiricinin programlama modeli ve yaygın olarak kanal katmanını adlı temel alınan ileti exchange arasında dönüştürme gerçekleştirir. WCF kanalı ve uç nokta dağıtıcıları (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>sırasıyla) ve hizmet bileşenlerinin iletileri, işlemi gönderme ve çağırma ve yanıt işleme alma, yeni kanallar kabul etmek için sorumludur. Dağıtıcı nesneleri alıcı nesneleridir, ancak geri çağırma sözleşme çift yönlü hizmetler uygulamalarında da dağıtıcısı nesnelerine denetleme, değişiklik ya da uzantı için açın.  
  
 Kanal dağıtıcı (ve yardımcı <xref:System.ServiceModel.Channels.IChannelListener>) alt kanal dışında iletileri çeker ve bunların ilgili uç nokta dağıtıcıları iletileri geçirir. Her uç nokta dağıtıcıya sahip bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> iletileri uygun yönlendiren <xref:System.ServiceModel.Dispatcher.DispatchOperation>, yöntemi çağırma işlemi uygulayan için sorumlu olduğu. Çeşitli isteğe bağlıdır ve gerekli uzantısı sınıfları yol boyunca çağrılır. Bu konu, bu bilgilerin nasıl bir araya getireceğinizi ve nasıl özelliklerini değiştirmek ve temel işlevselliğini genişletmek için kendi kodunuzu takılır açıklar.  
  
 Dağıtıcı özellikleri ve değiştirilen özelleştirme nesneleri hizmet uç noktası, sözleşme veya işlemi davranışı nesneleri kullanılarak eklenir. Bu konuda davranışları kullanmayı açıklamaz. Dağıtıcı değişiklikler eklemek için kullanılan türleri hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Aşağıdaki grafikte bir hizmette mimari öğeleri üst düzey bir görünümünü sağlar.  
  
 ![Gönderme çalışma zamanı mimarisi](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Kanal dağıtıcıları  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesne ilişkilendirilecek oluşturulur bir <xref:System.ServiceModel.Channels.IChannelListener> adresindeki (dinleme URI'si olarak adlandırılır) belirli bir URI ile bir hizmet örneği. Her <xref:System.ServiceModel.ServiceHost> nesne birçok olabilir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesneleri, her tek bir dinleyicisi ile ilişkili ve URI dinleme. Bir ileti geldiğinde <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> her ilişkilendirilen sorgular <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> uç nokta ileti kabul edebilir ve olabilir bir iletiyi geçirmeden olup olmadığını nesneleri.  
  
 İnceleme veya üzerinde değişiklik için yaşam süresi ve bir kanal oturum davranışını denetleyen tüm özellikler kullanılabilir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesnesi. Özel kanal başlatıcılar, kanal dinleyicisi, ana bilgisayar, ilişkili bunlar <xref:System.ServiceModel.InstanceContext>ve benzeri.  
  
### <a name="endpoint-dispatchers"></a>Uç nokta dağıtıcıları  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Nesnesidir iletilerden işlemekten sorumlu bir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ne zaman bir ileti hedef adresini eşleşen <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve ileti eylem eşleşmeleri <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> özelliği. İki <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneleri bir ileti kabul edebileceği <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> özellik değeri daha yüksek öncelik endpoint belirler.  
  
 Kullanmak <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> iki ana hizmet modeli uzantısı noktaları – edinmeye <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları – dağıtıcı işlenmesini özelleştirmek için kullanabilirsiniz. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Sınıfı müdahale ve dağıtıcı sözleşmesi kapsamında genişletmek kullanıcıların sağlar (diğer bir deyişle, bir sözleşme tüm iletiler için). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıfı müdahale ve dağıtıcı bir işlemi kapsamında genişletmek kullanıcıların sağlar (diğer bir deyişle, bir işlemde tüm iletiler için).  
  
## <a name="scenarios"></a>Senaryolar  
 Burada pek çok dağıtıcı genişletmek için:  
  
-   Özel ileti doğrulama. Kullanıcılar, bir iletinin belirli bir şema için geçerli olduğunu zorunlu kılabilir. Bu ileti dinleyiciyi arabirimler uygulama tarafından yapılabilir. Bir örnek için bkz: [ileti denetçileri](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Özel ileti günlüğe kaydetme. Kullanıcılar, inceleyin ve bir uç noktası aracılığıyla akış uygulama iletileri bazı kümesi günlüğe. Bu, ileti dinleyiciyi arabirimleriyle da gerçekleştirilebilir.  
  
-   Özel ileti dönüşümleri. Kullanıcılar belirli Dönüşümleri (örneğin, sürüm oluşturma) çalışma zamanı iletisinde uygulayabilirsiniz. Bu, yeniden ileti dinleyiciyi arabirimleri ile gerçekleştirilebilir.  
  
-   Özel veri modeli. Kullanıcılar, WCF'de varsayılan desteklenenler dışındaki bir veri seri hale getirme modelde olabilir (yani, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>ve raw iletileri). Bu uygulama tarafından ileti biçimlendirici arabirimleri yapılabilir. Bir örnek için bkz: [işlem biçimlendirici ve işlem Seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Özel parametre doğrulaması. Kullanıcılar, yazılı parametreleri (XML aksine) geçerli olduğunu zorunlu kılabilir. Bu yapılabilir parametre denetçisi arabirimleri kullanarak.  
  
-   Özel işlem gönderme. Kullanıcılar, Eylem – Örneğin, başka bir şeyi body öğesi veya bir özel ileti özelliği göndermeyi uygulayabilirsiniz. Bu yapılabilir kullanarak <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi. Bir örnek için bkz: [işlem biçimlendirici ve işlem Seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Nesne havuzu oluşturma. Kullanıcıların, yeni bir yapılan her çağrı için ayırma yerine örnekleri havuza alabilir. Bu örnek sağlayıcısı arabirimleri kullanılarak uygulanabilir. Bir örnek için bkz: [toplama](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Örnek kiralama. Kullanıcıların örneği için yaşam süresi, .NET Framework uzaktan iletişim için benzer bir kiralama desen uygulayabilirsiniz. Bu yapılabilir örnek bağlamı ömrü arabirimleri kullanarak.  
  
-   Özel hata işleme. Kullanıcıların nasıl hem yerel hataları işlenir ve istemciler için hataları nasıl bildirilir kontrol edebilirsiniz. Bu kullanarak uygulanabilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimleri.  
  
-   Özel yetkilendirme davranışlar. Kullanıcılar, sözleşme veya işlemi çalışma zamanı parça genişletme ve güvenlik denetimleri iletide belirteçleri göre ekleyerek özel erişim denetimi uygulayabilirsiniz. Bu ileti kesici veya parametre dinleyiciyi arabirimleri kullanılarak gerçekleştirilebilir. Örnekler için bkz: [güvenlik genişletilebilirliği](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Güvenlik özellikleri değiştirme WCF uygulamaları güvenliğini tehlikeye olanağına sahip olduğundan, güvenlikle ilgili değişiklikler dikkatli gerçekleştirmek ve dağıtımdan önce sınamanız kesinlikle önerilir.  
  
-   Özel WCF çalışma zamanı doğrulayıcıları. Hizmetleri, sözleşmeler ve bağlamaları WCF uygulamaları göre kuruluş düzeyinde ilkelerini zorlamak için inceleyin özel doğrulayıcıları yükleyebilirsiniz. (Örneğin, [nasıl yapılır: Lock aşağı Enterprise uç noktalarını](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>DispatchRuntime sınıfını kullanma  
 Kullanım <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı bir hizmet veya tek tek uç nokta varsayılan davranışını değiştirmek için ya da birini veya her ikisini aşağıdaki hizmet işlemleri (veya istemci işlemleri çift yönlü bir istemci söz konusu olduğunda) için özel değişiklikler uygulayan nesneler eklemek için:  
  
-   Gelen iletileri dönüşümü nesneleri ve hizmet nesnesi üzerinde yöntem çağrılarına olarak bu nesneleri serbest bırakma.  
  
-   Bir hizmet işlemi çağrısının giden iletilere yanıt alınıp nesneleri dönüştürme.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Müdahale ve bile bir ileti tanınmıyor olduğunda tüm iletiler için kanal veya uç nokta dağıtıcısı sözleşmeye arasında genişletmek sağlar. Bir ileti herhangi eşleşmeyen geldiğinde bildirilen gönderilen tarafından döndürülen işlemi için sözleşmesindeki <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> özelliği. Intercept veya belirli bir işlem için tüm iletileri üzerinden genişletmek için bkz: <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfı.  
  
 Dağıtıcı genişletilebilirlik tarafından sunulan dört ana alanlarının vardır <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı:  
  
1.  Kanal bileşenleri özelliklerini kullanmak <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve bunlar tarafından döndürülen ilişkili kanal dağıtıcı <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> nasıl kanal dağıtıcı kabul eder ve kanallar kapatır özelleştirmek için özellik. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> özellikleri.  
  
2.  İşlenen her ileti için ileti bileşenleri özelleştirilir. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>ve <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> özellikleri.  
  
3.  Örnek bileşenleri oluşturulması, yaşam süresi ve hizmet türünün örneklerini elden özelleştirin. Hizmet nesne yaşam süresi hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özellikleri.  
  
4.  Güvenlikle ilgili bileşenleri aşağıdaki özellikleri kullanabilirsiniz:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> Denetim olaylarının yazılacağı gösterir.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak taklit girişiminde olup olmadığını denetler.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> başarılı ileti kimlik doğrulama olayları tarafından belirtilen olay günlüğüne yazılır olup olmadığını denetler <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> denetimlerin nasıl <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği ayarlanmış.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Yetkilendirme olaylarının denetlenmesi nasıl gerçekleştirildiğini belirtir.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> günlüğe kaydetme işlemi sırasında oluşan kritik olmayan özel durumlarını engellenip engellenmeyeceğini belirtir.  
  
 Özel uzantı nesneleri genellikle, atanan bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özellik veya hizmet davranışı tarafından bir koleksiyona eklenmiş (uygulayan bir nesne <xref:System.ServiceModel.Description.IServiceBehavior>), bir sözleşme davranış (uygulayan bir nesne <xref:System.ServiceModel.Description.IContractBehavior>), ya da bir uç nokta davranış (uygulayan bir nesneye <xref:System.ServiceModel.Description.IEndpointBehavior>). Yükleme davranışı nesne davranışları uygun koleksiyonuna programlı olarak veya özel bir uygulama tarafından eklenen sonra <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> uygulama yapılandırma dosyası kullanarak eklenecek davranışını etkinleştirmek için nesne.  
  
 Çift yönlü istemcileri (çift yönlü bir hizmet tarafından belirtilen bir geri çağırma sözleşmesini uygulama istemciler) de bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> kullanılarak erişilebilir nesne <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> özelliği.  
  
### <a name="using-the-dispatchoperation-class"></a>DispatchOperation sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıftır konumu için çalışma zamanı değişiklikleri ve ekleme kapsamındaki özel uzantıları için yalnızca bir hizmet işlemi noktası. (Bir sözleşme tüm iletiler için hizmet çalışma zamanı davranışını değiştirmek için kullanın <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı.)  
  
 Yükleme <xref:System.ServiceModel.Dispatcher.DispatchOperation> bir özel hizmet davranışı nesnesi kullanılarak değişiklikler.  
  
 Kullanım <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> bulmak için özellik <xref:System.ServiceModel.Dispatcher.DispatchOperation> belirli bir hizmet işlemini temsil eden nesne.  
  
 Aşağıdaki özellikler çalışma zamanı yürütme işlemi düzeyinde kontrol edin:  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> özelliklerini işlemi için ilgili değerleri alın.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> işlem davranışı belirtin.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> göreli olarak kullanıcı tanımlı bir hizmet nesnesinin ömrü denetim özelliklerini <xref:System.ServiceModel.InstanceContext>.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> özellikleri etkinleştirmek ve iletileri nesneleri iletilerden dönüştürme üzerinde açık denetim.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Özelliği işlemi kimliğe bürünme düzeyini belirtir.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Özelliği işlemi için özel çağrısı bağlam uzantıları ekler.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Özelliği denetler zaman parametre nesneler yok.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Özelliği bir özel çağırıcı nesnesi ekler.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Özelliği inceleyebilir veya parametreleri değiştirin ve dönüş değerleri için kullanabileceğiniz bir özel parametre denetçisi eklemenize olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime>  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation>  
 [Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)  
 [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)  
 [Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
