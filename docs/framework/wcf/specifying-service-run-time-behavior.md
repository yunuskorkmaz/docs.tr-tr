---
title: Hizmet Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 246f16cee85633499a6a1c200e608ee7bccf133c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243108"
---
# <a name="specifying-service-run-time-behavior"></a>Hizmet Çalışma Zamanı Davranışını Belirtme
Bir hizmet sözleşmesi[(Hizmet Sözleşmelerini Tasarlama)](designing-service-contracts.md)tasarladıktan ve hizmet sözleşmenizi[(Hizmet Sözleşmelerini Uygulama)](implementing-service-contracts.md)uyguladıktan sonra, hizmet çalışma zamanının çalışma davranışını yapılandırabilirsiniz. Bu konu, sistem tarafından sağlanan hizmet ve çalışma davranışlarını açıklar ve yeni davranışlar oluşturmak için daha fazla bilginin nerede bulunacağını açıklar. Bazı davranışlar öznitelik olarak uygulanırken, çoğu bir uygulama yapılandırma dosyası kullanılarak veya programlı olarak uygulanır. Hizmet uygulamanızı yapılandırma hakkında daha fazla bilgi için [bkz.](configuring-services.md)  
  
## <a name="overview"></a>Genel Bakış  
 Sözleşme, bu tür bir hizmetin girdilerini, çıktılarını, veri türlerini ve yeteneklerini tanımlar. Hizmet sözleşmesinin uygulanması, bir adreste bağlayıcılıkla yapılandırıldığında uyguladığı sözleşmeyi yerine getiren bir sınıf oluşturur. Sözleşme, bağlama ve adres bilgilerinin tümü müşteri tarafından bilinir; bunlar olmadan, istemci hizmeti kullanamaz.  
  
 Ancak, iş parçacığı sorunları veya örnek yönetimi gibi işlem özellikleri istemciler için opaktır. Hizmet sözleşmenizi uyguladıktan sonra, *davranışları*kullanarak çok sayıda işlem özelliğini yapılandırabilirsiniz. Davranışlar, windows communication foundation (WCF) çalışma zamanını bir çalışma zamanı özelliği ayarlayarak veya çalışma zamanına bir özelleştirme türü ekleyerek değiştiren nesnelerdir. Kullanıcı tanımlı davranışlar oluşturarak çalışma süresini değiştirme hakkında daha fazla bilgi için [Bkz.](./extending/extending-servicehost-and-the-service-model-layer.md)  
  
 Ve <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> öznitelikleri en yaygın olarak yararlı davranışlar dır ve en sık istenen işlem özelliklerini ortaya çıkarır. Öznitelikler olduğundan, bunları hizmet veya işlem uygulamasına uygularsınız. Diğer davranışlar, <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> örneğin, <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır, ancak bunları programlı olarak kullanabilirsiniz.  
  
 Bu <xref:System.ServiceModel.ServiceBehaviorAttribute> konu, <xref:System.ServiceModel.OperationBehaviorAttribute> ve özniteliklere genel bir bakış sağlar, davranışların çalışabileceği çeşitli kapsamları açıklar ve WCF geliştiricileri için ilgi çekici olabilecek çeşitli kapsamlarda sistem tarafından sağlanan davranışların çoğunun hızlı bir açıklamasını sağlar.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute ve OperationBehaviorAttribute  
 En önemli davranışlar, <xref:System.ServiceModel.ServiceBehaviorAttribute> denetlemek <xref:System.ServiceModel.OperationBehaviorAttribute> için kullanabileceğiniz öznitelikler ve özniteliklerdir:  
  
- Örnek yaşam ömürleri  
  
- Eşzamanlılık ve senkronizasyon desteği  
  
- Yapılandırma davranışı  
  
- Hareket davranışı  
  
- Serileştirme davranışı  
  
- Meta veri dönüşümü  
  
- Oturum ömrü  
  
- Adres filtreleme ve üstbilgi işleme  
  
- Kimliğe bürünme  
  
- Bu öznitelikleri kullanmak için, hizmet veya işlem uygulamasını bu kapsama uygun öznitelikile işaretleyin ve özellikleri ayarlayın. Örneğin, aşağıdaki kod örneği, bu işlemi <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> arayanların kimliğe bürünme desteği gerektirmek için özelliği kullanan bir işlem uygulaması gösterir.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Özelliklerin çoğu bağlama ek destek gerektirir. Örneğin, istemciden bir hareket gerektiren bir işlem, akışlı hareketleri destekleyen bir bağlayıcı kullanmak üzere yapılandırılmalıdır.  
  
