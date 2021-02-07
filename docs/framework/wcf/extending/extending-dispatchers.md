---
description: 'Daha fazla bilgi edinin: dispatchers genişletiliyor'
title: Dağıtıcıları Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 22be85c57439a88746e3e87625472d02ab412c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735289"
---
# <a name="extending-dispatchers"></a>Dağıtıcıları Genişletme

Dispatchler, temel alınan kanallara ait gelen iletileri çekmekten, bunları uygulama kodundaki yöntem çağırmaları içine çevirerek ve sonuçları çağırana geri gönderen sorumludurlar. Dağıtıcı uzantıları bu işlemeyi değiştirmenize izin verir.  İletilerin veya parametrelerin içeriğini denetleyen veya değiştiren ileti ya da parametre Inspectors uygulayabilirsiniz.  İletilerin işlemlere yönlendirilme biçimini değiştirebilir veya başka bir işlevsellik sağlayabilirsiniz.

Bu konu, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> bir dağıtıcı 'ın varsayılan yürütme davranışını değiştirmek veya iletileri, parametreleri ya da kanal katmanından gönderilmeden veya geri alınmadan önce ileti, parametre ya da dönüş değerlerini almak ya da değiştirmek için WINDOWS COMMUNICATION FOUNDATION (WCF) hizmet uygulamasında ve sınıflarının nasıl kullanılacağını açıklar. Eşdeğer istemci çalışma zamanı iletisi işleme hakkında daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md). <xref:System.ServiceModel.IExtensibleObject%601>Farklı çalışma zamanı özelleştirme nesneleri arasında paylaşılan duruma erişirken, türlerin hangi rol üzerinde çalındığını anlamak için bkz. [Genişletilebilir nesneler](extensible-objects.md).

## <a name="dispatchers"></a>Dağıtıcılarının yerini alabilir

Hizmet modeli katmanı, geliştiricilerin programlama modeli ve genellikle kanal katmanı olarak adlandırılan temel ileti değişimi arasında dönüştürme işlemini gerçekleştirir. WCF 'de kanal ve uç nokta sevkiyatcıları ( <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ve <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sırasıyla), yeni kanalları kabul etme, iletileri alma, işlem gönderme ve çağırma ve yanıt işleme işlemlerinin sorumlu olduğu hizmet bileşenleridir. Dağıtıcı nesneleri alıcı nesneleridir, ancak çift yönlü hizmetlerdeki geri çağırma sözleşmesi uygulamaları da denetim, değişiklik veya uzantı için Dispatcher nesnelerini kullanıma sunar.

Kanal dağıtıcısı (ve Yardımcısı <xref:System.ServiceModel.Channels.IChannelListener> ), iletileri düşük kanaldan alıp iletileri ilgili uç noktası dağıtıcıları 'na geçirir. Her uç nokta dağıtıcılarının, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> işlemi uygulayan yöntemi çağırmaktan sorumlu olan iletileri uygun bir şekilde yönlendirdiğini vardır. Çeşitli isteğe bağlı ve gerekli uzantı sınıfları, bu şekilde çağrılır. Bu konu, bu parçaların nasıl bir araya uyduğunu ve temel işlevselliği genişletmek için özellikleri nasıl değiştirebileceğinizi ve içindeki kodunuzu nasıl kullanabileceğinizi açıklar.

Dağıtıcı özellikleri ve değiştirilmiş özelleştirme nesneleri, hizmet, uç nokta, anlaşma veya işlem davranışı nesneleri kullanılarak eklenir. Bu konu, davranışların nasıl kullanılacağını tanımlamaz. Dağıtıcı değişikliklerini eklemek için kullanılan türler hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).

Aşağıdaki grafik, bir hizmette mimari öğelerin üst düzey bir görünümünü sağlar.

