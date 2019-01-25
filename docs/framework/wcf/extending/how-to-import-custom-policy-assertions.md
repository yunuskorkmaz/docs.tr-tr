---
title: 'Nasıl yapılır: Özel ilke onaylamalarını içe aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: ff727922aeee7aeaea801dabd842f913ce75c220
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674787"
---
# <a name="how-to-import-custom-policy-assertions"></a>Nasıl yapılır: Özel ilke onaylamalarını içe aktarma
İlke onaylamalarını bir hizmet uç noktası gereksinimlerini ve özelliklerini açıklar.  İstemci uygulamaları ilke onaylamalarını bağlama istemciyi yapılandırmak için veya bir hizmet uç noktası için hizmet sözleşmesi özelleştirmek için hizmet meta verilerinde kullanabilir.  
  
 Özel ilke onaylamalarını uygulayarak aktarılır <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimi ve söz konusu nesne meta veri sistemini veya uygulama kaydederek geçirme uygulama yapılandırma dosyanızda yazın.  Uygulamaları <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimi, varsayılan bir oluşturucu sağlamalıdır.  
  
### <a name="to-import-custom-policy-assertions"></a>Özel ilke onaylamalarını içe aktarmak için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimdeki bir sınıf. Aşağıdaki yordamlara bakın.  
  
2.  Özel ilke alma ya da ekleme tarafından:  
  
3.  Bir yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
4.  Bir yapılandırma dosyası kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aşağıdaki yordamlara bakın.  
  
5.  İlke içeri Aktarıcı programlı olarak ekleniyor. Aşağıdaki yordamlara bakın.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Herhangi bir sınıf System.ServiceModel.Description.IPolicyImportExtension arabirim uygulamak için  
  
1.  İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> yöntemi, ilgilendiğiniz her ilke konu bulun (istediğiniz onaylama kapsamını olarak) uygun yöntemi çağırarak içeri aktarmak istediğiniz ilke onaylamalarını üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> nesne geçirildi yöntem. Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> özel İlkesi onayını bulun ve tek bir adımda koleksiyondan kaldırmak için yöntemi. Bulun ve onaylama kaldırmak için kaldırma yöntemi kullanırsanız, 4. adım gerçekleştirmeniz gerekmez.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  İlke onaylamalarını işleyin. İlke sistemi Normalleştir değil Not iç içe ilkeleri ve `wsp:optional`. İlke içeri aktarma uzantısı uygulamanızda bu yapıları işlemesi gerekir.  
  
3.  Bağlama veya özellik veya İlkesi onayını tarafından belirtilen gereksinim destekleyen sözleşme özelleştirme işlemi gerçekleştirin. Genellikle onaylar bağlama belirli bir yapılandırma veya belirli bir bağlama öğesi gerektiğini belirtmiş olursunuz. Erişerek şu değişiklikleri yapın <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> özelliği. Diğer bir onayları sözleşme değiştirme gerektirir.  Erişim ve sözleşme aracılığıyla değiştirmek <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> özelliği.  İlke içeri Aktarıcı birden çok kez aynı bağlama ve sözleşme için çağrılmadığı, ancak bir ilke alternatif içe aktarılıyorsa farklı ilke alternatifleri başarısız unutmayın. Kodunuzu bu davranışı için dayanıklı olmalıdır.  
  
4.  Özel ilke onaylama onaylama koleksiyondan kaldırın. Windows Communication Foundation (WCF), ilke içeri aktarma işleminiz başarısız oldu ve ilişkili bağlama almaz onaylama kaldırmazsanız varsayar. Kullandıysanız <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> özel İlkesi onayını bulun ve bu adımı gerçekleştirmeniz gerekmez tek bir adımda koleksiyondan kaldırmak için yöntemi.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Özel ilke içeri Aktarıcı meta verilere bir yapılandırma dosyası kullanarak sistemi eklemek için  
  
1.  İçeri Aktarıcı türüne eklemek `<extensions>` öğe içinde [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) istemci yapılandırma dosyasında öğesi.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  İstemci uygulamasında <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> meta veriler ve içeri Aktarıcı çağrıldığında otomatik olarak çözümlenecek.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Özel ilke alma Svcutil.exe kullanarak meta verileri sisteme eklemek için  
  
1.  İçeri Aktarıcı türüne eklemek `<extensions>` öğe içinde [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) Svcutil.exe.config yapılandırma dosyasında öğesi. Noktası ilke alma türleri kullanarak farklı yapılandırma dosyasında kayıtlı yüklemek için Svcutil.exe ayrıca `/svcutilConfig` seçeneği.  
  
2.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veriler ve içeri Aktarıcı içeri aktarmak için otomatik olarak çağrılır.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Özel ilke alma meta verileri sisteme programlı olarak eklemek için  
  
1.  Alma için ekleme <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> özelliği (örneğin, kullanıyorsanız <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) meta verileri içeri aktarmadan önce.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
