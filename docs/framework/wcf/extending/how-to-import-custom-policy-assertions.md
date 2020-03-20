---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: ed8aae30875e3b17f65be5857c7d93af98db9b3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185562"
---
# <a name="how-to-import-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma
İlke iddiaları, bir hizmet bitiş noktasının özelliklerini ve gereksinimlerini açıklar.  İstemci uygulamaları, istemci bağlamayı yapılandırmak veya hizmet bitiş noktası için hizmet sözleşmesini özelleştirmek için hizmet meta verilerindeki ilke iddialarını kullanabilir.  
  
 Özel ilke iddiaları <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimi uygulayarak ve bu nesneyi meta veri sistemine geçirerek veya uygulama yapılandırma dosyanıza uygulama türünü kaydederek içeri alınır.  Arabirimin <xref:System.ServiceModel.Description.IPolicyImportExtension> uygulamaları parametresiz bir oluşturucu sağlamalıdır.  
  
### <a name="to-import-custom-policy-assertions"></a>Özel ilke iddialarını almak için  
  
1. Arabirimi <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bir sınıfüzerinde uygulayın. Aşağıdaki yordamlara bakın.  
  
2. Özel ilke içe aktarıcısını aşağıdakiler tarafından ekleyin:  
  
3. Yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
4. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)ile yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
5. İlke içe aktarıcısı programlı olarak eklenir. Aşağıdaki yordamlara bakın.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>System.ServiceModel.Description.IPolicyImportExtension arayüzünü herhangi bir sınıfta uygulamak için  
  
1. <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> Yöntemde, ilgilendiğiniz her ilke konusu için, yönteme geçirilen <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> nesne üzerinde uygun yöntemi (istediğiniz iddianın kapsamına bağlı olarak) çağırarak almak istediğiniz ilke iddialarını bulun. Aşağıdaki kod örneği, özel <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> ilke iddiasını bulmak ve bir adımda koleksiyondan kaldırmak için yöntemin nasıl kullanılacağını gösterir. Öneleiyi bulmak ve kaldırmak için kaldırma yöntemini kullanırsanız, adım 4 gerçekleştirmeniz gerekmez.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. İlke iddialarını işleme. İlke sisteminin iç içe olan ilkeleri normalleştirmediğini ve `wsp:optional`. Bu yapıları ilke alma uzantısı uygulamasında işlemeniz gerekir.  
  
3. İlke iddiası tarafından belirtilen yetenek veya gereksinimi destekleyen bağlama veya sözleşmeye özelleştirme gerçekleştirin. Genellikle iddialar, bağlamanın belirli bir yapılandırma veya belirli bir bağlama öğesi gerektirdiğini gösterir. <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> Tesise erişerek bu değişiklikleri yapın. Diğer iddialar, sözleşmeyi değiştirmenizi gerektirir.  Mülkü kullanarak sözleşmeye erişebilir <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> ve sözleşmeyi değiştirebilirsiniz.  İlke içe aktarıcınızın aynı bağlama ve sözleşme için birden çok kez çağrılabileceğini, ancak bir ilke alternatifi içe aktarma başarısız olursa farklı ilke alternatifleri olabileceğini unutmayın. Kodunuz bu davranışa dayanıklı olmalıdır.  
  
4. Özel ilke iddiasını seves koleksiyonundan kaldırın. Windows Communication Foundation (WCF) ilkesini kaldırmazsanız, ilke alma işleminin başarısız olduğunu varsayar ve ilişkili bağlamayı almaz. Özel ilke <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> iddiasını bulmak ve bir adımda koleksiyondan kaldırmak için yöntemi kullandıysanız, bu adımı gerçekleştirmeniz gerekmez.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Yapılandırma dosyasını kullanarak meta veri sistemine özel ilke aktarıcıeklemek için  
  
1. İstemci yapılandırma dosyasındaki `<extensions>`>öğesi [ \<içini içindeki](../../configure-apps/file-schema/wcf/policyimporters.md) öğeye içe aktarıcı türünü ekleyin.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. İstemci uygulamasında, <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> meta <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> verileri kullanmak veya çözmek için ve içe aktarıcı otomatik olarak çağrılır.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Svcutil.exe kullanarak meta veri sistemine özel ilke alıcı eklemek için  
  
1. Svcutil.exe.config yapılandırma dosyasındaki `<extensions>` [ \<>](../../configure-apps/file-schema/wcf/policyimporters.md) öğesinin içindeki öğeye ithalatçı türünü ekleyin. `/svcutilConfig` Ayrıca, seçeneği kullanarak farklı bir yapılandırma dosyasında kayıtlı ilke içeni türlerini yüklemek için Svcutil.exe'yi işaret edebilirsiniz.  
  
2. Meta verileri almak için [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın ve ithalatçı otomatik olarak çağrılır.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Özel ilke içe aktarıcısını programlı olarak meta veri sistemine eklemek için  
  
1. Meta verileri almadan <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> önce içe aktarıcıyı özelliğe ekleyin (örneğin, bu <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>verileri kullanıyorsanız).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Meta Veri Sistemini Genişletme](extending-the-metadata-system.md)
