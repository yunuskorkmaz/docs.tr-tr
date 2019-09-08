---
title: İstemcileri Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 91277e1a4d0a1d001d62d677dbd087bec5d875f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797170"
---
# <a name="extending-clients"></a>İstemcileri Genişletme
Çağıran bir uygulamada, hizmet modeli katmanı, uygulama kodundaki Yöntem çağrılarını giden iletilere çevirmekten, bunları temeldeki kanallara ileterek, sonuçları döndürülen değerlere ve çıkış parametrelerine geri çevirmeye sorumludur. uygulama kodu ve sonuçları çağırana geri döndürülüyor. Hizmet modeli uzantıları, istemci veya dağıtıcı işlevselliği, özel davranışlar, ileti ve parametre yakaalımı ve diğer genişletilebilirlik işlevleriyle ilgili yürütme veya iletişim davranışlarını ve özellikleri değiştirir veya uygular.  
  
 Bu konu, <xref:System.ServiceModel.Dispatcher.ClientRuntime> bir WCF istemcisinin varsayılan yürütme <xref:System.ServiceModel.Dispatcher.ClientOperation> davranışını değiştirmek veya iletileri, parametreleri ya da dönüş değerlerini kesme ya da değiştirme için bir Windows Communication Foundation (WCF) istemci uygulamasında ve sınıflarının nasıl kullanılacağını açıklar veya daha sonra kanal katmanından gönderilmeden önce. Hizmet çalışma zamanını genişletme hakkında daha fazla bilgi için bkz. [dispatchers 'ı genişletme](extending-dispatchers.md). Özelleştirme nesnelerini istemci çalışma zamanına değiştirme ve ekleme davranışları hakkında daha fazla bilgi için, bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>İstemciler  
 Bir istemcide, WCF istemci nesnesi veya istemci kanalı, Yöntem çağrılarını giden iletilere ve gelen iletileri çağıran uygulamaya döndürülen işlem sonuçlarına dönüştürür. (İstemci türleri hakkında daha fazla bilgi için bkz. [WCF Istemci mimarisi](../feature-details/client-architecture.md).)  
  
 WCF istemci türlerinde, bu uç noktayı ve işlem düzeyi işlevselliğini işleyen çalışma zamanı türleri vardır. Bir uygulama bir işlem <xref:System.ServiceModel.Dispatcher.ClientOperation> çağırdığında, giden nesneleri bir iletiye çevirir, bu işlem, dinleyici, giden çağrının hedef sözleşmeye uygun olduğunu onaylar ve giden iletiyi <xref:System.ServiceModel.Dispatcher.ClientRuntime> giden kanalları (ve çift yönlü hizmetler söz konusu olduğunda gelen kanallar) oluşturma ve yönetme, ek giden ileti işlemeyi işleme (başlık değişikliği gibi), her iki yönde de ileti yakalayıcılar işleme ve gelen yönlendirme uygun istemci tarafı <xref:System.ServiceModel.Dispatcher.DispatchRuntime> nesnesine çift yönlü çağrılar. , <xref:System.ServiceModel.Dispatcher.ClientOperation> Ve<xref:System.ServiceModel.Dispatcher.ClientRuntime> iletileri (hatalar dahil) istemciye döndürüldüğünde her ikisi de benzer hizmetleri sağlar.  
  
 Bu iki çalışma zamanı sınıfı, WCF istemci nesnelerinin ve kanallarının işlenmesini özelleştirmek için ana uzantıdır. Sınıfı <xref:System.ServiceModel.Dispatcher.ClientRuntime> , kullanıcıların sözleşmede bulunan tüm iletilerde istemci yürütmesini kesmesini ve genişletmelerine olanak sağlar. Sınıfı <xref:System.ServiceModel.Dispatcher.ClientOperation> , kullanıcıların belirli bir işlemdeki tüm iletiler için istemci yürütmeyi kesmesini ve genişletmelerine olanak sağlar.  
  
 Özellikleri değiştirme veya özelleştirmeler ekleme, sözleşme, uç nokta ve işlem davranışları kullanılarak yapılır. İstemci çalışma zamanı özelleştirmelerini gerçekleştirmek üzere bu tür davranışları kullanma hakkında daha fazla bilgi için, bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Senaryolar  
 İstemci sistemini genişletmek için aşağıdakiler de dahil olmak üzere birkaç neden vardır:  
  
- Özel Ileti doğrulaması. Bir Kullanıcı belirli bir şema için bir iletinin geçerli olduğunu zorlamak isteyebilir. Bu, <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi uygulayarak ve uygulamaya uygulama <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> atanarak yapılabilir. Örnekler için bkz [. nasıl yapılır: İstemcideki](how-to-inspect-or-modify-messages-on-the-client.md) iletileri inceleyin veya değiştirin ve [şunları yapın: Istemcideki](how-to-inspect-or-modify-messages-on-the-client.md)Iletileri inceleyin veya değiştirin.  
  
- Özel Ileti günlüğü. Bir Kullanıcı bir uç nokta aracılığıyla akan bazı uygulama iletilerinin bir kümesini incelemek ve günlüğe kaydetmek isteyebilir. Bu, ileti yakalayıcısı arabirimleriyle de gerçekleştirilebilir.  
  
- Özel Ileti dönüşümleri. Uygulama kodunu değiştirmek yerine, Kullanıcı çalışma zamanındaki iletiye belirli dönüştürmeleri uygulamak isteyebilir (örneğin, sürüm oluşturma için). Bu, ileti yakalayıcısı arabirimleriyle birlikte gerçekleştirilebilir.  
  
- Özel veri modeli. Kullanıcı, WCF (yani <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>,, ve <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> nesneler) için varsayılan olarak desteklenenlerden farklı bir veri veya serileştirme modeli olmasını isteyebilir. Bu, ileti biçimlendirici arabirimlerini uygulayarak yapılabilir. Daha fazla bilgi için bkz <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> . <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> ve özelliği.  
  
- Özel parametre doğrulaması. Kullanıcı, yazılan parametrelerin geçerli olduğunu (XML 'nin aksine) zorlamak isteyebilir. Bu işlem, parametre denetçisi arabirimleri kullanılarak yapılabilir. Bir örnek için bkz [. nasıl yapılır: Parametreleri](how-to-inspect-or-modify-parameters.md) veya [istemci doğrulamasını](../samples/client-validation.md)inceleyin veya değiştirin.  
  
### <a name="using-the-clientruntime-class"></a>ClientRuntime sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Sınıfı, iletileri denetleyen ve istemci davranışını genişleten uzantı nesneleri ekleyebileceğiniz bir genişletilebilirlik noktasıdır. Yakalatma nesneleri belirli bir sözleşmede bulunan tüm iletileri işleyebilir, belirli işlemler için yalnızca iletileri işleyebilir, özel kanal başlatması gerçekleştirebilir ve diğer özel istemci uygulaması davranışını uygulayabilir.  
  
- Özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> , hizmet tarafından başlatılan geri arama istemcileri için dağıtım çalışma zamanı nesnesini döndürür.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Özelliği özel bir işlem Seçici nesnesini kabul eder.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Özelliği, istemci kanalını incelemenize veya değiştirebilmesine izin veren bir kanal başlatıcısı eklenmesini mümkün bir şekilde sunar.  
  
- Özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> , bu işlemin iletilerine özgü <xref:System.ServiceModel.Dispatcher.ClientOperation> işlevselliği sağlayan özel ileti yakalayıcılar ekleyebileceğiniz bir nesne koleksiyonu alır.  
  
- Özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> , bir uygulamanın adresleme 'yi doğrudan denetlemek için bazı otomatik adresleme üstbilgilerini kapatmasına olanak sağlar.  
  
- Özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> , aracıları ve diğer senaryoları desteklemek için aktarım düzeyindeki iletinin hedefinin değerini ayarlar.  
  
- Özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> , bir WCF istemcisi aracılığıyla <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> seyahat eden tüm iletiler için özel ileti yakalayıcılar ekleyebileceğiniz bir nesne koleksiyonu alır.  
  
 Ayrıca, sözleşme bilgilerini alan bazı diğer özellikler vardır:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 WCF istemcisi çift yönlü bir WCF istemcise, aşağıdaki özellikler geri çağırma WCF istemci bilgilerini de alır:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 WCF istemci yürütülmesini tüm WCF istemcisi genelinde genişletmek için, bir özelliğin değiştirilip değiştirilmediğini veya bir <xref:System.ServiceModel.Dispatcher.ClientRuntime> arabirimin uygulanıp uygulanmadığını ve aradığınız işlevselliği oluşturup bir özelliğe eklemeyi görmek için sınıfta bulunan özellikleri gözden geçirin. Oluşturmak için belirli bir uzantıyı seçtikten sonra, çağrıldığında <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfa erişim sağlayan bir istemci davranışı uygulayarak uzantınızı uygun özelliğe ekleyin.  
  
 Bir işlem davranışı (uygulayan <xref:System.ServiceModel.Description.IOperationBehavior>bir nesne), bir anlaşma davranışı (uygulayan <xref:System.ServiceModel.Description.IContractBehavior>bir nesne) veya bir uç nokta davranışı <xref:System.ServiceModel.Description.IEndpointBehavior> (uygulayan bir nesne) kullanarak bir koleksiyona özel uzantı nesneleri ekleyebilirsiniz. ). Yükleme davranışı nesnesi, programlı olarak, bildirimli olarak (özel bir öznitelik uygulayarak) veya bir özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> nesne uygulayarak, davranışı uygulama yapılandırma dosyası. Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Bir WCF istemcisi genelinde yakalaşmayı gösteren örnekler için bkz [. nasıl yapılır: Istemcideki](how-to-inspect-or-modify-messages-on-the-client.md)Iletileri inceleyin veya değiştirin.  
  
### <a name="using-the-clientoperation-class"></a>Clienentoperation sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Sınıfı, istemci çalışma zamanı değişikliklerinin ve yalnızca bir hizmet işlemi kapsamındaki özel uzantılar için ekleme noktasının konumudur. (Bir sözleşmede bulunan tüm iletiler için istemci çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfını kullanın.)  
  
 Belirli bir hizmet işlemini temsil eden <xref:System.ServiceModel.Dispatcher.ClientOperation> nesneyi bulmak için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Aşağıdaki özellikler, WCF istemci sistemine özel nesneler ekleme olanağı sağlar:  
  
- Bir işlem için özel <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> uygulama eklemek veya geçerli biçimlendirici değiştirmek için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> Özel<xref:System.ServiceModel.Dispatcher.IParameterInspector> bir uygulama eklemek veya geçerli olanı değiştirmek için özelliğini kullanın.  
  
 Aşağıdaki özellikler, biçimlendirici ve özel parametre denetçiler ile etkileşime sahip sistemi değiştirmenize olanak sağlar:  
  
- Bir giden iletinin serileştirmesini denetlemek için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A>  
  
- Bir gelen iletinin serisini kaldırma özelliğinidenetlemekiçinözelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A>  
  
- İstek iletisinin ws-Addressing eylemini denetlemek için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A>  
  
- Hangi WCF istemci <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> yöntemlerinin zaman uyumsuz bir işlemle ilişkilendirildiğini belirtmek için vekullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A>  
  
- Ayrıntı türü olarak SOAP hatalarıyla görünebilen türleri içeren bir koleksiyon almak için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A>  
  
- İşlem çağrıldığında, <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> bir oturumun başlatılıp başlatılmayacağını veya bozuk olup olmadığını denetlemek için veözelliklerinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A>  
  
- İşlemin tek yönlü bir işlem olup olmadığını denetlemek için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> İçeren<xref:System.ServiceModel.Dispatcher.ClientRuntime> nesneyi almak için özelliğini kullanın.  
  
- İşlemin adını almak için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A>  
  
- Hangi yöntemin işleme eşlendiğini denetlemek için özelliğinikullanın.<xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A>  
  
 WCF istemci yürütülmesini yalnızca bir hizmet işlemi genelinde genişletmek için, bir özelliğin değiştirilip etkinleştirilmeyeceğini veya bir <xref:System.ServiceModel.Dispatcher.ClientOperation> arabirimin uygulanıp yüklenmediğini ve bu özelliği bir özelliğe ekleyerek Aradığınız işlevselliği oluşturduğunu görmek için sınıfta bulunan özellikleri gözden geçirin. Oluşturmak için belirli bir uzantıyı seçtikten sonra, çağrıldığında <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıfa erişim sağlayan bir istemci davranışı uygulayarak uzantınızı uygun özelliğe ekleyin. Bu davranışın içinde, <xref:System.ServiceModel.Dispatcher.ClientRuntime> özelliği gereksinimlerinize uyacak şekilde değiştirebilirsiniz.  
  
 Genellikle, bir işlem davranışı uygulamak ( <xref:System.ServiceModel.Description.IOperationBehavior> arabirimi uygulayan bir nesne), ancak belirli bir için için öğesini bularak aynı şeyi gerçekleştirmek için uç nokta davranışlarını ve Sözleşme davranışlarını da kullanabilirsiniz. <xref:System.ServiceModel.Description.OperationDescription> işlem ve bu davranışı ekleme. Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Yapılandırmadan özel davranışınızı kullanmak için özel bir davranış yapılandırması bölüm işleyicisi kullanarak davranışınızı yüklemelisiniz. Ayrıca, özel bir öznitelik oluşturarak davranışınızı yükleyebilirsiniz.  
  
 Bir WCF istemcisi genelinde yakalaşmayı gösteren örnekler için bkz [. nasıl yapılır: Parametreleri](how-to-inspect-or-modify-parameters.md)inceleyin veya değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Nasıl yapılır: Istemcideki Iletileri inceleyin veya değiştirin](how-to-inspect-or-modify-messages-on-the-client.md)
- [Nasıl yapılır: Parametreleri İnceleme veya değiştirme](how-to-inspect-or-modify-parameters.md)
