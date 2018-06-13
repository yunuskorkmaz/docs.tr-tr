---
title: İstemcileri Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 95340a9ae6ac5a3face81d5fe6f61ea134fb6ad2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806662"
---
# <a name="extending-clients"></a>İstemcileri Genişletme
Bir arama uygulamasında hizmet modeli katmanını giden iletilere uygulama kodundaki yöntem çağrılarına çevirme, temel alınan kanalları Ftp'den, geri dönüş değerleri ve out Parametreleri sonuçları çevirme sorumludur uygulama kodu ve sonuçları döndüren çağırana yedekleyin. Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve istemci veya dağıtıcısı işlevi, özel davranışları, ileti ve parametre kişiler tarafından ele ve diğer genişletilebilirlik işlevleri içeren özellikler uygular.  
  
 Bu konuda nasıl kullanılacağını açıklar <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> bir WCF istemcisi veya müdahale veya iletileri, parametreleri değiştirmek için varsayılan yürütme davranışını değiştiren veya dönüş değerleri için bir Windows Communication Foundation (WCF) istemci uygulamasında sınıfları için önceki veya sonraki gönderme veya kanal katmandan alınıyor. Hizmet çalışma zamanı genişletme hakkında daha fazla bilgi için bkz: [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Değiştirebilir ve istemci çalışma zamanına özelleştirme nesneleri eklemek davranışları hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>İstemciler  
 Bir istemcide bir WCF istemcisi nesnesi veya istemci kanal yöntem çağrılarına giden iletiler ve çağıran uygulamada döndürülen işlem sonuçları gelen iletileri dönüştürür. (İstemci türleri hakkında daha fazla bilgi için bkz: [WCF istemci mimarisi](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 WCF istemci türlerini Bu uç nokta ve işlem düzeyinde işlevselliği işlemek çalışma zamanı türlerine sahip. Bir uygulama, bir işlem çağırdığında <xref:System.ServiceModel.Dispatcher.ClientOperation> giden nesneler iletiye çevirir, dinleyiciler işler, giden çağrı hedef sözleşmenin uyan ve Giden iletiye aktarır onaylar <xref:System.ServiceModel.Dispatcher.ClientRuntime>, olduğu sorumlu oluşturmak ve giden kanal (ve gelen kanalları çift yönlü hizmetler söz konusu olduğunda), fazladan giden ileti (üstbilgi değişikliği gibi) işleme işleme yönetmek için gelen ileti dinleyiciler her iki yönde işleme ve yönlendirme uygun istemci-tarafı çift yönlü çağrıları <xref:System.ServiceModel.Dispatcher.DispatchRuntime> nesnesi. Hem <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> (hataları dahil olmak üzere) iletiler istemciye döndürüldüğünde benzer hizmetleri sağlar.  
  
 Bu iki çalışma zamanı WCF istemci nesneleri ve kanallar işlenmesini özelleştirmek için ana uzantısı sınıflarıdır. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Sınıfı müdahale ve sözleşmenin tüm iletileri üzerinden istemci yürütme genişletmek kullanıcıların sağlar. <xref:System.ServiceModel.Dispatcher.ClientOperation> Sınıfı müdahale ve belirli bir işlemi tüm iletiler için istemci yürütme genişletmek kullanıcıların sağlar.  
  
 Özellikleri değiştirme veya özelleştirme ekleme Sözleşme, uç nokta ve işlem davranışları kullanılarak yapılır. Bu tür davranışları istemci çalışma zamanı özelleştirmeleri gerçekleştirmek için nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Senaryolar  
 Burada pek çok istemci sistemini genişletmek için de dahil olmak üzere:  
  
-   Özel ileti doğrulama. Bir kullanıcı, bir iletinin belirli bir şema için geçerli olduğunu zorlamak isteyebilirsiniz. Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi ve kullanımla atama <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> özelliği. Örnekler için bkz: [nasıl yapılır: inceleme veya değiştirme istemcide iletileri](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) ve [nasıl yapılır: inceleme veya değiştirme istemcide iletileri](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Özel ileti günlüğe kaydetme. Bir kullanıcı inceleyin ve bir uç noktası aracılığıyla akış uygulama iletileri bazı kümesi günlüğe isteyebilirsiniz. Bu, ileti dinleyiciyi arabirimleriyle da gerçekleştirilebilir.  
  
-   Özel ileti dönüşümleri. Uygulama kodunu değiştirmek yerine kullanıcı çalışma zamanı (örneğin, sürüm oluşturma) iletisinde belirli dönüştürmeleri uygulamak isteyebilirsiniz. Bu, yeniden ileti dinleyiciyi arabirimleri ile gerçekleştirilebilir.  
  
-   Özel veri modeli. Bir kullanıcı WCF'de varsayılan desteklenenler dışındaki bir veri ya da serileştirme modelde gerekebilir (yani, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> nesneleri). Bu ileti biçimlendirici arabirimler uygulama tarafından yapılabilir. Daha fazla bilgi için bkz: <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> özelliği.  
  
-   Özel parametre doğrulaması. Bir kullanıcı yazılan parametreleri (XML aksine) geçerli zorlamak isteyebilirsiniz. Bu yapılabilir parametre denetçisi arabirimleri kullanarak. Bir örnek için bkz [nasıl yapılır: inceleme veya değiştirme parametreleri](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) veya [istemci doğrulama](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Da ClientRuntime sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Sınıfı bir genişletilebilirlik noktasıdır için müdahale iletileri ve istemci davranışını genişleten uzantısı nesneleri ekleyebilirsiniz. Kişiler tarafından ele nesneleri belirli bir sözleşme tüm iletileri işlemek, yalnızca iletileri belirli işlemler için işlem, özel kanal başlatma gerçekleştirmek ve diğer özel istemci uygulamanın davranışı uygulamak.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Özelliği hizmeti tarafından başlatılan geri çağırma istemcileri için dağıtım çalışma zamanı nesnesi döndürür.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Özelliği bir özel işlem Seçici nesnesi kabul eder.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Özelliği, incelemek veya istemci kanal değiştirmek için bir kanal Başlatıcı eklenmesini sağlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Özelliği bir koleksiyonunu alır <xref:System.ServiceModel.Dispatcher.ClientOperation> nesneleri bu işlem iletileri için özel işlevsellik sağlayan özel ileti dinleyiciler ekleme yapabilir.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Özelliği, doğrudan adresleme denetlemek için bazı otomatik adresleme üstbilgileri devre dışı bırakma bir uygulama sağlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Özelliği, aracılar ve diğer senaryoları desteklemek için aktarım düzeyinde ileti hedef değerini ayarlar.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Özelliği bir koleksiyonunu alır <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> nesneleri bir WCF istemcisi üzerinden yolculuk tüm iletiler için özel ileti dinleyiciler ekleme yapabilir.  
  
 Ayrıca, bir dizi sözleşme bilgileri almak diğer özellikleri vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 WCF istemcisini çift yönlü bir WCF istemcisi ise, aşağıdaki özellikler de geri çağırma WCF istemci bilgilerini al:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 WCF istemci yürütme tüm bir WCF istemcisi genişletmek için kullanılabilen özellikleri gözden geçirin <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfı bir özellik değiştirme veya arabirimi uygulama ve için özellik ekleme aramayı işlevselliği oluşturup oluşturmayacağını bakın. Uzantınızı oluşturmak için belirli bir uzantıyı seçtikten sonra uygun Ekle <xref:System.ServiceModel.Dispatcher.ClientRuntime> erişim sağlayan bir istemci davranışını uygulayarak özelliği <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfı çağrıldığında.  
  
 Özel uzantı nesneleri bir işlemi davranışını kullanan bir koleksiyona ekleyebilirsiniz (uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior>), bir sözleşme davranış (uygulayan bir nesne <xref:System.ServiceModel.Description.IContractBehavior>), ya da bir uç noktası davranışı (uygulayan bir nesne <xref:System.ServiceModel.Description.IEndpointBehavior> ). Yükleme davranışı nesne davranışları uygun koleksiyonuna program aracılığıyla, bildirimli olarak (özel bir öznitelik uygulayarak) eklenir veya özel bir uygulama tarafından <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> kullanarak eklenecek davranışını etkinleştirmek için nesne bir Uygulama yapılandırma dosyası. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Bir WCF istemcisi kişiler tarafından ele gösteren örnekler için bkz [nasıl yapılır: inceleme veya değiştirme istemcide iletileri](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>ClientOperation sınıfını kullanma  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Sınıfı konumdur istemci çalışma zamanı değişiklikleri ve ekleme kapsamındaki özel uzantıları için yalnızca bir hizmet işlemi noktası. (Bir sözleşme tüm iletiler için istemci çalışma zamanı davranışını değiştirmek için kullanın <xref:System.ServiceModel.Dispatcher.ClientRuntime> sınıfı.)  
  
 Kullanım <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> bulmak için özellik <xref:System.ServiceModel.Dispatcher.ClientOperation> belirli bir hizmet işlemini temsil eden nesne. Aşağıdaki özellikleri WCF istemci sisteme özel nesneleri eklemek etkinleştir:  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> özel eklemek için özellik <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> uygulama için bir işlem veya geçerli biçimlendirici değiştirin.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> özel eklemek için özellik <xref:System.ServiceModel.Dispatcher.IParameterInspector> uygulama ya da geçerli birini değiştirmek için.  
  
 Aşağıdaki özellikler biçimlendirici ve özel parametre denetçiler etkileşimi sistemde değiştirmenizi etkinleştirin:  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> giden ileti serileştirmek denetleme özelliği.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> gelen iletinin seri durumdan çıkarma denetleme özelliği.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> istek iletisinin WS adresleme eylem denetleme özelliği.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> hangi WCF istemci yöntemleri zaman uyumsuz bir işlem ile ilişkili olduğunu belirtmek için.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> SOAP içinde görünebilir türler içeren bir koleksiyon almak için özellik hataları ayrıntı türü.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> ve <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> özelliklerini oturumu olup olmadığını denetlemek için başlatılır veya işlemi çağrıldığında, sırasıyla aşağıya kaldırılır.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> işlemi tek yönlü bir işlem olup olmadığını denetlemek için özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> içeren almak için özellik <xref:System.ServiceModel.Dispatcher.ClientRuntime> nesnesi.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> işlemin adının alınacağı özellik.  
  
-   Kullanım <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> çalışması için hangi yöntemi eşlenen denetleme özelliği.  
  
 WCF istemci yürütme arasında yalnızca bir hizmet işlemi genişletmek için kullanılabilen özellikleri gözden geçirin <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıfı bir özellik değiştirme veya arabirimi uygulama ve için özellik ekleme aramayı işlevselliği oluşturup oluşturmayacağını bakın. Uzantınızı oluşturmak için belirli bir uzantıyı seçtikten sonra uygun Ekle <xref:System.ServiceModel.Dispatcher.ClientOperation> erişim sağlayan bir istemci davranışını uygulayarak özelliği <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıfı çağrıldığında. İçinde bu davranış, daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Dispatcher.ClientRuntime> gereksinimlerinizi karşılayacak şekilde özelliği.  
  
 Genellikle, bir işlemi davranışı uygulama (uygulayan bir nesne <xref:System.ServiceModel.Description.IOperationBehavior> arabirimi) son eklerini, ancak aynı zamanda uç nokta davranışları kullanın ve sözleşme bularak aynı şeyi başarmak için davranışlar <xref:System.ServiceModel.Description.OperationDescription> belirli bir işlem ve davranış var. ekleme. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Yapılandırma, özel davranışından kullanmak için özel davranışı yapılandırma bölümü işleyicisi kullanarak, davranış yükleyin. Özel bir öznitelik oluşturarak, davranış da yükleyebilirsiniz.  
  
 Bir WCF istemcisi kişiler tarafından ele gösteren örnekler için bkz [nasıl: inceleme veya değiştirme parametreleri](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime>  
 <xref:System.ServiceModel.Dispatcher.ClientOperation>  
 [Nasıl yapılır: İstemcide İletileri Denetleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)  
 [Nasıl yapılır: Parametreleri İnceleme veya Değiştirme](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
