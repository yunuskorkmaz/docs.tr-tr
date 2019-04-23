---
title: Hizmet Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 9fa6e4114e9579079705700708840f2814b03b99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186881"
---
# <a name="specifying-service-run-time-behavior"></a>Hizmet Çalışma Zamanı Davranışını Belirtme
Bir hizmet sözleşmesini tasarladıktan sonra ([Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)) ve hizmet sözleşmeniz ([hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)) işlemi davranışını yapılandırabilirsiniz. Hizmet çalışma zamanı. Bu konu, sistem tarafından sağlanan hizmet ve işlem davranışları açıklar ve yeni davranışlar oluşturma hakkında daha fazla bilgi bulmak nereye açıklar. Bazı davranışları öznitelik olarak uygulanır, ancak çoğu uygulama yapılandırma dosyası kullanılarak uygulanır veya programlama yoluyla. Hizmet uygulamanızın yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Genel Bakış  
 Sözleşme girişler, çıkışlar, veri türleri ve bu türde bir hizmet özelliklerini tanımlar. Bir hizmet sözleşmesini uygulama oluşturur bir sınıf, bir adresteki bir bağlama ile yapılandırıldığında karşıladığı sözleşmenin uygular. Sözleşme, bağlama ve adres bilgilerini tüm istemci tarafından bilinir; İstemci onlar olmadan yapamazsınız hizmetini kullanın.  
  
 Ancak, işlem özellikleri, iş parçacığı oluşturma sorunları veya örnek yönetimi gibi istemciler için donuk uygulanır. Hizmet sözleşmeniz uyguladıktan sonra çok sayıda işlem özelliklerini kullanarak yapılandırabilirsiniz *davranışları*. Davranışlar çalışma zamanı özelliğini ayarlayarak ya da çalışma zamanına özelleştirme türü ekleyerek Windows Communication Foundation (WCF) çalışma zamanı değiştiren nesneleridir. Kullanıcı tanımlı davranışlar oluşturarak çalışma zamanını değiştirme hakkında daha fazla bilgi için bkz. [genişletme ServiceHost ve hizmet modeli katmanını](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> Ve <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> özniteliklerin en yaygın olarak yararlı davranışları ve en sık istenen işlem özellikleri kullanıma sunar. Öznitelikleri olduklarından, hizmet veya işlem uygulaması için geçerlidir. Diğer davranışlar gibi <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, programlı olarak kullanabilirsiniz, ancak genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır.  
  
 Bu konu, genel bir bakış sağlar. <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikler, hangi davranışları çalışabilir, çeşitli kapsamları açıklar ve birçok sistem tarafından sağlanan davranışlarını çekebilecek çeşitli kapsam hızlı bir açıklaması verilmiştir WCF geliştiricileri ilgilendiren.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute ve OperationBehaviorAttribute  
 En önemli davranışlarının olan <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> denetlemek için kullanabileceğiniz öznitelikleri:  
  
-   Örnek yaşam süresi yok  
  
-   Eşzamanlılık ve eşitleme desteği  
  
-   Yapılandırma davranışı  
  
-   İşlem davranışı  
  
-   Serileştirme davranışı  
  
-   Meta veri dönüştürme  
  
-   Oturum yaşam süresi  
  
-   Adres filtreleme ve üst bilgisi işleme  
  
-   Kimliğe bürünme  
  
-   Bu öznitelikler kullanmak için öznitelik hizmet veya işlemi uygulamasıyla ilgili kapsam için uygun işaretleyin ve özelliklerini ayarlayın. Örneğin, aşağıdaki kod örneği kullanan bir işlem uygulaması gösterir <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> özelliği bu işlemin çağıranlar kimliğe bürünme desteği gerektirir.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Özelliklerin birçoğu, ek destek bağlama gerektirir. Örneğin, istemciden gelen bir işlem gerektiren bir işlem akan işlemleri destekleyen bir bağlama kullanmak için yapılandırılmalıdır.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen tekil hizmetin  
 Kullanabileceğiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> belirli ömürleri, her ikisini de denetlemek için öznitelikleri <xref:System.ServiceModel.InstanceContext> ve işlemlerini uygulamak hizmet nesneleri.  
  
 Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik denetler ne sıklıkta <xref:System.ServiceModel.InstanceContext> yayımlandığı ve <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> denetim özelliklerini hizmet nesnesi yayınlandığında.  
  
 Ancak, aynı zamanda bir hizmet nesnesi kendiniz oluşturabilir ve bu nesneyi kullanarak hizmet ana bilgisayarını oluşturun. Bunu yapmak için de ayarlamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.InstanceContextMode.Single> veya hizmet ana bilgisayarı açıldığında bir özel durum oluşturulur.  
  
 Kullanım <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> böyle bir hizmet oluşturmak için oluşturucu. Özel bir uygulama için bir alternatif sağlayan <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> belirli nesne örneği, tek bir hizmet tarafından kullanılmak üzere sağlamak istediğiniz zaman. Hizmet uygulama türünüzü (örneğin, bu parametre sahip varsayılan bir public Oluşturucu uygulamıyorsa) oluşturmak zor olduğunda, bu aşırı yüklemesini kullanabilirsiniz.  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (davranışı depolamasına WCF için) ilgili bazı özellikler farklı iş unutmayın. Örneğin, çağırma <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> iyi bilinen nesne örneği sağlandığında hiçbir etkisi olmaz. Benzer şekilde, başka bir örneği yayın mekanizması göz ardı edilir. <xref:System.ServiceModel.ServiceHost> Sınıfı her zaman davranacağını gibi <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> tüm işlemler için.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Diğer hizmet, uç nokta, sözleşme ve işlem davranışları  
 Davranışlar gibi hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği, hizmetin tamamı çalışır. Örneğin, ayarlarsanız <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> hizmet her bir işlemin içinde iş parçacığı eşitleme sorunları kendiniz işlemelidir. Uç nokta davranışları bir uç nokta üzerinde çalışır; çoğu sistem tarafından sağlanan uç nokta davranışları için istemci işlevsellik bulunur. Sözleşme davranışları sözleşme düzeyinde çalışır ve işlem teslim işlem davranışları değiştirin.  
  
 Bu davranışların çoğu, özniteliklerinde uygulanır ve yaptığınız gibi bunları kullanmak <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri — uygun hizmet sınıfı veya işlemi uygulama uygulayarak. Diğer davranışlar gibi <xref:System.ServiceModel.Description.ServiceMetadataBehavior> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior> nesneler genellikle uygulandığı bir uygulama yapılandırma dosyası kullanarak bunlar aynı zamanda program aracılığıyla kullanılabilir olsa da.  
  
 Örneğin, meta veri yayımlanmasını kullanarak yapılandırılan <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesne. Aşağıdaki uygulama yapılandırma dosyası, en yaygın kullanımını gösterir.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Aşağıdaki bölümlerde, hizmet veya istemci çalışma zamanı dağıtımını değiştirmek için kullanabileceğiniz faydalı sistem tarafından sağlanan davranışları birçoğu açıklanmaktadır. Her birini kullanmak nasıl belirlemek için başvuru konusuna bakın.  
  
### <a name="service-behaviors"></a>Hizmet davranışları  
 Aşağıdaki davranışları hizmetleri üzerinde çalışır.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Bu hizmet çalıştırılabilir olup olmadığını belirtmek için bir WCF Hizmeti uygulanan [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uyumluluk modu.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Hizmet istemci talep nasıl yetkilendirir denetler.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Bir hizmet kimlik bilgisi yapılandırır. Bu sınıf, bir X.509 sertifikası gibi hizmete ilişkin kimlik bilgileri belirtmek için kullanın.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Hata ayıklamayı etkinleştirir ve yardımcı bir WCF hizmeti için bilgi özellikleri.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Hizmet meta verileri ve ilgili bilgilerin yayınlanmasını denetler.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Güvenlik olaylarını denetleme davranışını belirtir.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Hizmet performansı ayarlamak etkinleştirdiğiniz çalışma zamanı aktarım ayarları yapılandırır.  
  
### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Aşağıdaki davranışları uç noktalarında çalışır. Bu davranışların çoğu, istemci uygulamalarında kullanılır.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Bir geri çağırma hizmet uygulaması, bir çift yönlü istemci uygulaması olarak yapılandırır.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Bir WCF geri çağırma nesnesi için hizmet hata ayıklamasını etkinleştirir.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Yanı sıra istemci ve hizmet kimlik bilgilerini yapılandırın, hizmet istemci üzerinde kullanım için kimlik bilgisi kimlik doğrulaması ayarları izin verir.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Taşıma kanalının oluşturulması gereken Tekdüzen Kaynak Tanımlayıcısı (URI) belirtmek için istemciler tarafından kullanılır.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Devre dışı bırakmak için WCF bildirir `MustUnderstand` işleniyor.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Eş zamanlı kullanmak için çalışma zamanı bildirir kanallar için işlemi alır.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. İşlem desteği alan taşımalar alma işlemlerinde en iyi duruma getirir.  
  
### <a name="contract-behaviors"></a>Sözleşme davranışları  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Hizmet veya istemci uygulamasına bağlamaları sağlaması gereken özellik gereksinimlerini belirtir.  
  
### <a name="operation-behaviors"></a>İşlem davranışları  
 Aşağıdaki işlem davranışları işlemleri için seri hale getirme ve işlem denetimleri belirtin.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Çalışma zamanı davranışını temsil eden <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Çalışma zamanı davranışını denetleyen `XmlSerializer` ve bir işlem ile ilişkilendirir.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Bir hizmet işlemi bir işlem üst bilgisi kabul eden düzeyini belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md)
- [Nasıl yapılır: Hizmet örneği oluşturmayı denetleme](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
