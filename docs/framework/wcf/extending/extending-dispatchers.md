---
title: Dağıtıcıları Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 4eb96eaf409fd34e9b10a469ed31fbbe18ebac5e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046007"
---
# <a name="extending-dispatchers"></a>Dağıtıcıları Genişletme
Dispatchler, temel alınan kanallara ait gelen iletileri çekmekten, bunları uygulama kodundaki yöntem çağırmaları içine çevirerek ve sonuçları çağırana geri gönderen sorumludurlar. Dağıtıcı uzantıları bu işlemeyi değiştirmenize izin verir.  İletilerin veya parametrelerin içeriğini denetleyen veya değiştiren ileti ya da parametre Inspectors uygulayabilirsiniz.  İletilerin işlemlere yönlendirilme biçimini değiştirebilir veya başka bir işlevsellik sağlayabilirsiniz.

Bu konu, bir dağıtıcı 'ın varsayılan <xref:System.ServiceModel.Dispatcher.DispatchRuntime> yürütme <xref:System.ServiceModel.Dispatcher.DispatchOperation> davranışını değiştirmek veya iletileri, parametreleri veya dönüşü ele almak ya da değiştirmek için bir Windows Communication Foundation (WCF) hizmet uygulamasında ve sınıflarının nasıl kullanılacağını açıklar. ya da sonrasında kanal katmanından gönderilmeden veya ondan sonra gelen değerler. Eşdeğer istemci çalışma zamanı iletisi işleme hakkında daha fazla bilgi için bkz. [Istemcileri genişletme](../../../../docs/framework/wcf/extending/extending-clients.md). Farklı çalışma zamanı özelleştirme nesneleri <xref:System.ServiceModel.IExtensibleObject%601> arasında paylaşılan duruma erişirken, türlerin hangi rol üzerinde çalındığını anlamak için bkz. [Genişletilebilir nesneler](../../../../docs/framework/wcf/extending/extensible-objects.md).

## <a name="dispatchers"></a>Dağıtıcılarının yerini alabilir

Hizmet modeli katmanı, geliştiricilerin programlama modeli ve genellikle kanal katmanı olarak adlandırılan temel ileti değişimi arasında dönüştürme işlemini gerçekleştirir. WCF 'de kanal ve uç nokta sevkiyatcıları (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>sırasıyla), yeni kanalları kabul etme, iletileri alma, işlem gönderme ve çağırma ve yanıt işleme işlemlerinin sorumlu olduğu hizmet bileşenleridir. Dağıtıcı nesneleri alıcı nesneleridir, ancak çift yönlü hizmetlerdeki geri çağırma sözleşmesi uygulamaları da denetim, değişiklik veya uzantı için Dispatcher nesnelerini kullanıma sunar.

Kanal dağıtıcısı (ve Yardımcısı <xref:System.ServiceModel.Channels.IChannelListener>), iletileri düşük kanaldan alıp iletileri ilgili uç noktası dağıtıcıları 'na geçirir. Her uç nokta dağıtıcılarının <xref:System.ServiceModel.Dispatcher.DispatchRuntime> , işlemi uygulayan yöntemi çağırmaktan <xref:System.ServiceModel.Dispatcher.DispatchOperation>sorumlu olan iletileri uygun bir şekilde yönlendirdiğini vardır. Çeşitli isteğe bağlı ve gerekli uzantı sınıfları, bu şekilde çağrılır. Bu konu, bu parçaların nasıl bir araya uyduğunu ve temel işlevselliği genişletmek için özellikleri nasıl değiştirebileceğinizi ve içindeki kodunuzu nasıl kullanabileceğinizi açıklar.

Dağıtıcı özellikleri ve değiştirilmiş özelleştirme nesneleri, hizmet, uç nokta, anlaşma veya işlem davranışı nesneleri kullanılarak eklenir. Bu konu, davranışların nasıl kullanılacağını tanımlamaz. Dağıtıcı değişikliklerini eklemek için kullanılan türler hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).

