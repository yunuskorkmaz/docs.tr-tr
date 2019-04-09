---
title: İstemcileri Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 99b4dd5e4acfce8bea4d3c2cae3a53152585675d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074761"
---
# <a name="extending-clients"></a>İstemcileri Genişletme
Bir arama uygulamasında hizmet modeli katmanını içine giden iletiler için yöntem çağrılarına uygulama kodunda çevirme, bunları temel alınan kanallara gönderme, geri dönüş değerlerine dönüştürür ve out Parametreleri sonuçları çevirme sorumludur uygulama kodu ve sonuçları çağırana geri döndürülüyor. Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve istemci veya dağıtıcı işlevi, özel davranışlar, ileti ve parametre durdurma ve diğer genişletilebilirlik işlevlerini içeren özellikler uygular.  
  
 Bu konu nasıl kullanılacağını açıklar <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> bir WCF istemcisi veya ıntercept veya iletileri, parametreleri değiştirmek için varsayılan yürütme davranışını değiştirmek veya dönüş değerleri için bir Windows Communication Foundation (WCF) istemci uygulamasında sınıfları için önceki veya sonraki gönderme veya bunları kanal katmandan alınıyor. Hizmet çalışma zamanı genişletme hakkında daha fazla bilgi için bkz. [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Değiştiren ve istemci çalışma zamanına özelleştirme nesneleri eklemek davranışları hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>İstemciler  
 Bir istemcide bir WCF istemcisi nesne veya istemci kanalını yöntem çağrıları giden iletileri ve gelen iletileri arama uygulamaya döndürülen İşlem sonuçlarını dönüştürür. (İstemci türleri hakkında daha fazla bilgi için bkz. [WCF istemci mimarisi](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 WCF istemci türlerini, bu uç nokta ve işlem düzeyi işlevselliğine çalışma zamanı türleri vardır. Bir uygulama, bir işlem çağırdığında <xref:System.ServiceModel.Dispatcher.ClientOperation> giden nesneleri bir iletiye dönüştürür, dinleyicileri işler, giden çağrı için hedef sözleşmesi uyan ve giden iletinin uygulamalı onaylar <xref:System.ServiceModel.Dispatcher.ClientRuntime>, olduğu sorumlu oluşturmak ve giden kanallar (ve gelen kanalları çift yönlü hizmetler söz konusu olduğunda), (üst bilgi değiştirme gibi) işleme ek giden ileti işleme yönetmek için gelen ileti dinleyicileri her iki yönde işleme ve yönlendirme uygun istemci tarafı çift yönlü çağrıları <xref:System.ServiceModel.Dispatcher.DispatchRuntime> nesne. Hem <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> istemciye ileti (hatalar dahil olmak üzere) döndürüldüğünde benzer hizmetleri sağlar.  
  
 Bu iki çalışma zamanı WCF istemci nesneleri ve kanalları işlenmesini özelleştirmek için ana uzantısı sınıflardır. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Sınıfı ıntercept ve sözleşmenin içindeki tüm iletileri arasında istemci yürütme genişletmek kullanıcıların sağlar. <xref:System.ServiceModel.Dispatcher.ClientOperation> Sınıfı ıntercept ve belirli bir işlemde tüm iletiler için istemci yürütme genişletmek kullanıcıların sağlar.  
  
 Özellikleri değiştirme veya özelleştirme ekleyerek sözleşme, uç noktayı ve işlem davranışları kullanarak gerçekleştirilir. İstemci çalışma zamanı özelleştirmeleri gerçekleştirmek için bu tür davranışları kullanma hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Senaryolar  
 Burada birkaç nedenden istemci sistemini genişletmek için de dahil olmak üzere:  
  
-   Özel ileti doğrulama. Bir kullanıcı, bir ileti için belirli bir şema geçerli olduğunu zorlamak isteyebilirsiniz. Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi ve uygulaması için atama <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> özelliği. Örnekler için bkz [nasıl yapılır: İstemcide iletileri denetleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) ve [nasıl yapılır: İstemcide iletileri denetleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Özel ileti günlüğe kaydetme. Bir kullanıcı inceleyin ve bir uç noktası aracılığıyla akış uygulama iletileri bir dizi oturum isteyebilirsiniz. Bu da ileti kesici arabirimleri ile gerçekleştirilebilir.  
  
-   Özel ileti dönüşümler. Uygulama kodunu değiştirmek yerine, kullanıcı iletisi (örneğin, sürüm oluşturma) çalışma zamanında belirli dönüştürmeleri uygulamak isteyebilirsiniz. Bu, yeniden ileti kesici arabirimleri ile gerçekleştirilebilir.  
  
-   Özel veri modeli. Bir kullanıcı bir veri veya seri hale getirme modeli varsayılan WCF tarafından desteklenen dışındaki gerekebilir (yani, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> nesneleri). Bu ileti biçimlendirici arabirimlerini uygulayarak yapılabilir. Daha fazla bilgi için <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> özelliği.  
  
-   Özel parametre doğrulama. Bir kullanıcı türü belirtilmiş bir parametre (XML aksine) geçerli olduğunu zorlamak isteyebilirsiniz. Bu yapılabilir parametresi denetçisi arabirimleri kullanarak. Bir örnek için bkz [nasıl yapılır: Parametreleri inceleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) veya [istemci doğrulama](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>ClientRuntime sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Sınıfı, bir genişletilebilirlik noktası için istemci davranışını genişletmek ve müdahale iletileri genişletme nesneleri ekleyebilirsiniz. Durdurma nesneleri belirli bir sözleşme tüm iletileri işler, yalnızca belirli işlemleri için iletileri işlemek, özel kanal başlatma gerçekleştirmek ve diğer özel istemci uygulama davranışı uygulamak.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Özelliği hizmet tarafından başlatılan bir geri çağırma istemcileri için dağıtım çalışma zamanı nesnesi döndürür.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Özelliği bir özel işlem Seçici nesnesi kabul eder.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Özelliği inceleyin veya istemci kanal değiştirebilen bir kanal Başlatıcı eklenmesini sağlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Özellik koleksiyonunu alır <xref:System.ServiceModel.Dispatcher.ClientOperation> iletileri bu işlem, belirli işlevleri sağlayan özel ileti dinleyiciler eklemek nesneleri.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Özelliği, doğrudan adresleme denetlemek için bazı otomatik adres üstbilgileri devre dışı açmak bir uygulama sağlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Özelliği, aracılar ve diğer senaryoları desteklemek için taşıma düzeyinde hedef iletinin değerini ayarlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Özellik koleksiyonunu alır <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> nesneleri bir WCF istemcisi üzerinden yolculuk tüm iletiler için özel ileti dinleyicileri ekleme yapabilir.  
  
 Ayrıca, bir dizi sözleşmesi bilgileri almak diğer özellikleri vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 WCF istemcisini çift yönlü bir WCF istemcisi, aşağıdaki özellikleri WCF istemci bilgileri geri çağırma ayrıca Al:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 WCF istemci yürütme tüm bir WCF istemcisi genişletmek için kullanılabilir özelliklerini gözden geçirin. <xref:System.ServiceModel.Dispatcher.ClientRuntime> bir özelliğini değiştirme veya arabirim uygulama ve özellik ekleme dağıtımınızla işlevselliğini oluşturup oluşturmayacağını görmek için sınıf. Uzantınızı oluşturmak için belirli bir uzantıya seçtikten sonra uygun Ekle <xref:System.ServiceModel.Dispatcher.ClientRuntime> erişim sağlayan bir istemci davranışını uygulayarak özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime> çağrıldığında sınıf.  
  
 Özel genişletme nesneleri bir işlem davranışını kullanarak bir koleksiyona ekleyebilirsiniz (uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior>), bir sözleşme davranış (uygulayan bir nesne <xref:System.ServiceModel.Description.IContractBehavior>), veya bir uç nokta davranışı (uygulayan bir nesne <xref:System.ServiceModel.Description.IEndpointBehavior> ). Yükleme davranışı nesne davranışların ilgili koleksiyona program aracılığıyla, bildirimli olarak (özel bir öznitelik uygulayarak) eklenir veya özel bir uygulama tarafından <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> kullanarak eklenecek davranışı etkinleştirmek üzere nesne bir Uygulama yapılandırma dosyası. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Bir WCF istemcisi arasında durdurma gösteren örnekler için bkz. [nasıl yapılır: İstemcide iletileri denetleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>ClientOperation sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Sınıfı, konumu istemci çalışma zamanı değişiklikleri ve ekleme kapsamındaki özel uzantıları için yalnızca bir hizmet işlemine noktası. (Bir sözleşme tüm iletiler için istemci çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfı.)  
  
 Kullanım <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> bulmak için özellik <xref:System.ServiceModel.Dispatcher.ClientOperation> belirli hizmet işlemini temsil eden nesne. Aşağıdaki özellikleri WCF istemci sisteme özel nesneleri eklemek etkinleştirin:  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> özel eklemek için özellik <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> uygulama için bir işlem veya geçerli biçimlendirici değiştirin.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> özel eklemek için özellik <xref:System.ServiceModel.Dispatcher.IParameterInspector> uygulama veya geçerli değiştirilecek.  
  
 Aşağıdaki özellikler, biçimlendirici ve özel parametre denetçiler etkileşimi sistemde değişiklik olanak sağlar:  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> giden ileti serileştirmek denetlemek için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> gelen iletinin seri durumundan çıkarma denetlemek için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> istek iletisi WS-Addressing eylemini denetlemek için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> hangi WCF istemci yöntemleri bir zaman uyumsuz işlemle ilişkili olduğunu belirtmek için.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> SOAP içinde görünebilir türler içeren koleksiyonu almak için özelliği ayrıntı türüne hataları.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> oturum olup olmadığını denetlemek için özellikler başlatılır veya aşağı, sırasıyla işlemi çağrılırken bozuk.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> işlemi tek yönlü bir işlem olup olmadığını denetlemek için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> içeren almak için özellik <xref:System.ServiceModel.Dispatcher.ClientRuntime> nesne.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> işlem adını almak için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> işlemi için hangi yöntemin eşlendi denetlemek için özellik.  
  
 WCF istemci yürütme arasında yalnızca bir hizmet işlemi genişletmek için kullanılabilir özelliklerini gözden geçirin. <xref:System.ServiceModel.Dispatcher.ClientOperation> bir özelliğini değiştirme veya arabirim uygulama ve özellik ekleme dağıtımınızla işlevselliğini oluşturup oluşturmayacağını görmek için sınıf. Uzantınızı oluşturmak için belirli bir uzantıya seçtikten sonra uygun Ekle <xref:System.ServiceModel.Dispatcher.ClientOperation> erişim sağlayan bir istemci davranışını uygulayarak özelliği <xref:System.ServiceModel.Dispatcher.ClientOperation> çağrıldığında sınıf. İçinde bu davranış, daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Dispatcher.ClientRuntime> gereksinimlerinizi karşılayacak şekilde özelliği.  
  
 Genellikle, bir işlem davranışı uygulayan (uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior> arabirimi) soneklerini belirttiniz, ancak aynı zamanda uç nokta davranışları kullanın ve sözleşme bularak aynı şeyi yapmanın davranışları <xref:System.ServiceModel.Description.OperationDescription> belirli bir işlem ve davranışı var. ekleme. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Özel davranışınızı yapılandırmasından kullanmak için özel davranış yapılandırma bölümü işleyicisi kullanarak davranışınızı yükleyin. Özel bir öznitelik oluşturularak davranışınızı de yükleyebilirsiniz.  
  
 Bir WCF istemcisi arasında durdurma gösteren örnekler için bkz. [nasıl yapılır: Parametreleri inceleme veya değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)
- [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
