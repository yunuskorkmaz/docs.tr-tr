---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: b3d3afdd1e3fba2a77186d1cd644d723c445600c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306228"
---
# <a name="how-to-export-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma
İlke onaylamalarını bir hizmet uç noktası gereksinimlerini ve özelliklerini açıklar. Hizmet uygulamaları özel ilke onaylamalarını hizmet meta verilerinde uç, iletişim için kullanabileceğiniz istemci uygulamasına bağlama veya sözleşme özelleştirme bilgileri. Uç nokta, işlem ya da ileti konular, özellikleri veya gereksinimleri iletişim kuran bağlı olarak WSDL bağlamalarda iliştirilmiş ilke ifadelerde onaylar dışarı aktarmak için Windows Communication Foundation (WCF) kullanabilirsiniz.  
  
 Özel ilke onaylamalarını dışa aktarılır uygulayarak <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve hizmet uç noktası veya bağlama öğesi uygulamanızda kaydederek bağlama doğrudan ya da bağlama öğesi ekleniyor yapılandırma dosyası. İlkeyi dışarı aktarma uygulamanıza özel ilke değerinizi olarak eklemelisiniz bir <xref:System.Xml.XmlElement?displayProperty=nameWithType> uygun örneğine <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> yöntemlere geçirilen <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi.  
  
 Buna ek olarak işaretlemeniz gerekir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter> sınıfı ve iç içe geçmiş ilke ifadeleri ve ilke framework öznitelikleri belirtilen ilke sürüme göre doğru ad alanında dışarı aktarma.  
  
 Özel ilke onaylamalarını içe aktarmak için bkz. <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> ve [nasıl yapılır: Özel ilke onaylamalarını içe aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Özel ilke onaylamalarını dışa aktarmak için  
  
1. Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Aşağıdaki kod örneği, bir özel ilke onaylama bağlama düzeyinde uygulanışı gösterilmektedir.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Program aracılığıyla bağlama veya uygulama yapılandırma dosyası kullanarak uç bağlama öğesi ekleyin. Aşağıdaki yordamlara bakın.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için  
  
1. Uygulama <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> , özel ilke onaylama bağlama öğesi için.  
  
2. Yapılandırma dosyası kullanarak bağlama öğesi uzantısı ekleyin [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) öğesi.  
  
3. Özel bağlama kullanma yapı <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Program aracılığıyla bir bağlama öğesi eklemek için  
  
1. Yeni bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ekleyebilmek için bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2. Özel bağlama 1. adımdan ekleyin. Yeni bir uç noktası için ve bu yeni hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
3. <xref:System.ServiceModel.ServiceHost>uygulamasını açın. Aşağıdaki kod örneği, özel bağlama oluşturma ve bağlama öğelerinin programlı ekleme gösterir.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
