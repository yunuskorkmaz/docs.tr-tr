---
description: 'Hakkında daha fazla bilgi edinin: bir WCF uzantısı için özel meta verileri dışarı aktarma'
title: WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 5803dd7d2e03f9597ecac34bf38641656a9077b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685796"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma

Windows Communication Foundation (WCF) ' de, meta veri dışa aktarma, hizmet uç noktalarını açıklama ve bunları istemcilerin hizmeti nasıl kullanacağınızı anlamak için kullanabileceği paralel ve standartlaştırılmış bir gösterimde yansıtma işlemidir. Özel meta veriler, sistem tarafından belirtilen meta verilerin dışarı aktarıcılar tarafından verilebilme XML öğelerinden oluşur. Genellikle, bu, Kullanıcı tanımlı davranışlar için özel WSDL öğeleri ve bağlamaların ve sözleşmelerin özellikleri ve gereksinimleriyle ilgili öğe ve ilke onayları içerir.  
  
 Bu bölümde, özel WSDL veya ilke onayları dışarı aktarılıyor ve dışarı aktarma işleminin kendisi üzerinde odaklanılamaz. Meta verilerin özel veya sistem tarafından oluşturulmuş olmasından bağımsız olarak dışa ve içeri aktarılan türleri kullanma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](../feature-details/exporting-and-importing-metadata.md)aktarma.  
  
## <a name="overview"></a>Genel Bakış  

 Meta veriler kullanılarak yayımlandığında, <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> INCELENME ve xsd ve WSDL ve WSDL, ilke onayları dahil olmak üzere, WCF 'nin sistem tarafından sunulan öznitelikleri ve bağlamaları kullanarak destekleyebileceği tüm sözleşmeler ve bağlamalar için oluşturulur. Ancak, özel davranış öznitelikleri veya bağlama öğeleri, düzgün şekilde verilebilmeleri için destek gerektirir.  
  
 Bu bölümde şunları açıklar:  
  
1. <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>WSDL 'yi yayımlamadan önce WSDL oluşturma verilerini kullanıma sunan arabirimini uygulama ve kullanma.  
  
2. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>WSDL verilerinde ilke onayları dışarı aktarmadan önce size ilke verilerini sunan arabirimini uygulama ve kullanma.  
  
 Özel WSDL ve ilke onayları alma hakkında daha fazla bilgi için bkz. [BIR WCF uzantısı Için özel meta verileri Içeri aktarma](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Özel WSDL öğelerini dışa aktarma  

 <xref:System.ServiceModel.Description.IWsdlExportExtension>İşlem davranışını, anlaşma davranışını, uç nokta davranışını veya bağlama öğesini ( <xref:System.ServiceModel.Description.IOperationBehavior> , <xref:System.ServiceModel.Description.IContractBehavior> , <xref:System.ServiceModel.Description.IEndpointBehavior> , veya <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> sırasıyla) uygulayın ve davranışları veya bağlama öğelerini dışarı aktarmaya çalıştığınız hizmetin açıklamasına ekleyin. (Davranışlar ekleme hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension>Her bitiş noktası için çağrılır ve her bitiş noktası henüz dışa aktarılmışsa, sözleşmeyi dışa aktarır. Gereksinimlerinize bağlı olarak, dışarı aktarma işlemine katılabilirsiniz:  
  
- <xref:System.ServiceModel.Description.WsdlContractConversionContext>Yöntemi içindeki dışarıya aktarılmış meta verileri değiştirmek için kullanın <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> .  
  
- <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>Yöntemi içindeki uç noktanın dışarıya aktarılmış meta verilerini değiştirmek için öğesini kullanın <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> .  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>Yöntemi, <xref:System.ServiceModel.Description.IWsdlExportExtension> aktarılmakta olan örnek içindeki tüm uygulamalarda çağrılır <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> .  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>Yöntemi, <xref:System.ServiceModel.Description.IWsdlExportExtension> verilen örneğe sahip tüm uygulamalarda çağrılır <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> .  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: özel wsdl dışarı aktarma](how-to-export-custom-wsdl.md) ve örnek [özel wsdl yayımı](../samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Özel Ilke onaylamalarını dışa aktarma  

 <xref:System.ServiceModel.Description.IPolicyExportExtension>' A uygulayın <xref:System.ServiceModel.Channels.BindingElement> ve WSDL 'ye bağlama desteği ve sözleşme özellikleri hakkında özel ilke onayları yazmak için bağlamaya bağlama öğesini ekleyin. , <xref:System.ServiceModel.Description.IPolicyExportExtension> Bir bağlamada uygulanan bağlama öğesi dışarı aktarılırken bir kez çağrılır ve <xref:System.ServiceModel.Description.PolicyConversionContext> <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metodunu yöntemine geçirir. <xref:System.ServiceModel.Description.PolicyConversionContext>İleti, işlem veya uç nokta konularında WSDL bağlamaya eklenen ilke onaylamalarına eklemek için örneğindeki yöntemleri kullanabilirsiniz.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: özel Ilke onaylamalarını dışarı aktarma](how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel WSDL Dışarı Aktarma](how-to-export-custom-wsdl.md)
- [Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma](how-to-export-custom-policy-assertions.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](importing-custom-metadata-for-a-wcf-extension.md)
