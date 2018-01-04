---
title: "Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma"
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
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 916f5b820ce9e1c30c13a9834548c83e32bc3579
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-import-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma
İlke onaylamalarını hizmet uç noktası gereksinimlerini ve özelliklerini açıklar.  İstemci uygulamaları ilke onaylamalarını hizmeti meta verilerde bağlama istemcisini yapılandırmak için veya bir hizmet uç noktası için hizmet sözleşmesini özelleştirmek için kullanabilirsiniz.  
  
 Özel ilke onaylamalarını uygulayarak alınır <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimi ve meta veri sistemi veya uygulama kaydı tarafından söz konusu nesne geçirme, uygulama yapılandırma dosyasında yazın.  Uygulamaları <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimi, varsayılan bir oluşturucu sağlamalıdır.  
  
### <a name="to-import-custom-policy-assertions"></a>Özel ilke onaylamalarını içe aktarmak için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirim üzerinde bir sınıf. Aşağıdaki yordamlara bakın.  
  
2.  Özel ilke alma ya da Ekle tarafından:  
  
3.  Bir yapılandırma dosyası kullanarak. Aşağıdaki yordamlara bakın.  
  
4.  Bir yapılandırma dosyası kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aşağıdaki yordamlara bakın.  
  
5.  Program aracılığıyla ilke alma ekleniyor. Aşağıdaki yordamlara bakın.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Herhangi bir sınıf System.ServiceModel.Description.IPolicyImportExtension arabirimi uygulamak için  
  
1.  İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> yöntemi için ilgilendiğiniz her ilke konu bulun (istediğiniz onaylama kapsamını bağlı olarak) uygun yöntemini çağırarak içeri aktarmak istediğiniz ilke onaylamalarını üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> nesnesi geçirildi yöntem. Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> özel ilke onaylama bulun ve tek bir adımda koleksiyondan kaldırmak için yöntem. Bulun ve onay kaldırmak için Kaldır yöntemi kullanırsanız, 4. adım gerçekleştirmeniz gerekmez.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  İlke onaylamalarını işleyin. İlke sistemi değil normalleştirin Not iç içe ilkeleri ve `wsp:optional`. İlke içeri aktarma uzantısı uygulamanızda bu yapıları işlemesi gerekir.  
  
3.  Bağlama veya yetenek veya ilke onaylama işlemi tarafından belirtilen gereksinim destekleyen sözleşme özelleştirme gerçekleştirin. Genellikle bir bağlama belirli bir yapılandırma veya belirli bağlama öğesi gerektiriyor onaylar gösterir. Erişerek bu değişiklikleri yapmak <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> özelliği. Diğer onaylar sözleşme değiştirmeniz gerekir.  Erişim ve sözleşme kullanarak değiştirme <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> özelliği.  İlke içeri Aktarıcı birden çok kez aynı bağlama ve sözleşme için çağrılmadığı, ancak bir ilke alternatif alınıyorsa farklı ilke alternatifleri başarısız unutmayın. Kodunuzu bu davranış dayanıklı olması gerekir.  
  
4.  Özel ilke onaylama onaylama koleksiyondan kaldırın. Onaylama işlemi kaldırmazsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ilke alma işlemi başarısız oldu ve ilişkili bağlama almaz varsayar. Kullandıysanız <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> özel ilke onaylama bulun ve bu adımı gerçekleştirmeniz gerekmez tek bir adımda koleksiyondan kaldırmak için yöntem.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Bir yapılandırma dosyası kullanarak sistem meta veri özel ilkesine içeri Aktarıcı eklemek için  
  
1.  Alıcı türü eklemek `<extensions>` öğesi içinde [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) istemci yapılandırma dosyası öğesi.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  İstemci uygulamada kullanmak <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> meta verileri ve içeri Aktarıcı çağrılır otomatik olarak çözümlenecek.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Özel ilke alma Svcutil.exe kullanarak meta verileri sistemine eklemek için  
  
1.  Alıcı türü eklemek `<extensions>` öğesi içinde [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) Svcutil.exe.config yapılandırma dosyası öğesi. Noktası kullanarak farklı yapılandırma dosyasında kayıtlı ilke alma türleri yüklemek için Svcutil.exe kullanabileceğiniz `/svcutilConfig` seçeneği.  
  
2.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verileri ve içeri Aktarıcı almak için otomatik olarak çağrılır.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Özel ilke alma meta verileri sisteme programlı olarak eklemek için  
  
1.  Alma için ekleme <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> özelliği (örneğin, kullanıyorsanız <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) meta verileri içe aktarma önce.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 [Meta Veri Sistemini Genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
