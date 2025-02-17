---
description: 'Daha fazla bilgi edinin: Service Run-Time davranışını belirtme'
title: Hizmet Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: a7336a64c32773b0fa960879021bb04cccfaa24f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703490"
---
# <a name="specifying-service-run-time-behavior"></a>Hizmet Çalışma Zamanı Davranışını Belirtme

Bir hizmet sözleşmesini tasarladıktan ([hizmet sözleşmeleri tasarladıktan](designing-service-contracts.md)) ve hizmet sözleşmenizi ([hizmet sözleşmelerini uygulama](implementing-service-contracts.md)) uyguladıktan sonra, hizmet çalışma zamanının işlem davranışını yapılandırabilirsiniz. Bu konuda, sistem tarafından sunulan hizmet ve işlem davranışları açıklanmakta ve yeni davranışlar oluşturmak için nereden daha fazla bilgi bulacağınız açıklanmaktadır. Bazı davranışlar öznitelik olarak uygulandığından, çoğu uygulama yapılandırma dosyası veya programlı olarak uygulanır. Hizmet uygulamanızı yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetleri yapılandırma](configuring-services.md).  
  
## <a name="overview"></a>Genel Bakış  

 Sözleşme, bu türdeki bir hizmetin giriş, çıkış, veri türleri ve yeteneklerini tanımlar. Bir hizmet sözleşmesinin uygulanması, bir adreste bağlama ile yapılandırıldığında, uyguladığı Sözleşmeyi yerine getiren bir sınıf oluşturur. Sözleşme, bağlama ve adres bilgilerinin hepsi istemci tarafından bilinir; istemci bu olmadan hizmeti kullanamaz.  
  
 Ancak, iş parçacığı sorunları veya örnek yönetimi gibi işlem özellikleri, istemciler için opaktır. Hizmet sözleşmenizi uyguladıktan sonra, *davranışları* kullanarak çok sayıda işlem özelliği yapılandırabilirsiniz. Davranışlar, çalışma zamanı özelliğini ayarlayarak ya da çalışma zamanına bir özelleştirme türü ekleyerek Windows Communication Foundation (WCF) çalışma zamanını değiştiren nesnelerdir. Kullanıcı tanımlı davranışlar oluşturarak çalışma zamanını değiştirme hakkında daha fazla bilgi için bkz. [ServiceHost ve hizmet modeli katmanını genişletme](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>Ve <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> öznitelikleri en yaygın olarak kullanılan davranışlardır ve en sık istenen işlem özelliklerini kullanıma sunar. Öznitelikleri olduklarından, bunları hizmet veya işlem uygulamasına uygularsınız. Ya da gibi diğer davranışlar <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType> genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır, ancak bunları programlı bir şekilde kullanabilirsiniz.  
  
 Bu konu, ve özniteliklerine genel bir bakış sunar <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> , davranışların çalışacağı çeşitli kapsamları AÇıKLAR ve WCF geliştiricilerine ilgi çekici olabilecek çeşitli kapsamlar üzerinde sistem tarafından sağlanan davranışların birçoğu için hızlı bir açıklama sağlar.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute ve OperationBehaviorAttribute  

 En önemli davranışlar, <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini denetlemek için kullanabileceğiniz ve öznitelikleridir:  
  
- Örnek yaşam süreleri  
  
- Eşzamanlılık ve eşitleme desteği  
  
- Yapılandırma davranışı  
  
- İşlem davranışı  
  
- Serileştirme davranışı  
  
- Meta veri dönüştürme  
  
- Oturum ömrü  
  
- Adres Filtreleme ve üstbilgi işleme  
  
- Kimliğe bürünme  
  
- Bu öznitelikleri kullanmak için, hizmet veya işlem uygulamasını söz konusu kapsama uygun özniteliğiyle işaretleyin ve özellikleri ayarlayın. Örneğin, aşağıdaki kod örneği, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> Bu işlemin çağrı yapanların kimliğe bürünme özelliğini desteklemesini gerektiren özelliği kullanan bir işlem uygulamasını gösterir.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Özelliklerin birçoğu bağlamadan ek destek gerektirir. Örneğin, istemciden bir işlem gerektiren bir işlem, akışlı işlemleri destekleyen bir bağlama kullanacak şekilde yapılandırılmalıdır.  
  
### <a name="well-known-singleton-services"></a>Well-Known Singleton Hizmetleri  

 <xref:System.ServiceModel.ServiceBehaviorAttribute>Ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini, her ikisi de <xref:System.ServiceModel.InstanceContext> işlemleri uygulayan hizmet nesnelerinin belirli yaşam sürelerini denetlemek için kullanabilirsiniz.  
  
 Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği ne sıklıkla <xref:System.ServiceModel.InstanceContext> yayımlanacağını ve <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> hizmet nesnesi serbest bırakıldığında ve özelliklerini denetler.  
  
 Bununla birlikte, kendiniz de bir hizmet nesnesi oluşturabilir ve bu nesneyi kullanarak hizmet konağını oluşturabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.InstanceContextMode.Single> hizmet ana bilgisayarı açıldığında özelliği olarak ayarlamanız veya bir özel durum oluşturulması gerekir.  
  
 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29>Bu tür bir hizmet oluşturmak için oluşturucuyu kullanın. <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType>Tek bir hizmet tarafından kullanılmak üzere belirli bir nesne örneği sağlamak istediğinizde özel uygulamaya bir alternatif sağlar. Bu aşırı yüklemeyi, hizmet uygulama türü oluşturulması zor olduğunda kullanabilirsiniz (örneğin, parametresiz bir ortak Oluşturucu uygulamadıysanız).
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) örnek oluşturma davranışıyla ilgili bazı özelliklerin farklı şekilde çalıştığını unutmayın. Örneğin, <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> iyi bilinen bir nesne örneği sağlandığında çağırmanın hiçbir etkisi yoktur. Benzer şekilde, diğer örnek yayın mekanizması yok sayılır. <xref:System.ServiceModel.ServiceHost>Sınıfı her zaman <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği tüm işlemler için olarak ayarlanmış gibi davranır <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> .  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Diğer hizmet, uç nokta, sözleşme ve Işlem davranışları  

 Özniteliği gibi hizmet davranışları <xref:System.ServiceModel.ServiceBehaviorAttribute> bir hizmetin tamamında çalışır. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliğini olarak ayarlarsanız, <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> söz konusu hizmette her bir işlem içindeki iş parçacığı eşitleme sorunlarını işlemeniz gerekir. Uç nokta davranışları bir uç nokta boyunca çalışır; sistem tarafından sunulan uç nokta davranışlarının birçoğu istemci işlevselliğine yöneliktir. Sözleşme davranışları sözleşme düzeyinde çalışır ve işlem davranışları işlem teslimini değiştirir.  
  
 Bu davranışların birçoğu özniteliklere uygulanır ve bunları <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> uygun hizmet sınıfına veya işlem uygulamasına uygulayarak, ve özniteliklerini yaptığınız şekilde kullanabilirsiniz. Ya da nesneleri gibi diğer davranışlar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> <xref:System.ServiceModel.Description.ServiceDebugBehavior> genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır, ancak program aracılığıyla da kullanılabilir.  
  
 Örneğin, meta veri yayını nesnesi kullanılarak yapılandırılır <xref:System.ServiceModel.Description.ServiceMetadataBehavior> . Aşağıdaki uygulama yapılandırma dosyasında en sık kullanılan kullanım gösterilmektedir.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Aşağıdaki bölümlerde, hizmetinizin veya istemcinizin çalışma zamanının dağıtımını değiştirmek için kullanabileceğiniz en yararlı sistem tarafından sağlanmış davranışların birçoğu açıklanır. Her birinin nasıl kullanılacağını öğrenmek için başvuru konusuna bakın.  
  
