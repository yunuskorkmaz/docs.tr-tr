---
title: WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: fa6a2751f8ef3326febc7fa6bed85e10603701c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616062"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma
Windows Communication Foundation (WCF), meta veri dışarı aktarma, hizmet uç noktaları tanımlamak ve bunları istemcilere hizmetin nasıl kullanılacağını anlamak için kullanabileceğiniz bir paralel, standartlaştırılmış gösterimine yansıtma işlemidir. Özel meta verileri, sistem tarafından sağlanan meta verileri vericiler dışarı aktarılamıyor XML öğelerden oluşur. Genellikle, bu kullanıcı tanımlı davranışlar ve bağlama öğeleri ve özellikleri ve bağlamalar ve sözleşmeler gereksinimleriyle ilgili ilke onaylamalarını özel WSDL öğeleri içerir.  
  
 Bu bölümde, özel WSDL veya ilke onaylamalarını dışa aktarma açıklar ve dışarı aktarma işlemi kendisini odaklı değildir. Meta veriler özel ya da sistem oluşturulmuş olmasına bakılmaksızın meta verileri alma ve verme türleri kullanma hakkında daha fazla bilgi için bkz. [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Genel Bakış  
 Meta verileri kullanarak yayımlandığında <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> incelenir ve XSD ve--ilke onaylamalarını dahil olmak üzere--WSDL tüm sözleşmeler ve WCF sistem tarafından sağlanan öznitelikler ve bağlamaları kullanarak destekleyebilir bağlamaları için oluşturulur. Ancak önce düzgün aktarılabilir özel davranışı öznitelikleri veya bağlama öğeleri desteği gerektirir.  
  
 Bu bölümde açıklanmaktadır:  
  
1.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi, WSDL yayımlamadan önce WSDL yeni nesil veriler sizin için kullanıma sunar.  
  
2.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> arabirimi, WSDL verilerindeki ilke onaylamalarını dışa aktarma önce ilke verilerini de sunar.  
  
 Özel WSDL ve ilke onaylamalarını içe aktarma hakkında daha fazla bilgi için bkz. [WCF uzantısı için özel meta alma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Öğeleri özel WSDL dışarı aktarma  
 Uygulama <xref:System.ServiceModel.Description.IWsdlExportExtension> işlemi davranışı, sözleşme davranışı, uç nokta davranışı veya bağlama öğesi (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, veya <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> sırasıyla) ve bağlama öğeleri eklemek ve davranışları Ekle vermeye çalıştığınız hizmetin açıklaması. (Davranışları ekleme hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). <xref:System.ServiceModel.Description.IWsdlExportExtension> Çağrılır için zaten dışarı varsa her uç nokta ve her bir uç nokta sözleşme ilk dışarı aktarır. Gereksinimlerinize bağlı olarak ya da dışarı aktarma işleminde katılabilir:  
  
-   Kullanım <xref:System.ServiceModel.Description.WsdlContractConversionContext> dışarı aktarılan meta verilerde değiştirilecek <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> yöntemi.  
  
-   Kullanım <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> içindeki uç nokta için dışarı aktarılan meta verilerini değiştirmek için <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi.  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> Yöntemi tüm çağrılır <xref:System.ServiceModel.Description.IWsdlExportExtension> uygulamaları içinde <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> dışarı aktarılan örnek.  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> Yöntemi tüm çağrılır <xref:System.ServiceModel.Description.IWsdlExportExtension> uygulamalarıyla <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> dışarı aktarılan örnek.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel WSDL dışarı aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) ve örnek [özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Özel ilke onaylamalarını dışa aktarma  
 Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension> üzerinde bir <xref:System.ServiceModel.Channels.BindingElement> ve bağlama desteği ve sözleşme özellikler ekleyen WSDL bağlama hakkında özel ilke onaylamalarını yazmak için bağlama öğesi ekleyin. <xref:System.ServiceModel.Description.IPolicyExportExtension> Kez uygulanan bağlama öğesi bir bağlamaya verilirken çağrılır ve geçirir <xref:System.ServiceModel.Description.PolicyConversionContext> için <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi. Üzerinde yöntemleri kullanabilirsiniz <xref:System.ServiceModel.Description.PolicyConversionContext> için ilke onaylamalarını eklemek için örnek ileti, işlem veya uç nokta konuları, WSDL bağlama iliştirilmiş.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel ilke onaylamalarını dışa](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Özel WSDL dışarı aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Nasıl yapılır: Özel ilke onaylamalarını dışa](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
