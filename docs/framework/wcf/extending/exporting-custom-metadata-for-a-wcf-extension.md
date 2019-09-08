---
title: WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797187"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
Windows Communication Foundation (WCF) ' de, meta veri dışa aktarma, hizmet uç noktalarını açıklama ve bunları istemcilerin hizmeti nasıl kullanacağınızı anlamak için kullanabileceği paralel ve standartlaştırılmış bir gösterimde yansıtma işlemidir. Özel meta veriler, sistem tarafından belirtilen meta verilerin dışarı aktarıcılar tarafından verilebilme XML öğelerinden oluşur. Genellikle, bu, Kullanıcı tanımlı davranışlar için özel WSDL öğeleri ve bağlamaların ve sözleşmelerin özellikleri ve gereksinimleriyle ilgili öğe ve ilke onayları içerir.  
  
 Bu bölümde, özel WSDL veya ilke onayları dışarı aktarılıyor ve dışarı aktarma işleminin kendisi üzerinde odaklanılamaz. Meta verilerin özel veya sistem tarafından oluşturulmuş olmasından bağımsız olarak dışa ve içeri aktarılan türleri kullanma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](../feature-details/exporting-and-importing-metadata.md)aktarma.  
  
## <a name="overview"></a>Genel Bakış  
 Meta veriler kullanılarak <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> yayımlandığında, İncelenme ve xsd ve WSDL ve WSDL, ilke onayları dahil olmak üzere, WCF 'nin sistem tarafından sunulan öznitelikleri ve bağlamaları kullanarak destekleyebileceği tüm sözleşmeler ve bağlamalar için oluşturulur. Ancak, özel davranış öznitelikleri veya bağlama öğeleri, düzgün şekilde verilebilmeleri için destek gerektirir.  
  
 Bu bölümde şunları açıklar:  
  
1. WSDL 'yi yayımlamadan önce WSDL oluşturma <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> verilerini kullanıma sunan arabirimini uygulama ve kullanma.  
  
2. WSDL verilerinde ilke onayları dışarı aktarmadan <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> önce size ilke verilerini sunan arabirimini uygulama ve kullanma.  
  
 Özel WSDL ve ilke onayları alma hakkında daha fazla bilgi için bkz. [BIR WCF uzantısı Için özel meta verileri Içeri aktarma](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Özel WSDL öğelerini dışa aktarma  
 <xref:System.ServiceModel.Description.IContractBehavior><xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior>İşlem davranışını, anlaşma davranışını, uç nokta davranışını veya bağlama öğesini (,, veya sırasıyla) uygulayın ve <xref:System.ServiceModel.Description.IWsdlExportExtension> dışarı aktarmaya çalıştığınız hizmetin açıklaması. (Davranışlar ekleme hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Her bitiş noktası için çağrılır ve her bitiş noktası henüz dışa aktarılmışsa, sözleşmeyi dışa aktarır. Gereksinimlerinize bağlı olarak, dışarı aktarma işlemine katılabilirsiniz:  
  
- Yöntemi içindeki dışarıya aktarılmış meta verileri değiştirmek içinkullanın.<xref:System.ServiceModel.Description.WsdlContractConversionContext> <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>  
  
- Yöntemi içindeki uç noktanın dışarıya aktarılmış meta verilerini değiştirmek içinöğesinikullanın.<xref:System.ServiceModel.Description.WsdlEndpointConversionContext> <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>  
  
 Yöntemi, aktarılmakta olan <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> örnek içindeki <xref:System.ServiceModel.Description.IWsdlExportExtension> tüm uygulamalarda çağrılır. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>  Yöntemi, verilen <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> örneğe sahip tüm <xref:System.ServiceModel.Description.IWsdlExportExtension> uygulamalarda çağrılır. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A>  
  
 Daha fazla bilgi için [nasıl yapılır: Özel wsdl](how-to-export-custom-wsdl.md) ve örnek [özel wsdl yayınını](../samples/custom-wsdl-publication.md)dışarı aktarın.  
  
## <a name="exporting-custom-policy-assertions"></a>Özel Ilke onaylamalarını dışa aktarma  
 <xref:System.ServiceModel.Description.IPolicyExportExtension> ' A<xref:System.ServiceModel.Channels.BindingElement> uygulayın ve WSDL 'ye bağlama desteği ve sözleşme özellikleri hakkında özel ilke onayları yazmak için bağlamaya bağlama öğesini ekleyin. , <xref:System.ServiceModel.Description.IPolicyExportExtension> Bir bağlamada uygulanan bağlama öğesi dışarı aktarılırken bir kez çağrılır ve <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metodunu yöntemine <xref:System.ServiceModel.Description.PolicyConversionContext> geçirir. İleti, işlem veya uç nokta konularında WSDL bağlamaya eklenen ilke onaylamalarına eklemek için <xref:System.ServiceModel.Description.PolicyConversionContext> örneğindeki yöntemleri kullanabilirsiniz.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel Ilke onaylamalarını](how-to-export-custom-policy-assertions.md)dışarı aktarın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel WSDL 'yi dışarı aktar](how-to-export-custom-wsdl.md)
- [Nasıl yapılır: Özel Ilke onaylamalarını dışarı aktar](how-to-export-custom-policy-assertions.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](importing-custom-metadata-for-a-wcf-extension.md)
