---
title: "Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma"
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
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8620dec4997947df2dc7078e337a5e421d66c55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma
İlke onaylamalarını hizmet uç noktası gereksinimlerini ve özelliklerini açıklar. Hizmet uygulamaları özel ilke onaylamalarını hizmeti meta verilerde bitiş noktası, iletişim kurmak için kullanabileceğiniz istemci uygulamasına bağlama veya sözleşme özelleştirme bilgileri. Kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL bağlamalarda uç noktası, işlem veya özelliklerini veya gereksinimleri iletişim bağlı olarak, ileti konuları iliştirilmiş ilke ifadelerde onaylar vermek için.  
  
 Özel ilke onaylamalarını dışa aktarılır uygulayarak <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve hizmet uç noktası ya da bağlama öğesi uygulamanızda kaydetme bağlama doğrudan ya da bağlama öğesi ekleniyor yapılandırma dosyası. İlke verme uygulamanıza özel ilke değerinizi olarak eklemelisiniz bir <xref:System.Xml.XmlElement?displayProperty=nameWithType> uygun örneğine <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> içine geçirilen <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi.  
  
 Buna ek olarak işaretlemeniz gerekir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter> sınıfı ve iç içe geçmiş ilke ifadeleri ve ilke framework öznitelikleri doğru ad alanında belirtilen ilke sürümlerine göre dışarı aktarma.  
  
 Özel ilke onaylamalarını içe aktarmak için bkz: <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> ve [nasıl yapılır: özel ilke onaylamalarını içe](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Özel ilke onaylamalarını dışa aktarmak için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Aşağıdaki kod örneğinde bir özel ilke onaylama bağlama düzeyinde uyarlamasını gösterir.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Bağlama öğesi ya da program aracılığıyla bağlama veya uygulama yapılandırma dosyası kullanarak uç nokta yerleştirin. Aşağıdaki yordamlara bakın.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için  
  
1.  Uygulama <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> özel ilke onaylama bağlama öğesi için.  
  
2.  Bağlama öğesi uzantısı yapılandırma dosyasını kullanarak eklemek [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) öğesi.  
  
3.  Özel bağlama kullanma yapı <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Program aracılığıyla bir bağlama öğesi eklemek için  
  
1.  Yeni bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ekleyebilmek için bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Özel bağlama adım 1'den ekleyin. Yeni bir uç noktası için ve bu yeni hizmet uç noktasına ekleyin <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.  
  
3.  Açık <xref:System.ServiceModel.ServiceHost>. Aşağıdaki kod örneğinde, özel bağlama oluşturma ve bağlama öğelerinin programlama ekleme gösterir.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