Aşağıdaki grafik, bir hizmette mimari öğelerin üst düzey bir görünümünü sağlar.

![Dağıtım çalışma zamanı mimarisi](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")

### <a name="channel-dispatchers"></a>Kanal Sevkiyatcıları

Belirli <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> bir URI 'nin (dinleme URI <xref:System.ServiceModel.Channels.IChannelListener> 'si olarak adlandırılır) bir hizmetin örneğiyle ilişkilendirilmesi için bir nesne oluşturulur. Her <xref:System.ServiceModel.ServiceHost> nesne, her biri <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> yalnızca bir dinleyici ve dinleme URI 'siyle ilişkili birçok nesneye sahip olabilir. Bir ileti geldiğinde <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> , her bir ilişkili <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneyi, uç noktanın iletiyi kabul edip etmediğini sorgular ve iletiyi ' a iletir.

Bir kanal oturumunun ömrünü ve davranışını denetleyen tüm özellikler, <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> nesne üzerinde denetleme veya değiştirme için kullanılabilir. Bunlar özel kanal başlatıcıları, kanal dinleyicisi, ana bilgisayar, ilişkili <xref:System.ServiceModel.InstanceContext>vb. içerir.

### <a name="endpoint-dispatchers"></a>Endpoint Dispatchler

<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> Nesne, bir<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> iletinin hedef adresi ile eşleştiğinde ve ileti eylemi özelliği ile eşleştiğinde bir öğesinden gelen <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> iletileri işlemeden sorumludur. İki <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesne bir iletiyi kabul edebiliyorsanız <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> , özellik değeri daha yüksek öncelikli uç noktayı belirler.

, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Dağıtıcısı işlemini özelleştirmek için kullanabileceğiniz iki ana hizmet modeli uzantı noktasını <xref:System.ServiceModel.Dispatcher.DispatchRuntime> (ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları) almak için kullanın. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Sınıfı, kullanıcıların dağıtıcıyı anlaşma kapsamında (yani, bir sözleşmede bulunan tüm iletiler için) kesmesini ve genişletmesini sağlar. <xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıfı, kullanıcıların dağıtıcı bir işlem kapsamında (yani bir işlemdeki tüm iletiler için) kesmesini ve genişletmesine olanak tanır.

## <a name="scenarios"></a>Senaryolar

Dağıtıcısı genişletecek birkaç neden vardır:

- Özel Ileti doğrulaması. Kullanıcılar, belirli bir şema için bir iletinin geçerli olduğunu zorlayabilir. Bu işlem, ileti yakalayıcı arabirimlerini uygulayarak yapılabilir. Bir örnek için bkz. [ileti](../../../../docs/framework/wcf/samples/message-inspectors.md)denetçiler.

- Özel Ileti günlüğü. Kullanıcılar bir uç nokta aracılığıyla akan bazı uygulama iletilerini inceleyebilir ve günlüğe kaydedebilir. Bu, ileti yakalayıcısı arabirimleriyle de gerçekleştirilebilir.

- Özel Ileti dönüşümleri. Kullanıcılar çalışma zamanındaki iletiye bazı dönüşümler uygulayabilir (örneğin, sürüm oluşturma için). Bu, ileti yakalayıcısı arabirimleriyle birlikte gerçekleştirilebilir.

- Özel veri modeli. Kullanıcılar, WCF 'de varsayılan olarak desteklenenden farklı bir veri serileştirme modeline sahip olabilir (yani <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>,, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, ve ham iletiler). Bu, ileti biçimlendirici arabirimlerini uygulayarak yapılabilir. Bir örnek için bkz. [Işlem biçimlendirici ve Işlem seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).