![Dağıtım çalışma zamanı mimarisi](./media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")

### <a name="channel-dispatchers"></a>Kanal Sevkiyatcıları

<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> <xref:System.ServiceModel.Channels.IChannelListener> Belırlı bir URI 'nin (dinleme URI 'si olarak adlandırılır) bir hizmetin örneğiyle ilişkilendirilmesi için bir nesne oluşturulur. Her <xref:System.ServiceModel.ServiceHost> nesne <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> , her biri yalnızca bir dinleyici ve dinleme URI 'siyle ilişkili birçok nesneye sahip olabilir. Bir ileti geldiğinde, her bir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> ilişkili <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneyi, uç noktanın iletiyi kabul edip etmediğini sorgular ve iletiyi ' a iletir.

Bir kanal oturumunun ömrünü ve davranışını denetleyen tüm özellikler, nesne üzerinde denetleme veya değiştirme için kullanılabilir <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> . Bunlar özel kanal başlatıcıları, kanal dinleyicisi, ana bilgisayar, ilişkili vb. içerir <xref:System.ServiceModel.InstanceContext> .

### <a name="endpoint-dispatchers"></a>Endpoint Dispatchler

<xref:System.ServiceModel.Dispatcher.EndpointDispatcher>Nesne <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> , bir iletinin hedef adresi ile eşleştiğinde <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> ve ileti eylemi özelliği ile eşleştiğinde bir öğesinden gelen iletileri işlemeden sorumludur <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> . İki <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesne bir iletiyi kabul edebiliyorsanız, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> özellik değeri daha yüksek öncelikli uç noktayı belirler.

, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> Dağıtıcısı işlemini özelleştirmek için kullanabileceğiniz iki ana hizmet modeli uzantı noktasını (ve sınıfları) almak için kullanın. <xref:System.ServiceModel.Dispatcher.DispatchRuntime>Sınıfı, kullanıcıların dağıtıcıyı anlaşma kapsamında (yani, bir sözleşmede bulunan tüm iletiler için) kesmesini ve genişletmesini sağlar. <xref:System.ServiceModel.Dispatcher.DispatchOperation>Sınıfı, kullanıcıların dağıtıcı bir işlem kapsamında (yani bir işlemdeki tüm iletiler için) kesmesini ve genişletmesine olanak tanır.

## <a name="scenarios"></a>Senaryolar

Dağıtıcısı genişletecek birkaç neden vardır:

- Özel Ileti doğrulaması. Kullanıcılar, belirli bir şema için bir iletinin geçerli olduğunu zorlayabilir. Bu işlem, ileti yakalayıcı arabirimlerini uygulayarak yapılabilir. Bir örnek için bkz. [ileti](../samples/message-inspectors.md)denetçiler.

- Özel Ileti günlüğü. Kullanıcılar bir uç nokta aracılığıyla akan bazı uygulama iletilerini inceleyebilir ve günlüğe kaydedebilir. Bu, ileti yakalayıcısı arabirimleriyle de gerçekleştirilebilir.

- Özel Ileti dönüşümleri. Kullanıcılar çalışma zamanındaki iletiye bazı dönüşümler uygulayabilir (örneğin, sürüm oluşturma için). Bu, ileti yakalayıcısı arabirimleriyle birlikte gerçekleştirilebilir.

- Özel veri modeli. Kullanıcılar, WCF 'de varsayılan olarak desteklenenden farklı bir veri serileştirme modeline sahip olabilir (yani, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> , <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> , ve ham iletiler). Bu, ileti biçimlendirici arabirimlerini uygulayarak yapılabilir. Bir örnek için bkz. [Işlem biçimlendirici ve Işlem seçici](../samples/operation-formatter-and-operation-selector.md).

