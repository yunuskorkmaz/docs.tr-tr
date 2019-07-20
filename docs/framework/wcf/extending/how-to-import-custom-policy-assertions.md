---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: 627b68d707dbedfaf6a291f2ab22dbc9a4f60835
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363849"
---
# <a name="how-to-import-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma
İlke onayları bir hizmet uç noktasının yeteneklerini ve gereksinimlerini anlatmaktadır.  İstemci uygulamaları, hizmet meta verilerinde ilke onayları kullanarak istemci bağlamasını yapılandırabilir veya bir hizmet uç noktası için hizmet sözleşmesini özelleştirebilir.  
  
 Özel ilke onayları, <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimini uygulayarak içeri aktarılır ve bu nesne meta veri sistemine geçirerek ya da uygulama yapılandırma dosyanıza uygulama türünü kaydederek içeri aktarılır.  <xref:System.ServiceModel.Description.IPolicyImportExtension> Arabirim uygulamalarının parametresiz bir Oluşturucu sağlaması gerekir.  
  
### <a name="to-import-custom-policy-assertions"></a>Özel ilke onaylamalarını içeri aktarmak için  
  
1. <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> Arabirimini bir sınıfa uygulayın. Aşağıdaki yordamlara bakın.  
  
2. Özel ilke içe aktarıcı şu şekilde ekleyin:  
  
3. Yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
4. [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ile bir yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
5. İlke İçeri Aktarıcı programlı bir şekilde ekleniyor. Aşağıdaki yordamlara bakın.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Herhangi bir sınıfta System. ServiceModel. Description. IPolicyImportExtension arabirimini uygulamak için  
  
1. Yönteminde, ilgilendiğiniz her ilke konusu için, uygun yöntemi (istediğiniz onaylama kapsamına bağlı olarak) <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> çağırarak, içeri aktarmak istediğiniz ilke onaylamalarını bulun. <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> yöntemidir. Aşağıdaki kod örneği, özel ilke onayını bulmak ve <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> tek bir adımda koleksiyondan kaldırmak için yönteminin nasıl kullanılacağını gösterir. Onaylama işlemini bulmak ve kaldırmak için Remove yöntemini kullanırsanız, 4. adımı gerçekleştirmeniz gerekmez.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. İlke onaylamalarını işleyin. İlke sisteminin iç içe geçmiş ilkeleri ve ile `wsp:optional`normalleştirmediğini unutmayın. Bu yapıları ilke içeri aktarma uzantı uygulamanızda işlemelidir.  
  
3. İlke onaylama işlemi tarafından belirtilen yeteneği veya gereksinimi destekleyen bağlama veya sözleşmede özelleştirmeyi gerçekleştirin. Genellikle Onaylamalar, bir bağlamanın belirli bir yapılandırma veya belirli bir bağlama öğesi gerektirdiğini gösterir. Bu değişiklikleri <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> özelliğe erişerek yapın. Diğer Onaylamalar, sözleşmeyi değiştirmenizi gerektirir.  <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> Özelliği kullanarak sözleşmeye erişebilir ve bunları değiştirebilirsiniz.  İlke içeri aktarmalarınızın aynı bağlama ve anlaşma için birden çok kez çağrılabilecek olduğunu, ancak bir ilkeyi içeri aktarma işlemi başarısız olursa farklı ilke alternatiflerine sahip olabileceğini unutmayın. Kodunuzun bu davranışa dayanıklı olması gerekir.  
  
4. Özel ilke onayını onaylama koleksiyonundan kaldırın. Onaylama kaldırma Windows Communication Foundation (WCF), ilke içeri aktarmanın başarısız olduğunu varsayar ve ilişkili bağlamayı içeri aktarmaz. Özel ilke onaylama işlemini <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> bulmak ve tek bir adımda koleksiyondan kaldırmak için yöntemini kullandıysanız, bu adımı gerçekleştirmeniz gerekmez.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Özel ilke alma aracını bir yapılandırma dosyası kullanarak meta veri sistemine eklemek için  
  
1. İçeri aktarma türünü `<extensions>` , istemci yapılandırma dosyasındaki [ \<PolicyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) öğesinin içindeki öğeye ekleyin.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2. İstemci uygulamasında, meta verileri çözümlemek için <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> kullanın ve içeri aktarma otomatik olarak çağrılır.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Özel ilke İçeri Aktarıcı ' yı Svcutil. exe kullanarak meta veri sistemine eklemek için  
  
1. Alıcı türünü `<extensions>` Svcutil. exe. config yapılandırma dosyasındaki [ \<PolicyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) öğesinin içindeki öğeye ekleyin. Ayrıca, `/svcutilConfig` seçeneği kullanılarak farklı bir yapılandırma dosyasına kayıtlı ilke İçeri Aktarıcı türlerini yüklemek için Svcutil. exe ' yi de kullanabilirsiniz.  
  
2. Meta verileri içeri aktarmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın ve içeri aktarma otomatik olarak çağrılır.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Özel ilke içe aktarıcı 'nın meta veri sistemine programlı bir şekilde eklenmesini sağlamak için  
  
1. Meta verileri içeri aktarmadan önce <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> özelliğine içeri aktarma özelliğini ekleyin (örneğin, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>kullanıyorsanız).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