### <a name="well-known-singleton-services"></a>Tanınmış Singleton Hizmetleri  
 İşlemleri uygulayan <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmet <xref:System.ServiceModel.OperationBehaviorAttribute> nesnelerinin <xref:System.ServiceModel.InstanceContext> hem de belirli yaşam ömürlerini denetlemek için öznitelikleri kullanabilirsiniz.  
  
 Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik ne sıklıkta <xref:System.ServiceModel.InstanceContext> serbest bırakıldığını <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> denetler ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> hizmet nesnesi serbest bırakıldığında özellikleri denetler.  
  
 Ancak, bir hizmet nesnesi kendiniz oluşturabilir ve bu nesneyi kullanarak hizmet ana bilgisayarını oluşturabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği de <xref:System.ServiceModel.InstanceContextMode.Single> ayarlamanız gerekir veya hizmet ana bilgisayar açıldığında bir özel durum atılır.  
  
 Böyle <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> bir hizmet oluşturmak için oluşturucuyu kullanın. Singleton hizmeti tarafından kullanılmak <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> üzere belirli bir nesne örneği sağlamak istediğinizde özel bir uygulama için bir alternatif sağlar. Hizmet uygulama türünüz zor olduğunda (örneğin, parametresiz bir ortak oluşturucu uygulamıyorsa) bu aşırı yükü kullanabilirsiniz.
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) ile ilgili bazı özelliklerin davranış yapısının farklı çalıştığını unutmayın. Örneğin, iyi <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> bilinen bir nesne örneği sağlandığında aramanın hiçbir etkisi yoktur. Benzer şekilde, başka bir örnek yayımetme mekanizması yoksayılır. Sınıf <xref:System.ServiceModel.ServiceHost> her zaman <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özellik tüm işlemler <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> için ayarlanmış gibi olur.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Diğer Hizmet, Bitiş Noktası, Sözleşme ve İşlem Davranışları  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> Öznitelik gibi hizmet davranışları tüm hizmet boyunca çalışır. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> size ayarlarsanız, bu hizmetteki her işlemdeki iş parçacığı eşitleme sorunlarını kendiniz işlemeniz gerekir. Bitiş noktası davranışları bir bitiş noktası boyunca çalışır; sistem tarafından sağlanan uç nokta davranışlarının çoğu istemci işlevselliği içindir. Sözleşme davranışları sözleşme düzeyinde çalışır ve işlem davranışları işlem teslimini değiştirir.  
  
 Bu davranışların çoğu öznitelikler üzerinde uygulanır ve bunları uygun hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> sınıfına veya işlem uygulamasına uygulayarak bunları kullanırsınız. Diğer davranışlar, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneğin veya <xref:System.ServiceModel.Description.ServiceDebugBehavior> nesneler, genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır, ancak bunlar da programlı olarak kullanılabilir.  
  
 Örneğin, meta verilerin yayınlanması <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne kullanılarak yapılandırılır. Aşağıdaki uygulama yapılandırma dosyası en yaygın kullanımı gösterir.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Aşağıdaki bölümler, hizmetinizin veya istemcinizin çalışma zamanı teslimini değiştirmek için kullanabileceğiniz en yararlı sistem tarafından sağlanan davranışların çoğunu açıklar. Her birinin nasıl kullanılacağını belirlemek için başvuru konusuna bakın.  
  
### <a name="service-behaviors"></a>Hizmet Davranışları  
 Aşağıdaki davranışlar hizmetlerde çalışır.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Bu hizmetin ASP.NET Uyumluluk Modunda çalıştırılıp çalıştırılamadığını belirtmek için wcf hizmetine uygulanır.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Hizmetin istemci taleplerine nasıl yetki verdiğini denetler.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Bir hizmet kimlik belgesini yapılandırır. X.509 sertifikası gibi hizmetin kimlik bilgisini belirtmek için bu sınıfı kullanın.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Bir WCF hizmeti için hata ayıklama ve Yardım bilgi özelliklerini etkinleştirir.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Hizmet meta verilerinin ve ilişkili bilgilerin yayınlanmasını denetler.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Güvenlik olaylarının denetim davranışını belirtir.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Hizmet performansını ayarlamanızı sağlayan çalışma zamanı iş verme ayarlarını yapılandırır.  
  
### <a name="endpoint-behaviors"></a>Bitiş Noktası Davranışları  
 Aşağıdaki davranışlar uç noktalarda çalışır. Bu davranışların çoğu istemci uygulamalarında kullanılır.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Çift yönlü istemci uygulamasında geri arama hizmeti uygulamasını yapılandırır.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. WCF geri arama nesnesi için hizmet hata ayıklamasağlar.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Kullanıcının istemci ve hizmet kimlik bilgilerini yapılandırmasının yanı sıra istemcide kullanılmak üzere hizmet kimlik bilgisi kimlik doğrulama ayarlarını yapılandırmasına olanak tanır.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Aktarım kanalının oluşturulması gereken Tek düzen kaynak tanımlayıcısını (URI) belirtmek için istemciler tarafından kullanılır.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. WCF'ye `MustUnderstand` işlemi devre dışı bmasını bildirir.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Kanallar için eşzamanlı alma işlemini kullanmanın çalışma saatini bildirir.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. İşlem alımlarını destekleyen taşımalar için alma işlemlerini optimize eder.  
  
### <a name="contract-behaviors"></a>Sözleşme Davranışları  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Bağlamaların hizmete veya istemci uygulamasına sağlaması gereken özellik gereksinimlerini belirtir.  
  
### <a name="operation-behaviors"></a>Operasyon Davranışları  
 Aşağıdaki işlem davranışları, işlemler için serileştirme ve hareket denetimlerini belirtir.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>Çalışma zamanı davranışını temsil eder.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Çalışma zamanı davranışını `XmlSerializer` denetler ve bir işlemle ilişkilendirer.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Hizmet işleminin bir işlem üstbilgisini kabul ettiği düzeyi belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](configuring-services.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](./feature-details/how-to-control-service-instancing.md)