- Özel parametre doğrulaması. Kullanıcılar, yazılan parametrelerin geçerli olduğunu (XML 'nin aksine) zorunlu kılabilir. Bu işlem, parametre denetçisi arabirimleri kullanılarak yapılabilir.

- Özel Işlem gönderme. Kullanıcılar, örneğin gövde öğesinde veya özel bir ileti özelliğinde, eylem dışında bir şeye gönderme işlemini uygulayabilir. Bu, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi kullanılarak yapılabilir. Bir örnek için bkz. [Işlem biçimlendirici ve Işlem seçici](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).

- Nesne havuzu oluşturma. Kullanıcılar, her çağrı için yeni bir tane ayırmak yerine, örnekleri havuza alabilir. Bu, örnek sağlayıcı arabirimleri kullanılarak uygulanabilir. Bir örnek için bkz. [Pooling](../../../../docs/framework/wcf/samples/pooling.md).

- Örnek Kiralama. Kullanıcılar, .NET Framework uzaktan Iletişim ile benzer örnek ömrü için bir kiralama stili uygulayabilir. Bu, örnek bağlam ömrü arabirimleri kullanılarak yapılabilir.

- Özel hata Işleme. Kullanıcılar, yerel hataların nasıl işlendiğini ve hataların istemcilere nasıl geri iletildiğini denetleyebilir. Bu, <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimler kullanılarak uygulanabilir.

- Özel yetkilendirme davranışları. Kullanıcılar, sözleşmenin veya Işlemin çalışma zamanı parçalarını genişleterek ve iletideki belirteçleri temel alarak güvenlik denetimleri ekleyerek özel erişim denetimi uygulayabilir. Bu, ileti yakalayıcısı ya da parametre yakalayıcısı arabirimleri kullanılarak yapılabilir. Örnekler için bkz. [güvenlik genişletilebilirliği](../../../../docs/framework/wcf/samples/security-extensibility.md).

  > [!CAUTION]
  > Güvenlik özelliklerinin değiştirilmesi, WCF uygulamalarının güvenliğinin aşılmasına neden olduğundan, dağıtıma karşı güvenlikle ilgili değişiklikler yapmanız ve dağıtımdan önce kapsamlı test yapmanız önerilir.

- Özel WCF çalışma zamanı Doğrulayıcıları. WCF uygulamalarına göre kurumsal düzeyde ilkeleri zorlamak için Hizmetleri, sözleşmeleri ve bağlamaları incelemek üzere özel doğrulayıcılar yükleyebilirsiniz. (Örneğin, bkz [. nasıl yapılır: Kuruluştaki](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)uç noktaları kilitle.)

### <a name="using-the-dispatchruntime-class"></a>DispatchRuntime sınıfını kullanma

Bir hizmetin veya tek bir uç noktanın varsayılan davranışını değiştirmek ya da aşağıdaki hizmet işlemlerinin birine veya her ikisine de (bir çift yönlü istemci durumunda istemci süreçlerine) özel değişiklikler uygulayan nesneler eklemek için sınıfınıkullanın:<xref:System.ServiceModel.Dispatcher.DispatchRuntime>

- Gelen iletilerin nesnelere dönüştürülmesi ve bu nesneleri bir hizmet nesnesi üzerinde yöntem çağırma olarak serbest bırakma.

- Bir hizmet işleminin yanıtından alınan nesnelerinin giden iletilere çağrılması.

, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Bir ileti tanınmadığında bile belirli bir sözleşmede tüm iletiler için kanal veya uç nokta dağıtıcısına müdahale etmenizi ve genişletmenizi sağlar. Bir ileti geldiğinde, bu bir ileti geldiğinde, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> özelliği tarafından döndürülen işleme gönderilir. Belirli bir işlemin tüm iletilerini kesme veya genişletme için, <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfına bakın.

<xref:System.ServiceModel.Dispatcher.DispatchRuntime> Sınıf tarafından sunulan dağıtıcı genişletilebilirliği dört ana alanı vardır:

1. Kanal bileşenleri, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> kanal dağıtıcısında kanalları kabul etme ve kapatma şeklini özelleştirmek için <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> özelliği tarafından döndürülen ilişkili kanal dağıtıcılarından ve özelliklerini kullanır. Bu kategori, <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> özelliklerini içerir.

2. İleti bileşenleri, işlenen her ileti için özelleştirilir. <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>Bu kategori <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> ,<xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>,, ve<xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> özelliklerini içerir.

3. Örnek bileşenleri, hizmet türü örneklerinin oluşturulmasını, ömrünü ve elden çıkarılmasını özelleştirir. Hizmet nesnesi yaşam süreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> . özelliği. Bu kategori, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> ve özelliklerini içerir.

4. Güvenlikle ilgili bileşenler aşağıdaki özellikleri kullanabilir:

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>Denetim olaylarının yazıldığı yeri belirtir.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A>hizmetin, gelen ileti tarafından belirtilen kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmadığını denetler.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A>başarılı ileti kimlik doğrulama olaylarının tarafından <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>belirtilen olay günlüğüne yazılıp yazılmadığını denetler.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A><xref:System.Threading.Thread.CurrentPrincipal%2A> özelliğin nasıl ayarlandığını denetler.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A>Yetkilendirme olaylarının denetimini nasıl gerçekleştirileceğini belirtir.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A>günlüğe kaydetme işlemi sırasında oluşan kritik olmayan özel durumların engellenip engellenmeyeceğini belirtir.

Genellikle, özel uzantı nesneleri bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özelliğe atanır veya bir hizmet davranışı (uygulayan <xref:System.ServiceModel.Description.IServiceBehavior>bir nesne), bir sözleşme davranışı (uygulayan <xref:System.ServiceModel.Description.IContractBehavior>bir nesne) veya bir uç nokta tarafından koleksiyona eklenir davranış (uygulayan <xref:System.ServiceModel.Description.IEndpointBehavior>bir nesne). Daha sonra yükleme davranışı nesnesi, programlı bir şekilde veya bir uygulama yapılandırma dosyası kullanılarak bir davranışın eklenmesine olanak tanımak <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> için özel bir nesne uygulayarak, uygun davranış koleksiyonuna eklenir.

Çift yönlü istemciler (bir çift yönlü hizmet tarafından belirtilen bir geri çağırma anlaşması uygulayan istemciler), <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> özelliği kullanılarak erişilebilen bir nesneye de sahiptir.

### <a name="using-the-dispatchoperation-class"></a>DispatchOperation sınıfını kullanma

<xref:System.ServiceModel.Dispatcher.DispatchOperation> Sınıfı, çalışma zamanı değişikliklerinin ve yalnızca bir hizmet işlemi kapsamındaki özel uzantılar için ekleme noktasının konumudur. (Bir sözleşmede tüm iletiler için hizmet çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfını kullanın.)

Özel <xref:System.ServiceModel.Dispatcher.DispatchOperation> bir hizmet davranışı nesnesi kullanarak değişiklikleri yükler.

Belirli bir hizmet işlemini temsil eden <xref:System.ServiceModel.Dispatcher.DispatchOperation> nesneyi bulmak için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>

Aşağıdaki özellikler çalışma zamanı yürütme işlemini işlem düzeyinde denetler:

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A> ,<xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A> ,,<xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> , Ve özellikleri işlem için ilgili değerleri elde eder. <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> Ve<xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> işlem davranışını belirtin.

- Ve özellikleri, Kullanıcı tanımlı <xref:System.ServiceModel.InstanceContext>hizmet nesnesinin öğesine göre ömrünü denetler. <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, Veözellikleri<xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> iletilerden nesnelere ve nesnelere dönüştürme üzerinde açık denetimi etkinleştirir. <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Özelliği, işlem kimliğe bürünme düzeyini belirtir.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Özelliği, işlem için özel çağrı bağlamı uzantıları ekler.

- Parametre nesneleri yok edildiğinde özelliğidenetler.<xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A>

- Özel bir Invoker nesnesi eklemek için özelliği.<xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A>

- Özelliği <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> , parametreleri incelemek veya değiştirmek için kullanabileceğiniz özel bir parametre denetçisi eklemenize olanak sağlar ve değerleri döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Nasıl yapılır: Hizmette Iletileri İnceleme ve değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [Nasıl yapılır: Parametreleri İnceleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [Nasıl yapılır: Kuruluştaki uç noktaları kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
