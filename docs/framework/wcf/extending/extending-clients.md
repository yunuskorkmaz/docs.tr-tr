---
title: İstemcileri Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: b3bbbdb895576b4a6d9167bcf321a99d10d378cc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249299"
---
# <a name="extending-clients"></a>İstemcileri Genişletme

Çağıran bir uygulamada, hizmet modeli katmanı, uygulama kodundaki Yöntem etkinleştirmeleri ' ı giden iletilere çevirmekten, bunları temel kanallara dağıtmaya, sonuçları döndürülen değerlere ve çıkış parametrelerine geri çevirmeye ve sonuçları çağırana geri döndürecek sorumludur. Hizmet modeli uzantıları, istemci veya dağıtıcı işlevselliği, özel davranışlar, ileti ve parametre yakaalımı ve diğer genişletilebilirlik işlevleriyle ilgili yürütme veya iletişim davranışlarını ve özellikleri değiştirir veya uygular.  
  
 Bu konu, <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientOperation> bir WCF istemcisinin varsayılan yürütme davranışını değiştirmek veya ileti, parametre veya dönüş değerlerini kanal katmanından göndermeden veya ondan önce almak ya da değiştirmek için WINDOWS COMMUNICATION FOUNDATION (WCF) istemci uygulamasında ve sınıflarının nasıl kullanılacağını açıklar. Hizmet çalışma zamanını genişletme hakkında daha fazla bilgi için bkz. [dispatchers 'ı genişletme](extending-dispatchers.md). Özelleştirme nesnelerini istemci çalışma zamanına değiştirme ve ekleme davranışları hakkında daha fazla bilgi için, bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>İstemciler  

 Bir istemcide, WCF istemci nesnesi veya istemci kanalı, Yöntem çağrılarını giden iletilere ve gelen iletileri çağıran uygulamaya döndürülen işlem sonuçlarına dönüştürür. (İstemci türleri hakkında daha fazla bilgi için bkz. [WCF Istemci mimarisi](../feature-details/client-architecture.md).)  
  
 WCF istemci türlerinde, bu uç noktayı ve işlem düzeyi işlevselliğini işleyen çalışma zamanı türleri vardır. Bir uygulama bir işlem çağırdığında, <xref:System.ServiceModel.Dispatcher.ClientOperation> giden nesneleri bir iletiye çevirir, işlem yakalayıcılar, giden çağrının hedef sözleşmeye uygun olduğunu onaylar ve giden <xref:System.ServiceModel.Dispatcher.ClientRuntime> kanalı (ve çift yönlü hizmetler söz konusu olduğunda gelen kanallar) oluşturup yönetmekten ve ek giden ileti işlemeyi (üst bilgi değişikliği gibi) işleme, her iki yönde de ileti yakalayıcılar işleme ve ilgili istemci tarafı nesnesi için gelen çift yönlü çağrıları yönlendirme işlemlerinden sorumludur <xref:System.ServiceModel.Dispatcher.DispatchRuntime> . , <xref:System.ServiceModel.Dispatcher.ClientOperation> Ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> iletileri (hatalar dahil) istemciye döndürüldüğünde her ikisi de benzer hizmetleri sağlar.  
  
 Bu iki çalışma zamanı sınıfı, WCF istemci nesnelerinin ve kanallarının işlenmesini özelleştirmek için ana uzantıdır. <xref:System.ServiceModel.Dispatcher.ClientRuntime>Sınıfı, kullanıcıların sözleşmede bulunan tüm iletilerde istemci yürütmesini kesmesini ve genişletmelerine olanak sağlar. <xref:System.ServiceModel.Dispatcher.ClientOperation>Sınıfı, kullanıcıların belirli bir işlemdeki tüm iletiler için istemci yürütmeyi kesmesini ve genişletmelerine olanak sağlar.  
  
 Özellikleri değiştirme veya özelleştirmeler ekleme, sözleşme, uç nokta ve işlem davranışları kullanılarak yapılır. İstemci çalışma zamanı özelleştirmelerini gerçekleştirmek üzere bu tür davranışları kullanma hakkında daha fazla bilgi için, bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Senaryolar  

 İstemci sistemini genişletmek için aşağıdakiler de dahil olmak üzere birkaç neden vardır:  
  
- Özel Ileti doğrulaması. Bir Kullanıcı belirli bir şema için bir iletinin geçerli olduğunu zorlamak isteyebilir. Bu, <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi uygulayarak ve uygulamaya uygulama atanarak yapılabilir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> . Örnekler için bkz. [nasıl yapılır: Istemcideki Iletileri İnceleme ve değiştirme](how-to-inspect-or-modify-messages-on-the-client.md) ve [nasıl yapılır: istemcideki Iletileri İnceleme veya değiştirme](how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Özel Ileti günlüğü. Bir Kullanıcı bir uç nokta aracılığıyla akan bazı uygulama iletilerinin bir kümesini incelemek ve günlüğe kaydetmek isteyebilir. Bu, ileti yakalayıcısı arabirimleriyle de gerçekleştirilebilir.  
  
- Özel Ileti dönüşümleri. Uygulama kodunu değiştirmek yerine, Kullanıcı çalışma zamanındaki iletiye belirli dönüştürmeleri uygulamak isteyebilir (örneğin, sürüm oluşturma için). Bu, ileti yakalayıcısı arabirimleriyle birlikte gerçekleştirilebilir.  
  
- Özel veri modeli. Kullanıcı, WCF (yani,, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ve nesneler) için varsayılan olarak desteklenenlerden farklı bir veri veya serileştirme modeli olmasını isteyebilir <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> . Bu, ileti biçimlendirici arabirimlerini uygulayarak yapılabilir. Daha fazla bilgi için bkz <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> . ve <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> özelliği.  
  
- Özel parametre doğrulaması. Kullanıcı, yazılan parametrelerin geçerli olduğunu (XML 'nin aksine) zorlamak isteyebilir. Bu işlem, parametre denetçisi arabirimleri kullanılarak yapılabilir. Bir örnek için bkz. [nasıl yapılır: parametreleri](how-to-inspect-or-modify-parameters.md) veya [istemci doğrulamasını](../samples/client-validation.md)İnceleme veya değiştirme.  
  
### <a name="using-the-clientruntime-class"></a>ClientRuntime sınıfını kullanma  

 <xref:System.ServiceModel.Dispatcher.ClientRuntime>Sınıfı, iletileri denetleyen ve istemci davranışını genişleten uzantı nesneleri ekleyebileceğiniz bir genişletilebilirlik noktasıdır. Yakalatma nesneleri belirli bir sözleşmede bulunan tüm iletileri işleyebilir, belirli işlemler için yalnızca iletileri işleyebilir, özel kanal başlatması gerçekleştirebilir ve diğer özel istemci uygulaması davranışını uygulayabilir.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>Özelliği, hizmet tarafından başlatılan geri arama istemcileri için dağıtım çalışma zamanı nesnesini döndürür.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A>Özelliği özel bir işlem Seçici nesnesini kabul eder.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A>Özelliği, istemci kanalını incelemenize veya değiştirebilmesine izin veren bir kanal başlatıcısı eklenmesini mümkün bir şekilde sunar.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A>Özelliği, <xref:System.ServiceModel.Dispatcher.ClientOperation> Bu işlemin iletilerine özgü işlevselliği sağlayan özel ileti yakalayıcılar ekleyebileceğiniz bir nesne koleksiyonu alır.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A>Özelliği, bir uygulamanın adresleme 'yi doğrudan denetlemek için bazı otomatik adresleme üstbilgilerini kapatmasına olanak sağlar.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A>Özelliği, aracıları ve diğer senaryoları desteklemek için aktarım düzeyindeki iletinin hedefinin değerini ayarlar.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A>Özelliği, <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> bir WCF istemcisi aracılığıyla seyahat eden tüm iletiler için özel ileti yakalayıcılar ekleyebileceğiniz bir nesne koleksiyonu alır.  
  
 Ayrıca, sözleşme bilgilerini alan bazı diğer özellikler vardır:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 WCF istemcisi çift yönlü bir WCF istemcise, aşağıdaki özellikler geri çağırma WCF istemci bilgilerini de alır:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 WCF istemci yürütülmesini tüm WCF istemcisi genelinde genişletmek için, <xref:System.ServiceModel.Dispatcher.ClientRuntime> bir özelliğin değiştirilip değiştirilmediğini veya bir arabirimin uygulanıp uygulanmadığını ve aradığınız işlevselliği oluşturup bir özelliğe eklemeyi görmek için sınıfta bulunan özellikleri gözden geçirin. Oluşturmak için belirli bir uzantıyı seçtikten sonra, <xref:System.ServiceModel.Dispatcher.ClientRuntime> çağrıldığında sınıfa erişim sağlayan bir istemci davranışı uygulayarak uzantınızı uygun özelliğe ekleyin <xref:System.ServiceModel.Dispatcher.ClientRuntime> .  
  
 Bir işlem davranışı (uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior> ), bir anlaşma davranışı (uygulayan bir nesne) <xref:System.ServiceModel.Description.IContractBehavior> veya bir uç nokta davranışı (uygulayan bir nesne) kullanarak bir koleksiyona özel uzantı nesneleri ekleyebilirsiniz <xref:System.ServiceModel.Description.IEndpointBehavior> . Yükleme davranışı nesnesi, programlı olarak, bildirimli olarak (özel bir öznitelik uygulayarak) veya <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> bir uygulama yapılandırma dosyası kullanılarak davranışın eklenmesine olanak tanımak için özel bir nesne uygulayarak, uygun davranış koleksiyonuna eklenir. Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Bir WCF istemcisi genelinde yakalaşmayı gösteren örnekler için bkz. [nasıl yapılır: Istemcideki Iletileri İnceleme veya değiştirme](how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Clienentoperation sınıfını kullanma  

 <xref:System.ServiceModel.Dispatcher.ClientOperation>Sınıfı, istemci çalışma zamanı değişikliklerinin ve yalnızca bir hizmet işlemi kapsamındaki özel uzantılar için ekleme noktasının konumudur. (Bir sözleşmede bulunan tüm iletiler için istemci çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfını kullanın.)  
  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> <xref:System.ServiceModel.Dispatcher.ClientOperation> Belirli bir hizmet işlemini temsil eden nesneyi bulmak için özelliğini kullanın. Aşağıdaki özellikler, WCF istemci sistemine özel nesneler ekleme olanağı sağlar:  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Bir işlem için özel uygulama eklemek veya geçerli biçimlendirici değiştirmek için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A>Özel bir <xref:System.ServiceModel.Dispatcher.IParameterInspector> uygulama eklemek veya geçerli olanı değiştirmek için özelliğini kullanın.  
  
 Aşağıdaki özellikler, biçimlendirici ve özel parametre denetçiler ile etkileşime sahip sistemi değiştirmenize olanak sağlar:  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A>Bir giden iletinin serileştirmesini denetlemek için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A>Bir gelen iletinin serisini kaldırma özelliğini denetlemek için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A>İstek iletisinin WS-Addressing eylemini denetlemek için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> Hangi WCF istemci yöntemlerinin zaman uyumsuz bir işlemle ilişkilendirildiğini belirtmek için ve kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A>Ayrıntı türü olarak SOAP hatalarıyla görünebilen türleri içeren bir koleksiyon almak için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> İşlem çağrıldığında, bir oturumun başlatılıp başlatılmayacağını veya bozuk olup olmadığını denetlemek için ve özelliklerini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A>İşlemin tek yönlü bir işlem olup olmadığını denetlemek için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A>İçeren nesneyi almak için özelliğini kullanın <xref:System.ServiceModel.Dispatcher.ClientRuntime> .  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A>İşlemin adını almak için özelliğini kullanın.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A>Hangi yöntemin işleme eşlendiğini denetlemek için özelliğini kullanın.  
  
 WCF istemci yürütülmesini yalnızca bir hizmet işlemi genelinde genişletmek için, <xref:System.ServiceModel.Dispatcher.ClientOperation> bir özelliğin değiştirilip etkinleştirilmeyeceğini veya bir arabirimin uygulanıp yüklenmediğini ve bu özelliği bir özelliğe ekleyerek Aradığınız işlevselliği oluşturduğunu görmek için sınıfta bulunan özellikleri gözden geçirin. Oluşturmak için belirli bir uzantıyı seçtikten sonra, <xref:System.ServiceModel.Dispatcher.ClientOperation> çağrıldığında sınıfa erişim sağlayan bir istemci davranışı uygulayarak uzantınızı uygun özelliğe ekleyin <xref:System.ServiceModel.Dispatcher.ClientOperation> . Bu davranışın içinde, <xref:System.ServiceModel.Dispatcher.ClientRuntime> özelliği gereksinimlerinize uyacak şekilde değiştirebilirsiniz.  
  
 Genellikle, bir işlem davranışı uygulamak (arabirimi uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior> ), ancak <xref:System.ServiceModel.Description.OperationDescription> belirli bir işlem için öğesini bularak ve davranışı ekleyerek aynı şeyi gerçekleştirmek için uç nokta davranışlarını ve Sözleşme davranışlarını da kullanabilirsiniz. Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Yapılandırmadan özel davranışınızı kullanmak için özel bir davranış yapılandırması bölüm işleyicisi kullanarak davranışınızı yüklemelisiniz. Ayrıca, özel bir öznitelik oluşturarak davranışınızı yükleyebilirsiniz.  
  
 Bir WCF istemcisi genelinde yakalaşmayı gösteren örnekler için bkz. [nasıl yapılır: parametreleri İnceleme veya değiştirme](how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme](how-to-inspect-or-modify-messages-on-the-client.md)
- [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](how-to-inspect-or-modify-parameters.md)