### <a name="service-behaviors"></a>Hizmet davranışları  

 Aşağıdaki davranışlar hizmetler üzerinde çalışır.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Hizmetin ASP.NET uyumluluk modunda çalıştırılıp çalıştırılamayacağını göstermek için bir WCF hizmetine uygulanır.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Hizmetin istemci taleplerini nasıl yetkilendiğini denetler.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Hizmet kimlik bilgilerini yapılandırır. Hizmetin kimlik bilgisini (örneğin, X. 509.440 sertifikası) belirtmek için bu sınıfı kullanın.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. WCF hizmeti için hata ayıklama ve yardım bilgileri özelliklerini sağlar.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Hizmet meta verilerinin ve ilgili bilgilerin yayımlanmasını denetler.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Güvenlik olaylarının Denetim davranışını belirtir.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Hizmet performansını ayarlamanıza olanak tanıyan çalışma zamanı işleme ayarlarını yapılandırır.  
  
### <a name="endpoint-behaviors"></a>Uç nokta davranışları  

 Aşağıdaki davranışlar uç noktalar üzerinde çalışır. Bu davranışların birçoğu istemci uygulamalarında kullanılır.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Bir çift yönlü istemci uygulamasında bir geri arama hizmeti uygulaması yapılandırır.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. WCF geri çağırma nesnesi için hizmet hata ayıklamasını sağlar.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Kullanıcının istemci ve hizmet kimlik bilgilerinin yanı sıra istemcide kullanılmak üzere hizmet kimlik bilgileri kimlik doğrulama ayarlarını yapılandırmasına izin verir.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. İstemci tarafından, aktarım kanalının oluşturulması gereken Tekdüzen Kaynak tanımlayıcısını (URI) belirtmek için kullanılır.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. WCF 'nin işlemeyi devre dışı bırakmasına izin verir `MustUnderstand` .  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Çalışma zamanına kanallar için zaman uyumlu alma işlemi kullanmasını söyler.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. İşlem alma işlemini destekleyen taşıtlar için alma işlemlerini iyileştirir.  
  
### <a name="contract-behaviors"></a>Sözleşme davranışları  

 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Bağlamaların hizmet veya istemci uygulamasına sağlaması gereken özellik gereksinimlerini belirtir.  
  
### <a name="operation-behaviors"></a>İşlem davranışları  

 Aşağıdaki işlem davranışları işlemler için serileştirme ve işlem denetimleri belirtir.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Öğesinin çalışma zamanı davranışını temsil eder <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> .  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Çalışma zamanı davranışını denetler `XmlSerializer` ve bir işlemle ilişkilendirir.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Bir hizmet işleminin bir işlem üst bilgisini kabul ettiği düzeyi belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](configuring-services.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](./feature-details/how-to-control-service-instancing.md)
