---
title: Dağıtıcıları Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: df726d71880d135adb883f834acfa9839641eae3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162730"
---
# <a name="extending-dispatchers"></a>Dağıtıcıları Genişletme
Dağıtıcıları çağırana geri göndererek arka plandaki kanal gelen iletileri çekerek ve bunları yöntem çağrıları uygulama kodunda içine çevirme yükümlü olursunuz. Dağıtıcı uzantıları, bu işleme değiştirmenize olanak sağlar.  İnceleme veya değiştirme iletileri ya da parametreler içeriğini ileti veya parametre denetçiler uygulayabilirsiniz.  İletileri işlemleri yönlendirilir veya başka bir işlevsellik sağlayan biçimini değiştirebilirsiniz.  
  
 Bu konu nasıl kullanılacağını açıklar <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları bir Windows Communication Foundation (WCF) hizmet uygulaması bir dağıtıcı varsayılan yürütme davranışını değiştirmek veya ıntercept iletileri, parametreleri değiştirin veya döndürmek için öncesinde veya gönderme veya bunları kanal katmandan alınırken den değerleri. Eşdeğer istemci Çalışma Zamanı Modülü ileti işleme hakkında daha fazla bilgi için bkz: [genişletme istemciler](../../../../docs/framework/wcf/extending/extending-clients.md). Rol anlamak için <xref:System.ServiceModel.IExtensibleObject%601> türleri çeşitli çalışma zamanı özelleştirme nesneleri arasında paylaşılan durum erişirken yürütmek, bkz: [genişletilebilen nesneler](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dağıtıcıları  
 Hizmet modeli katmanını geliştiricinin programlama modeli ve kanal katmanını sık adlı temel alınan ileti exchange arasında dönüştürme yapar. WCF kanalı ve uç nokta dağıtıcıları (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>sırasıyla) hizmet bileşenleri, yeni kanallar, iletileri, işlem dağıtma ve çağırma ve yanıt işleme alma kabul etmek için sorumludur. Alıcı nesneleri dağıtıcı nesnelerdir ancak geri çağırma anlaşması çift yönlü hizmetler uygulamalarında da inceleme, değiştirilmesi veya uzantı için dağıtıcı nesnelerine sunarsınız.  
  
 Kanal dağıtıcı (ve yardımcı <xref:System.ServiceModel.Channels.IChannelListener>) temel kanal iletileri çeker ve bunların ilgili uç nokta dağıtıcıları için iletileri geçirir. Her uç nokta dağıtıcı sahip bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> iletileri uygun yönlendiren <xref:System.ServiceModel.Dispatcher.DispatchOperation>, işlemi uygulayan yöntem çağırmak için sorumlu olduğu. Çeşitli isteğe bağlıdır ve gerekli uzantı sınıfları, süreç boyunca çağrılır. Bu konu, parçaların birbirine nasıl uyduğunu ve nasıl olabileceğiniz özelliklerini değiştirmek ve temel işlevlerini genişletmek için kendi kodunuzu takın açıklar.  
  
 Dağıtıcı özellikleri ve değiştirilmiş özelleştirme nesneleri hizmet, uç nokta, sözleşme veya işlem davranışı nesneleri kullanılarak eklenir. Bu konuda, davranışları kullanmayı açıklamaz. Dağıtıcı değişiklikleri eklemek için kullanılan türleri hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Aşağıdaki grafikte, hizmet mimari öğeleri üst düzey bir görünümünü sağlar.  
  
 ![Dağıtım çalışma zamanı mimarisi](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Kanal dağıtıcıları  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ilişkilendirilecek nesnesi oluşturulur bir <xref:System.ServiceModel.Channels.IChannelListener> (dinleme URI'si olarak adlandırılır) belirli bir URI ile bir hizmeti örneği konumunda. Her <xref:System.ServiceModel.ServiceHost> nesne birçok olabilir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesneler, yalnızca bir dinleyicisi ile ilişkili her ve URI dinleyin. İleti geldiğinde <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> her ilişkili sorgular <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> uç nokta iletiyi kabul edebilir ve yapabilen bir iletiyi geçirmeden olmadığını nesneleri.  
  
 İnceleme veya değişikliği için yaşam süresi ve kanal oturum davranışını denetleyen tüm özellikler kullanılabilir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesne. Özel kanal başlatıcılar, kanal dinleyicisi, konak, ilişkili bunlar <xref:System.ServiceModel.InstanceContext>ve benzeri.  
  
### <a name="endpoint-dispatchers"></a>Uç nokta dağıtıcıları  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Nesnesi gelen iletileri işlemek için sorumlu olan bir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ne zaman bir ileti hedef adresi eşleşen <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve ileti eylem eşleşmeleri <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> özelliği. İki <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneleri bir iletiyi kabul edebilir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> özellik değeri, daha yüksek öncelik uç noktasına belirler.  
  
 Kullanma <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> iki ana hizmet modeli uzantı noktaları – almaya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları – dağıtıcı işlenmesini özelleştirmek için kullanabilirsiniz. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Sınıfı ıntercept ve dağıtıcı sözleşme kapsamında genişletmek kullanıcıların sağlar (diğer bir deyişle, Sözleşme'de tüm iletiler için). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıfı ıntercept ve bir işlem kapsamında dağıtıcı genişletmek kullanıcıların sağlar (diğer bir deyişle, bir işlem de tüm iletiler için).  
  
## <a name="scenarios"></a>Senaryolar  
 Burada birkaç nedenden dağıtıcı genişletmek için:  
  
-   Özel ileti doğrulama. Kullanıcılar, bir ileti için belirli bir şema geçerli olduğunu zorunlu kılabilir. Bu ileti kesici arabirimlerini uygulayarak yapılabilir. Bir örnek için bkz. [ileti denetçileri](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Özel ileti günlüğe kaydetme. Kullanıcılar, inceleyin ve bir uç noktası aracılığıyla akış uygulama iletileri bir dizi oturum. Bu da ileti kesici arabirimleri ile gerçekleştirilebilir.  
  
-   Özel ileti dönüşümler. Kullanıcılar belirli Dönüşümleri (örneğin, sürüm oluşturma) çalışma zamanında iletisi uygulayabilir. Bu, yeniden ileti kesici arabirimleri ile gerçekleştirilebilir.  
  
-   Özel veri modeli. Kullanıcılar, varsayılan olarak WCF tarafından desteklenen dışındaki bir veri seri hale getirme modeli olabilir (yani, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>ve ham iletileri). Bu ileti biçimlendirici arabirimler uygulama tarafından yapılabilir. Bir örnek için bkz. [işlem biçimlendirici ve işlem Seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Özel parametre doğrulama. Kullanıcı türü belirtilmiş bir parametre (XML aksine) geçerli olduğunu zorunlu kılabilir. Bu yapılabilir parametresi denetçisi arabirimleri kullanarak.  
  
-   Özel işlem gönderme. Kullanıcılar, eylemi-Örneğin, başka bir şey üzerine body öğesi ya da bir özel ileti özelliği gönderme uygulayabilirsiniz. Bu yapılabilir kullanarak <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi. Bir örnek için bkz. [işlem biçimlendirici ve işlem Seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Nesne havuzu oluşturma. Kullanıcılar, her çağrı için yeni bir ayırma yerine örnekleri havuza alabilir. Bu örnek sağlayıcısı arabirimleri kullanılarak uygulanabilir. Bir örnek için bkz. [toplama](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Örnek kiralama. Kullanıcılar örneği için kullanım süresi, .NET Framework uzaktan iletişim için benzer bir kiralama desen uygulayabilirsiniz. Bu yapılabilir örneği bağlam ömrü arabirimleri kullanarak.  
  
-   Özel hata işleme. Kullanıcıların nasıl hem de yerel hata işlenir ve istemcilere geri hatalarının nasıl iletildiği denetleyebilirsiniz. Bunu kullanarak uygulanabilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimleri.  
  
-   Özel yetkilendirme davranışlar. Kullanıcılar, sözleşme veya işlemi çalışma zamanı parçaları genişletme ve iletide belirteçleri temel güvenlik denetimleri ekleyerek özel erişim denetimi uygulayabilirsiniz. Bu ileti kesici veya parametre dinleyiciyi arabirimleri kullanarak gerçekleştirilebilir. Örnekler için bkz [güvenlik genişletilebilirliği](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Güvenlik özelliklerini değiştirerek WCF uygulamaları güvenliğini tehlikeye olanağına sahip olduğundan, güvenlikle ilgili değişiklikler dikkatli harcayıp ve dağıtımdan önce sınamanız önerilir.  
  
-   WCF özel çalışma zamanı doğrulayıcıları. WCF uygulamaları göre kurumsal düzey ilkelerini zorlamak için Hizmetleri, sözleşmeler ve bağlamaları inceleyin özel doğrulayıcıları yükleyebilirsiniz. (Örneğin, [nasıl yapılır: Enterprise uç noktalarını kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>DispatchRuntime sınıfını kullanma  
 Kullanım <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı bir hizmet ya da tek bir uç noktası'nın varsayılan davranışını değiştirmek veya bir ya da aşağıdaki hizmet işlemleri (veya çift yönlü istemci söz konusu olduğunda istemci işlemleri) hem de özel değişiklikler uygulayan nesneler Ekle:  
  
-   Gelen iletileri dönüştürme nesneleri ve hizmet nesnesi üzerinde yöntem çağrıları olarak bu nesneleri serbest bırakma.  
  
-   Dönüştürme nesnelerin bir hizmet işlemi çağırma giden iletilere yanıt aldı.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Intercept ve bile bir ileti tanınmıyor tüm iletiler için kanal veya uç nokta dağıtıcı sözleşmeye arasında doğru genişletmenize olanak tanır. Bir ileti herhangi eşleşmeyen geldiğinde bildirilen dağıtılan işleme tarafından döndürülen sözleşmesindeki <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> özelliği. Intercept ya da belirli bir işlem için tüm iletiler arasında genişletmek için bkz: <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfı.  
  
 Dağıtıcı genişletilebilirlik tarafından sunulan dört ana alan bulunur <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı:  
  
1.  Kanal bileşenleri özelliklerini kullanmak <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve bunlar tarafından döndürülen ilişkili kanal dağıtıcı <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> nasıl kanal dağıtıcı kabul eder ve kanalları kapatır özelleştirmek için özellik. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> özellikleri.  
  
2.  İşlenen her ileti için ileti bileşenleri özelleştirilir. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>ve <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> özellikleri.  
  
3.  Örnek bileşenleri oluşturma, yaşam süresi ve hizmet türünün örneklerini elden özelleştirin. Hizmet nesne kullanım ömrü hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Bu kategori içerir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özellikleri.  
  
4.  Güvenlikle ilgili bileşenlerini aşağıdaki özellikleri kullanabilirsiniz:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> denetim olayları yazılacağı gösterir.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak bürünülecek deneyip denemeyeceğini denetler.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> başarılı iletisi kimlik doğrulama olayları tarafından belirtilen olay günlüğüne yazılır olup olmadığını kontrol eder <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> denetimleri nasıl <xref:System.Threading.Thread.CurrentPrincipal%2A> özelliği ayarlanmış.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Yetkilendirme olaylarının denetlenmesini nasıl gerçekleştirildiğini belirtir.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> günlüğe kaydetme işlemi sırasında oluşan özel durumlar kritik olmayan engellenip engellenmeyeceğini belirtir.  
  
 Genellikle, özel genişletme nesneleri için atanmış olan bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özelliği veya bir koleksiyona bir hizmet davranışını tarafından eklenen (uygulayan bir nesne <xref:System.ServiceModel.Description.IServiceBehavior>), bir sözleşme davranış (uygulayan bir nesne <xref:System.ServiceModel.Description.IContractBehavior>), veya bir uç nokta davranış (uygulayan bir nesne <xref:System.ServiceModel.Description.IEndpointBehavior>). Yükleme davranışı nesneyi programlama yoluyla veya özel bir uygulama tarafından davranışların ilgili koleksiyona eklenir sonra <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> uygulama yapılandırma dosyası kullanarak eklenecek davranışı etkinleştirmek için nesne.  
  
 Çift yönlü istemcileri (çift yönlü bir hizmet tarafından belirtilen bir geri çağırma anlaşması uygulamak istemciler) de bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> kullanılarak erişilebilir nesne <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> özelliği.  
  
### <a name="using-the-dispatchoperation-class"></a>DispatchOperation sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıfı, konumu çalışma zamanı değişiklikleri ve ekleme kapsamındaki özel uzantıları için yalnızca bir hizmet işlemine noktası. (Bir sözleşme tüm iletiler için hizmet çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfı.)  
  
 Yükleme <xref:System.ServiceModel.Dispatcher.DispatchOperation> bir özel hizmet davranışı nesnesini kullanarak değişiklikler.  
  
 Kullanım <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> bulmak için özellik <xref:System.ServiceModel.Dispatcher.DispatchOperation> belirli hizmet işlemini temsil eden nesne.  
  
 Aşağıdaki özellikleri, çalışma zamanı yürütme işlemi düzeyinde denetler:  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> özelliklerini işlemi ilgili değerleri alın.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> işlem davranışı belirtin.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> özellikleri göreli kullanıcı tanımlı bir hizmet nesnenin ömrünü denetlemek <xref:System.ServiceModel.InstanceContext>.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> özellikleri nesneleri ve nesneleri iletileri için iletileri dönüştürme açık bir denetime olanak tanır.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Özellik işlemi kimliğe bürünme düzeyini belirtir.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Özelliği işlemi için özel arama bağlamı uzantısını ekler.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Özelliği, parametre nesneler yok edileceği zaman denetler.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Özelliği bir özel Invoker nesnesi ekler.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Özelliği inceleyin veya değiştirme parametreleri ve dönüş değerleri için kullanabileceğiniz bir özel parametre denetçisi eklemenizi sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
