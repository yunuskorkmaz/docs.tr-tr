---
title: WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: c2ae547f10e96a1fdc16fc428e98145fc81c59d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
Windows Communication Foundation (WCF) meta veri dışarı aktarma hizmeti uç noktalarını tanımlayan ve istemcilerin Hizmeti'nin nasıl kullanılacağını anlamak için kullanabileceği bir paralel, standartlaştırılmış gösterimine yansıtma işlemidir. Özel meta verileri, sistem tarafından sağlanan meta verileri vericiler veremiyor XML öğelerden oluşur. Genellikle, bu kullanıcı tarafından tanımlanan davranışları ve bağlama öğeleri ve özellikleri ve bağlamalar ve sözleşmeler gereksinimleriyle ilgili ilke onaylamalarını özel WSDL öğeleri içerir.  
  
 Bu bölümde özel WSDL veya ilke onaylamalarını dışa aktarma açıklar ve dışarı aktarma işlemi kendisini odaklanmak değil. Meta veriler özel ya da sistem oluşturulmuş olmasına bakılmaksızın meta verileri alma ve verme türlerini kullanma hakkında daha fazla bilgi için bkz: [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Genel Bakış  
 Meta verileri kullanarak yayımlandığında <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> incelenir ve XSD ve--ilke onaylamalarını dahil olmak üzere--WSDL tüm sözleşmeler ve WCF sistem tarafından sağlanan özniteliklerini ve bağlamaları kullanarak destekleyebilir bağlamaları için oluşturulur. Ancak, doğru olarak verilebilir önce özel davranışı öznitelikleri veya bağlama öğeleri desteği gerektirir.  
  
 Bu bölümde açıklanmaktadır:  
  
1.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> WSDL yayımlamadan önce WSDL oluşturma verileri, kullanıma sunan arabirim.  
  
2.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ilke onaylamalarını WSDL veri aktarma işleminden önce ilke verilerini size sunar arabirimi.  
  
 Özel WSDL ve ilke onaylamalarını içe aktarma hakkında daha fazla bilgi için bkz: [alma özel meta verileri WCF uzantısı için](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Özel WSDL öğeleri dışarı aktarma  
 Uygulama <xref:System.ServiceModel.Description.IWsdlExportExtension> işlemi davranışı, sözleşme davranışı, uç noktası davranışı veya bağlama öğesi (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, veya <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> sırasıyla) ve davranışları veya bağlama öğeleri içine yerleştirin vermeye çalıştığınız hizmet açıklaması. (Davranışları ekleme hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Çağrılır için bunu değil zaten aktarılmış olan, her bitiş noktasıyla ve her bitiş sözleşme ilk dışa aktarır. Gereksinimlerinize bağlı olarak ya da dışa aktarma işlemine katılabilirler:  
  
-   Kullanım <xref:System.ServiceModel.Description.WsdlContractConversionContext> dışarı aktarılan meta verilerde değiştirmek için <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> yöntemi.  
  
-   Kullanım <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> uç için dışarı aktarılan meta verileri değiştirmeye <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Yöntemi tüm çağrılır <xref:System.ServiceModel.Description.IWsdlExportExtension> içinde uygulamaları <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> dışarı aktarılan örnek.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Yöntemi tüm çağrılır <xref:System.ServiceModel.Description.IWsdlExportExtension> uygulamaları ile <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> dışarı aktarılan örnek.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: özel WSDL dışarı](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) ve örnek [özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Özel ilke onaylamalarını dışa aktarma  
 Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension> üzerinde bir <xref:System.ServiceModel.Channels.BindingElement> ve WSDL desteği ve sözleşme özelliklerini bağlama hakkında özel ilke onaylamalarını yazmak için bağlama bağlama öğesi ekleyin. <xref:System.ServiceModel.Description.IPolicyExportExtension> Bağlama uygulanan bağlama öğesinde dışarı aktarılırken bir kez çağrılır ve geçirir <xref:System.ServiceModel.Description.PolicyConversionContext> için <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi. Yöntemleri kullanabilirsiniz <xref:System.ServiceModel.Description.PolicyConversionContext> iletisi, işlem veya uç nokta konuları adresindeki WSDL bağlama iliştirilmiş ilke onaylamalarını eklemek için örnek.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: özel ilke onaylamalarını dışa](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Özel WSDL Dışarı Aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)  
 [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
