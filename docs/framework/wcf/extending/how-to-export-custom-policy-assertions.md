---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 8bdc9948d6846631fde1d428c113682f40d15ec3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249221"
---
# <a name="how-to-export-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma

İlke onayları bir hizmet uç noktasının yeteneklerini ve gereksinimlerini anlatmaktadır. Hizmet uygulamaları, uç nokta, bağlama veya sözleşme özelleştirme bilgilerini istemci uygulamasına iletmek için hizmet meta verilerinde özel ilke onayları kullanabilir. İletişim kurduğunuz yeteneklere veya gereksinimlere bağlı olarak, bir uç nokta, işlem veya ileti konusunda WSDL bağlamalarında ekli ilke ifadelerinde onayları dışarı aktarmak için Windows Communication Foundation (WCF) kullanabilirsiniz.  
  
 Özel ilke onayları, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> bir üzerinde arabirimini uygulayarak <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve bağlama öğesini doğrudan hizmet uç noktasının bağlamasına veya uygulama yapılandırma dosyanıza kaydederek bağlama öğesini ekleyerek verilir. İlke dışa aktarma uygulamanız, özel ilke onayınız <xref:System.Xml.XmlElement?displayProperty=nameWithType> için yönteme geçirilecek uygun bir örnek olarak eklemesi gerekir <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> .  
  
 Ayrıca, <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> sınıfının özelliğini denetlemeniz <xref:System.ServiceModel.Description.WsdlExporter> ve iç içe geçmiş ilke ifadelerini ve ilke çerçevesi özniteliklerini belirtilen ilke sürümüne göre doğru ad alanında dışarı aktarmanız gerekir.  
  
 Özel ilke onaylamalarını içeri aktarmak için bkz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> . ve [nasıl yapılır: özel ilke onaylamalarını içeri aktarma](how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Özel ilke onaylamalarını dışarı aktarmak için  
  
1. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>Arabirimini bir üzerinde uygulayın <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> . Aşağıdaki kod örneği, bağlama düzeyinde özel bir ilke onaylama uygulamasının uygulanmasını gösterir.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Bağlama öğesini program aracılığıyla veya bir uygulama yapılandırma dosyası kullanarak uç nokta bağlamaya ekleyin. Aşağıdaki yordamlara bakın.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Bir uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için  
  
1. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>Özel ilke onaylama bağlama öğesi için uygulayın.  
  
2. Bağlama öğesi uzantısını öğesini kullanarak yapılandırma dosyasına ekleyin [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .  
  
3. Kullanarak özel bir bağlama oluşturun <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> .  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Programlı olarak bir bağlama öğesi eklemek için  
  
1. Yeni bir oluşturun <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ' a ekleyin <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> .  
  
2. Adım 1 ' den özel bağlamayı ekleyin. Yeni bir uç noktaya ekleyin ve yöntemini çağırarak bu yeni hizmet uç noktasını öğesine ekleyin <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .  
  
3. <xref:System.ServiceModel.ServiceHost>uygulamasını açın. Aşağıdaki kod örneği, özel bir bağlamanın oluşturulmasını ve bağlama öğelerinin programlı olarak eklenmesini gösterir.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma](how-to-import-custom-policy-assertions.md)