- Özel parametre doğrulaması. Kullanıcılar, yazılan parametrelerin geçerli olduğunu (XML 'nin aksine) zorunlu kılabilir. Bu işlem, parametre denetçisi arabirimleri kullanılarak yapılabilir.

- Özel Işlem gönderme. Kullanıcılar, örneğin gövde öğesinde veya özel bir ileti özelliğinde, eylem dışında bir şeye gönderme işlemini uygulayabilir. Bu, arabirimi kullanılarak yapılabilir <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> . Bir örnek için bkz. [Işlem biçimlendirici ve Işlem seçici](../samples/operation-formatter-and-operation-selector.md).

- Nesne havuzu oluşturma. Kullanıcılar, her çağrı için yeni bir tane ayırmak yerine, örnekleri havuza alabilir. Bu, örnek sağlayıcı arabirimleri kullanılarak uygulanabilir. Bir örnek için bkz. [Pooling](../samples/pooling.md).

- Örnek Kiralama. Kullanıcılar, .NET Framework uzaktan Iletişim ile benzer örnek ömrü için bir kiralama stili uygulayabilir. Bu, örnek bağlam ömrü arabirimleri kullanılarak yapılabilir.

- Özel hata Işleme. Kullanıcılar, yerel hataların nasıl işlendiğini ve hataların istemcilere nasıl geri iletildiğini denetleyebilir. Bu, arabirimler kullanılarak uygulanabilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> .

- Özel yetkilendirme davranışları. Kullanıcılar, sözleşmenin veya Işlemin çalışma zamanı parçalarını genişleterek ve iletideki belirteçleri temel alarak güvenlik denetimleri ekleyerek özel erişim denetimi uygulayabilir. Bu, ileti yakalayıcısı ya da parametre yakalayıcısı arabirimleri kullanılarak yapılabilir. Örnekler için bkz. [güvenlik genişletilebilirliği](../samples/security-extensibility.md).

  > [!CAUTION]
  > Güvenlik özelliklerinin değiştirilmesi, WCF uygulamalarının güvenliğinin aşılmasına neden olduğundan, dağıtıma karşı güvenlikle ilgili değişiklikler yapmanız ve dağıtımdan önce kapsamlı test yapmanız önerilir.

- Özel WCF çalışma zamanı Doğrulayıcıları. WCF uygulamalarına göre kurumsal düzeyde ilkeleri zorlamak için Hizmetleri, sözleşmeleri ve bağlamaları incelemek üzere özel doğrulayıcılar yükleyebilirsiniz. (Örneğin, bkz. [nasıl yapılır: kuruluştaki uç noktaları kilitleme](how-to-lock-down-endpoints-in-the-enterprise.md).)

### <a name="using-the-dispatchruntime-class"></a>DispatchRuntime sınıfını kullanma

<xref:System.ServiceModel.Dispatcher.DispatchRuntime>Bir hizmetin veya tek bir uç noktanın varsayılan davranışını değiştirmek ya da aşağıdaki hizmet işlemlerinin birine veya her ikisine de (bir çift yönlü istemci durumunda istemci süreçlerine) özel değişiklikler uygulayan nesneler eklemek için sınıfını kullanın:

- Gelen iletilerin nesnelere dönüştürülmesi ve bu nesneleri bir hizmet nesnesi üzerinde yöntem çağırma olarak serbest bırakma.

- Bir hizmet işleminin yanıtından alınan nesnelerinin giden iletilere çağrılması.

, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Bir ileti tanınmadığında bile belirli bir sözleşmede tüm iletiler için kanal veya uç nokta dağıtıcısına müdahale etmenizi ve genişletmenizi sağlar. Bir ileti geldiğinde, bu bir ileti geldiğinde, özelliği tarafından döndürülen işleme gönderilir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> . Belirli bir işlemin tüm iletilerini kesme veya genişletme için, <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfına bakın.

Sınıf tarafından sunulan dağıtıcı genişletilebilirliği dört ana alanı vardır <xref:System.ServiceModel.Dispatcher.DispatchRuntime> :

1. Kanal bileşenleri, <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> Kanal dağıtıcısında kanalları kabul etme ve kapatma şeklini özelleştirmek için özelliği tarafından döndürülen ilişkili kanal dağıtıcılarından ve özelliklerini kullanır. Bu kategori, <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> özelliklerini içerir.

2. İleti bileşenleri, işlenen her ileti için özelleştirilir. Bu kategori,, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> , <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> ve <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> özelliklerini içerir.

3. Örnek bileşenleri, hizmet türü örneklerinin oluşturulmasını, ömrünü ve elden çıkarılmasını özelleştirir. Hizmet nesnesi yaşam süreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> . özelliği. Bu kategori, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> ve özelliklerini içerir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> .

4. Güvenlikle ilgili bileşenler aşağıdaki özellikleri kullanabilir:

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> Denetim olaylarının yazıldığı yeri belirtir.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> hizmetin, gelen ileti tarafından belirtilen kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmadığını denetler.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> başarılı ileti kimlik doğrulama olaylarının tarafından belirtilen olay günlüğüne yazılıp yazılmadığını denetler <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> .

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A><xref:System.Threading.Thread.CurrentPrincipal%2A>özelliğin nasıl ayarlandığını denetler.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Yetkilendirme olaylarının denetimini nasıl gerçekleştirileceğini belirtir.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> günlüğe kaydetme işlemi sırasında oluşan kritik olmayan özel durumların engellenip engellenmeyeceğini belirtir.

Genellikle, özel uzantı nesneleri bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özelliğe atanır veya bir hizmet davranışı (uygulayan bir nesne <xref:System.ServiceModel.Description.IServiceBehavior> ), bir anlaşma davranışı (uygulayan bir nesne) <xref:System.ServiceModel.Description.IContractBehavior> veya bir uç nokta davranışı (uygulayan bir nesne) tarafından bir koleksiyona eklenir <xref:System.ServiceModel.Description.IEndpointBehavior> . Daha sonra yükleme davranışı nesnesi, programlı bir şekilde veya bir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> uygulama yapılandırma dosyası kullanılarak bir davranışın eklenmesine olanak tanımak için özel bir nesne uygulayarak, uygun davranış koleksiyonuna eklenir.

Çift yönlü istemciler (bir çift yönlü hizmet tarafından belirtilen bir geri çağırma anlaşması uygulayan istemciler) <xref:System.ServiceModel.Dispatcher.DispatchRuntime> , özelliği kullanılarak erişilebilen bir nesneye de sahiptir <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> .

### <a name="using-the-dispatchoperation-class"></a>DispatchOperation sınıfını kullanma

<xref:System.ServiceModel.Dispatcher.DispatchOperation>Sınıfı, çalışma zamanı değişikliklerinin ve yalnızca bir hizmet işlemi kapsamındaki özel uzantılar için ekleme noktasının konumudur. (Bir sözleşmede tüm iletiler için hizmet çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfını kullanın.)

<xref:System.ServiceModel.Dispatcher.DispatchOperation>Özel bir hizmet davranışı nesnesi kullanarak değişiklikleri yükler.

<xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation> Belirli bir hizmet işlemini temsil eden nesneyi bulmak için özelliğini kullanın.

Aşağıdaki özellikler çalışma zamanı yürütme işlemini işlem düzeyinde denetler:

- ,,,, <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> özellikleri işlem için ilgili değerleri elde eder.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A>Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> işlem davranışını belirtin.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A>Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> Özellikleri, Kullanıcı tanımlı hizmet nesnesinin öğesine göre ömrünü denetler <xref:System.ServiceModel.InstanceContext> .

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A> Ve <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> özellikleri iletilerden nesnelere ve nesnelere dönüştürme üzerinde açık denetimi etkinleştirir.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A>Özelliği, işlem kimliğe bürünme düzeyini belirtir.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A>Özelliği, işlem için özel çağrı bağlamı uzantıları ekler.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A>Parametre nesneleri yok edildiğinde özelliği denetler.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A>Özel bir Invoker nesnesi eklemek için özelliği.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A>Özelliği, parametreleri incelemek veya değiştirmek için kullanabileceğiniz özel bir parametre denetçisi eklemenize olanak sağlar ve değerleri döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme](how-to-inspect-and-modify-messages-on-the-service.md)
- [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](how-to-inspect-or-modify-parameters.md)
- [Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme](how-to-lock-down-endpoints-in-the-enterprise.md)
