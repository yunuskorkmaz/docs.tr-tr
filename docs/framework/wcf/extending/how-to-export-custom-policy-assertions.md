---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795674"
---
# <a name="how-to-export-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma
İlke onayları bir hizmet uç noktasının yeteneklerini ve gereksinimlerini anlatmaktadır. Hizmet uygulamaları, uç nokta, bağlama veya sözleşme özelleştirme bilgilerini istemci uygulamasına iletmek için hizmet meta verilerinde özel ilke onayları kullanabilir. İletişim kurduğunuz yeteneklere veya gereksinimlere bağlı olarak, bir uç nokta, işlem veya ileti konusunda WSDL bağlamalarında ekli ilke ifadelerinde onayları dışarı aktarmak için Windows Communication Foundation (WCF) kullanabilirsiniz.  
  
 Özel ilke onayları, bir <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> üzerinde arabirimini uygulayarak ve bağlama öğesini doğrudan hizmet uç noktası bağlamaya veya uygulamanıza bağlama öğesini kaydederek içe aktarılabilir. yapılandırma dosyası. İlke dışa aktarma uygulamanız, özel ilke <xref:System.Xml.XmlElement?displayProperty=nameWithType> onayınız için <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yönteme <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> geçirilecek uygun <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> bir örnek olarak eklemesi gerekir.  
  
 Ayrıca, <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> <xref:System.ServiceModel.Description.WsdlExporter> sınıfının özelliğini denetlemeniz ve iç içe geçmiş ilke ifadelerini ve ilke çerçevesi özniteliklerini belirtilen ilke sürümüne göre doğru ad alanında dışarı aktarmanız gerekir.  
  
 Özel ilke onaylamalarını içeri aktarmak için <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bkz [. ve nasıl yapılır: Özel Ilke onaylamalarını](how-to-import-custom-policy-assertions.md)içeri aktarma.  
  
### <a name="to-export-custom-policy-assertions"></a>Özel ilke onaylamalarını dışarı aktarmak için  
  
1. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> Arabirimini bir<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>üzerinde uygulayın. Aşağıdaki kod örneği, bağlama düzeyinde özel bir ilke onaylama uygulamasının uygulanmasını gösterir.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Bağlama öğesini program aracılığıyla veya bir uygulama yapılandırma dosyası kullanarak uç nokta bağlamaya ekleyin. Aşağıdaki yordamlara bakın.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Bir uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için  
  
1. Özel <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> ilke onaylama bağlama öğesi için uygulayın.  
  
2. Bağlama öğesi uzantısını [ \<BindingElementExtensions >](../../configure-apps/file-schema/wcf/bindingelementextensions.md) öğesini kullanarak yapılandırma dosyasına ekleyin.  
  
3. Kullanarak özel bir bağlama oluşturun <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Programlı olarak bir bağlama öğesi eklemek için  
  
1. Yeni <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> bir oluşturun ve ' a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>ekleyin.  
  
2. Adım 1 ' den özel bağlamayı ekleyin. Yeni bir uç noktaya ekleyin ve <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemini çağırarak bu yeni hizmet uç noktasını öğesine ekleyin.  
  
3. <xref:System.ServiceModel.ServiceHost>uygulamasını açın. Aşağıdaki kod örneği, özel bir bağlamanın oluşturulmasını ve bağlama öğelerinin programlı olarak eklenmesini gösterir.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Nasıl yapılır: Özel Ilke onaylamalarını içeri aktar](how-to-import-custom-policy-assertions.md)
