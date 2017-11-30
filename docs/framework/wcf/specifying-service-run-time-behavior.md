---
title: "Hizmet Çalışma Zamanı Davranışını Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f37259a971ab20cf68776ac9889615929996ad00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-service-run-time-behavior"></a>Hizmet Çalışma Zamanı Davranışını Belirtme
Bir hizmet sözleşmesini tasarladıktan sonra ([Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)) ve hizmet sözleşmesini uygulanan ([hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)) işlemi davranışını yapılandırabilirsiniz Hizmet çalışma zamanı. Bu konu, sistem tarafından sağlanan hizmet ve işlem davranışları açıklar ve yeni davranışlar oluşturma hakkında daha fazla bilgi bulmak nerede tanımlar. Bazı davranışları öznitelik olarak uygulanır, ancak çoğu uygulama yapılandırma dosyası kullanılarak uygulanır veya program aracılığıyla. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bkz: hizmet uygulamanızın yapılandırma [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Genel Bakış  
 Sözleşme Girişleri, çıktıları, veri türleri ve bu tür bir hizmet özelliklerini tanımlar. Bir hizmet sözleşmesini uygulama oluşturur bir sınıf, bir adresinde bir bağlama ile yapılandırıldığında bunu uygulayan sözleşme yerine getirir. Sözleşme, bağlama ve adres bilgilerini tüm istemci tarafından bilinen; bunları istemci yapamazsınız hizmetini kullanın.  
  
 Ancak, sorunları veya örnek yönetimi, iş parçacığı oluşturma gibi işlem özellikleri, istemcilere donuk değildir. Hizmet sözleşmesi uyguladıktan sonra kullanarak çok sayıda işlem özelliklerini yapılandırabilirsiniz *davranışları*. Davranışları olan değiştirme nesneler [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] ya da bir çalışma zamanı özellik ayarlama veya özelleştirme türü çalışma zamanına ekleyerek çalışma zamanı. [!INCLUDE[crabout](../../../includes/crabout-md.md)]çalışma zamanı davranışı, kullanıcı tanımlı oluşturarak değiştirme bkz [genişletme ServiceHost ve hizmet modeli katmanını](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> Ve <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> özniteliklerin en yaygın olarak yararlı davranışları ve sunmaya en sık istenen işlemi özellikleri. Öznitelikleri olduklarından, hizmet veya işlem uygulaması için geçerlidir. Diğer davranışları gibi <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, program aracılığıyla kullanabilirsiniz ancak genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır.  
  
 Bu konu genel bir bakış sağlar <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri, hangi davranışları çalışabilir, çeşitli kapsamlar açıklar ve çoğu sistem tarafından sağlanan davranışları ilgilendirebilecek çeşitli kapsamlar en hızlı bir açıklaması verilmiştir için ilgilendiğiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] geliştiriciler.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute ve OperationBehaviorAttribute  
 En önemli davranışları olan <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> denetlemek için kullanabileceğiniz öznitelikleri:  
  
-   Örnek yaşam süresi  
  
-   Eşzamanlılık ve eşitleme desteği  
  
-   Yapılandırma davranışı  
  
-   İşlem davranışı  
  
-   Seri hale getirme davranışı  
  
-   Meta veri dönüştürme  
  
-   Oturum yaşam süresi  
  
-   Adresi filtreleme ve üstbilgisi işleme  
  
-   Kimliğe bürünme  
  
-   Bu öznitelikler kullanmak için bir hizmet veya işlemi uygulama özniteliği ile bu kapsama uygun işaretleyin ve özellikleri ayarlayın. Örneğin, aşağıdaki kod örneği kullanan bir işlem uygulaması gösterir <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> özellik bu işlem arayanlar kimliğe bürünme desteği gerektirir.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Özelliklerin çoğu bağlama ek desteğini gerektirir. Örneğin, istemciden gelen bir işlem gerektiren bir işlem akan işlemleri destekleyen bir bağlama kullanacak şekilde yapılandırılması gerekir.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 Kullanabileceğiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> belirli yaşam süresi, her ikisini de denetlemek için öznitelikler <xref:System.ServiceModel.InstanceContext> ve işlemleri uygulamak hizmet nesneleri.  
  
 Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği denetler ne sıklıkta <xref:System.ServiceModel.InstanceContext> yayımlandığı ve <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> denetim özelliklerini hizmet nesnesi serbest bırakıldığında.  
  
 Ancak, ayrıca bir hizmet nesnesi kendiniz oluşturabilir ve bu nesneyi kullanarak hizmet ana bilgisayarını oluşturun. Bunu yapmak için de ayarlamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.InstanceContextMode.Single> ya da hizmet konağı açıldığında bir özel durum oluşur.  
  
 Kullanım <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> gibi bir hizmet oluşturmak için Oluşturucusu. Özel bir uygulama için bir alternatif sağlayan <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> belirli nesne örneği bir singleton hizmeti tarafından kullanım için sağlamak istediğiniz zaman. Hizmet uygulama türü (örneğin, bu parametreye sahip olmayan bir varsayılan ortak oluşturucu uygulamadığında) oluşturmak zor olduğu durumlarda, bu aşırı yüklemesini kullanabilirsiniz.  
  
 Bu oluşturucuya bir nesne sağlandığında, bazı özellikler için ilgili [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] davranışı iş farklı depolamasına. Örneğin, arama <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> iyi bilinen nesne örneği sağlandığında hiçbir etkisi olmaz. Benzer şekilde, diğer bir örnek yayın mekanizması göz ardı edilir. <xref:System.ServiceModel.ServiceHost> Sınıfı her zaman davranır gibi <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği ayarlanmış <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> tüm işlemleri için.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Diğer hizmet, uç nokta, sözleşme ve işlem davranışları  
 Davranışları gibi hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute> öznitelik, bir tüm hizmet çalışır. Örneğin, ayarlarsanız <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliğine <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> kendiniz hizmetin her bir işlemin içindeki iş parçacığı eşitleme sorunlarını işlemesi gerekir. Uç nokta davranışları bir uç nokta çalışır; çoğu sistem tarafından sağlanan uç nokta davranışları için istemci işlevsellik bulunur. Sözleşme davranışları sözleşme düzeyinde çalışır ve işlem teslim işlemi davranışları değiştirin.  
  
 Bu davranışların birçoğu özniteliklerinde uygulanır ve yaptığınız gibi bunları kullanmak <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleri — uygun hizmet sınıfı veya işlem kullanımla uygulayarak. Diğer davranışları gibi <xref:System.ServiceModel.Description.ServiceMetadataBehavior> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior> nesneleri, genellikle uygulanır bir uygulama yapılandırma dosyası kullanarak da programlı olarak kullanılabilmesi için rağmen.  
  
 Örneğin, meta veri yayımlanmasını kullanılarak yapılandırılan <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesnesi. Aşağıdaki uygulama yapılandırma dosyası en yaygın kullanımını gösterir.  
  
 [!code-csharp[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.cs#1)]  
  
 Aşağıdaki bölümlerde birçok hizmet ya da istemci çalışma zamanı teslimini değiştirmek için kullanabileceğiniz en yararlı sistem tarafından sağlanan davranışları açıklanmaktadır. Her birini kullanma belirlemek için başvuru konusuna bakın.  
  
### <a name="service-behaviors"></a>Hizmet davranışları  
 Aşağıdaki hizmetleri üzerinde çalışır.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Uygulanan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet çalıştırılabilir olup olmadığını belirtmek için hizmet [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uyumluluk modunda.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Hizmet istemci talep nasıl yetkilendirir denetler.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Bir hizmeti kimlik bilgileri yapılandırır. Bu sınıf, bir X.509 sertifikası gibi hizmet kimlik bilgilerini belirtmek için kullanın.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Hata ayıklamayı etkinleştirir ve Yardım için bilgi özellikleri bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Hizmet meta verilerini ve ilişkili bilgileri yayımlanmasını denetler.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Güvenlik olaylarını denetleme davranışını belirtir.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Hizmet performansı ayarlamak etkinleştirmeniz çalışma zamanı verimliliği ayarları yapılandırır.  
  
### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Aşağıdaki davranışları uç noktaları üzerinde çalışır. Bu davranışların çoğu, istemci uygulamalarında kullanılır.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Bir geri çağırma hizmet uygulaması bir çift yönlü istemci uygulamasında yapılandırır.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Hizmeti için hata ayıklamayı etkinleştirir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] geri çağırma nesnesi.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Yanı sıra istemci ve hizmet kimlik bilgilerini yapılandırmak kullanılacak istemcide kimlik bilgisi kimlik doğrulama ayarları hizmet verir.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Taşıma kanalı oluşturulmalıdır Tekdüzen Kaynak Tanımlayıcısı (URI) belirtmek için istemciler tarafından kullanılır.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Bildirir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] devre dışı bırakmak için `MustUnderstand` işleme.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Bir zaman uyumlu çalışma zamanı bildirir alma işleminin kanalları.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Alma işlemleri destek işlem alır aktarımları için en iyi duruma getirir.  
  
### <a name="contract-behaviors"></a>Sözleşme davranışları  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Bağlamaları için hizmet veya istemci uygulaması sağlamalısınız özellik gereksinimleri belirtir.  
  
### <a name="operation-behaviors"></a>İşlemi davranışları  
 Aşağıdaki işlemi davranışları işlemleri için seri hale getirme ve işlem denetimleri belirtin.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Çalışma zamanı davranışını temsil eden <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Çalışma zamanı davranışını denetleyen `XmlSerializer` ve bir işlem ile ilişkilendirir.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Bir hizmet işlemi işlem üstbilgi kabul düzeyini belirtir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md)  
 [Nasıl yapılır: Hizmet örneği oluşturmayı denetleme](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
