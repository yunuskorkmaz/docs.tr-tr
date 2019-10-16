---
title: Hizmet Çalışma Zamanı Davranışını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 087aaf5ebc69046d5404765114cfaecd28798915
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321386"
---
# <a name="specifying-service-run-time-behavior"></a>Hizmet Çalışma Zamanı Davranışını Belirtme
Bir hizmet sözleşmesini tasarladıktan ([hizmet sözleşmeleri tasarladıktan](designing-service-contracts.md)) ve hizmet sözleşmenizi ([hizmet sözleşmelerini uygulama](implementing-service-contracts.md)) uyguladıktan sonra, hizmet çalışma zamanının işlem davranışını yapılandırabilirsiniz. Bu konuda, sistem tarafından sunulan hizmet ve işlem davranışları açıklanmakta ve yeni davranışlar oluşturmak için nereden daha fazla bilgi bulacağınız açıklanmaktadır. Bazı davranışlar öznitelik olarak uygulandığından, çoğu uygulama yapılandırma dosyası veya programlı olarak uygulanır. Hizmet uygulamanızı yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetleri yapılandırma](configuring-services.md).  
  
## <a name="overview"></a>Genel bakış  
 Sözleşme, bu türdeki bir hizmetin giriş, çıkış, veri türleri ve yeteneklerini tanımlar. Bir hizmet sözleşmesinin uygulanması, bir adreste bağlama ile yapılandırıldığında, uyguladığı Sözleşmeyi yerine getiren bir sınıf oluşturur. Sözleşme, bağlama ve adres bilgilerinin hepsi istemci tarafından bilinir; istemci bu olmadan hizmeti kullanamaz.  
  
 Ancak, iş parçacığı sorunları veya örnek yönetimi gibi işlem özellikleri, istemciler için opaktır. Hizmet sözleşmenizi uyguladıktan sonra, *davranışları*kullanarak çok sayıda işlem özelliği yapılandırabilirsiniz. Davranışlar, çalışma zamanı özelliğini ayarlayarak ya da çalışma zamanına bir özelleştirme türü ekleyerek Windows Communication Foundation (WCF) çalışma zamanını değiştiren nesnelerdir. Kullanıcı tanımlı davranışlar oluşturarak çalışma zamanını değiştirme hakkında daha fazla bilgi için bkz. [ServiceHost ve hizmet modeli katmanını genişletme](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 @No__t-0 ve <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> öznitelikleri en yaygın olarak kullanılan davranışlardır ve en sık istenen işlem özelliklerini kullanıma sunar. Öznitelikleri olduklarından, bunları hizmet veya işlem uygulamasına uygularsınız. @No__t-0 veya <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType> gibi diğer davranışlar genellikle bir uygulama yapılandırma dosyası kullanılarak uygulanır, ancak bunları programlı olarak kullanabilirsiniz.  
  
 Bu konu, <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerine genel bir bakış sağlar, davranışların çalışacağı çeşitli kapsamları açıklar ve WCF ile ilgili olabilecek çeşitli kapsamlar üzerinde sistem tarafından sağlanan davranışların birçoğu için hızlı bir açıklama sağlar geliştiricilerinin.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute ve OperationBehaviorAttribute  
 En önemli davranışlar, denetlemek için kullanabileceğiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> öznitelikleridir:  
  
- Örnek yaşam süreleri  
  
- Eşzamanlılık ve eşitleme desteği  
  
- Yapılandırma davranışı  
  
- İşlem davranışı  
  
- Serileştirme davranışı  
  
- Meta veri dönüştürme  
  
- Oturum ömrü  
  
- Adres Filtreleme ve üstbilgi işleme  
  
- Kimliğe bürünme  
  
- Bu öznitelikleri kullanmak için, hizmet veya işlem uygulamasını söz konusu kapsama uygun özniteliğiyle işaretleyin ve özellikleri ayarlayın. Örneğin, aşağıdaki kod örneği, bu işlemin çağıranlarının kimliğe bürünme özelliğini desteklemesini gerektirmek için <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> özelliğini kullanan bir işlem uygulamasını gösterir.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Özelliklerin birçoğu bağlamadan ek destek gerektirir. Örneğin, istemciden bir işlem gerektiren bir işlem, akışlı işlemleri destekleyen bir bağlama kullanacak şekilde yapılandırılmalıdır.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 @No__t-0 ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini, her ikisi de işlemleri uygulayan <xref:System.ServiceModel.InstanceContext> ve hizmet nesnelerinin belirli yaşam sürelerini denetlemek için kullanabilirsiniz.  
  
 Örneğin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği, <xref:System.ServiceModel.InstanceContext> ' in ne sıklıkta yayınlanacağını ve hizmet nesnesi yayınlandığında <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> Özellikler denetimini denetler.  
  
 Bununla birlikte, kendiniz de bir hizmet nesnesi oluşturabilir ve bu nesneyi kullanarak hizmet konağını oluşturabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.InstanceContextMode.Single> olarak ayarlamanız gerekir ya da hizmet ana bilgisayarı açıldığında bir özel durum oluşturulur.  
  
 Böyle bir hizmet oluşturmak için <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> oluşturucusunu kullanın. Tek bir hizmet tarafından kullanılmak üzere belirli bir nesne örneği sağlamak istediğinizde, özel bir @no__t uygulamak için bir alternatif sağlar. Bu aşırı yüklemeyi, hizmet uygulama türü oluşturulması zor olduğunda kullanabilirsiniz (örneğin, hiçbir parametresi olmayan varsayılan bir ortak Oluşturucu uygulamaz).  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) örnek oluşturma davranışıyla ilgili bazı özelliklerin farklı şekilde çalıştığını unutmayın. Örneğin, <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> ' ı çağırmak iyi bilinen bir nesne örneği sağlandığında hiçbir etkiye sahip değildir. Benzer şekilde, diğer örnek yayın mekanizması yok sayılır. @No__t-0 sınıfı her zaman <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği tüm işlemler için <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> olarak ayarlanmış gibi davranır.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Diğer hizmet, uç nokta, sözleşme ve Işlem davranışları  
 @No__t-0 özniteliği gibi hizmet davranışları bir hizmetin tamamında çalışır. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> olarak ayarlarsanız, söz konusu hizmette her bir işlem içindeki iş parçacığı eşitleme sorunlarını işlemeniz gerekir. Uç nokta davranışları bir uç nokta boyunca çalışır; sistem tarafından sunulan uç nokta davranışlarının birçoğu istemci işlevselliğine yöneliktir. Sözleşme davranışları sözleşme düzeyinde çalışır ve işlem davranışları işlem teslimini değiştirir.  
  
 Bu davranışların birçoğu özniteliklere uygulanır ve bunları uygun hizmet sınıfına veya işlem uygulamasına uygulayarak <xref:System.ServiceModel.ServiceBehaviorAttribute> ve <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliklerini yaptığınız gibi kullanırsınız. @No__t-0 veya <xref:System.ServiceModel.Description.ServiceDebugBehavior> nesneleri gibi diğer davranışlar, genellikle program aracılığıyla da kullanılabilmesine rağmen bir uygulama yapılandırma dosyası kullanılarak uygulanır.  
  
 Örneğin, meta veri yayını <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nesnesi kullanılarak yapılandırılır. Aşağıdaki uygulama yapılandırma dosyasında en sık kullanılan kullanım gösterilmektedir.  
  
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
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. WCF 'nin `MustUnderstand` işlemesini devre dışı bırakmasına izin verir.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Çalışma zamanına kanallar için zaman uyumlu alma işlemi kullanmasını söyler.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. İşlem alma işlemini destekleyen taşıtlar için alma işlemlerini iyileştirir.  
  
### <a name="contract-behaviors"></a>Sözleşme davranışları  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Bağlamaların hizmet veya istemci uygulamasına sağlaması gereken özellik gereksinimlerini belirtir.  
  
### <a name="operation-behaviors"></a>İşlem davranışları  
 Aşağıdaki işlem davranışları işlemler için serileştirme ve işlem denetimleri belirtir.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. @No__t-0 ' ın çalışma zamanı davranışını temsil eder.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. @No__t-0 ' ın çalışma zamanı davranışını denetler ve bir işlemle ilişkilendirir.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Bir hizmet işleminin bir işlem üst bilgisini kabul ettiği düzeyi belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](configuring-services.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](./feature-details/how-to-control-service-instancing.md)
