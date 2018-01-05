---
title: "WCF Uzantısı için Özel Meta Verileri İçe Aktarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9208a73f6a35e4c05ab9be612491f3f7db792a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri İçe Aktarma
İçinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], meta verileri alma, sistemi, hizmet ya da bileşen parçalarından soyut bir temsili kendi meta verilerini oluşturma işlemidir. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri <xref:System.ServiceModel.Channels.Binding> örnekleri veya <xref:System.ServiceModel.Description.ContractDescription> WSDL örneklerden belge için bir hizmet. Hizmet meta verilerde almak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> soyut sınıf. Öğesinden türetilen türler <xref:System.ServiceModel.Description.MetadataImporter> sınıf WS-Policy yararlanmak alma meta veri biçimleri mantığı almak için destek uygulama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Özel meta verileri, sistem tarafından sağlanan meta verileri ımporters alamıyor XML öğelerden oluşur. Genellikle, bu özel WSDL uzantıları ve özel ilke onaylamalarını içerir.  
  
 Bu bölüm, özel WSDL uzantıları ve ilke onaylamalarını içe aktarmayı açıklar. İçeri aktarma işlemi kendisini odak değil. Meta veriler özel ya da sistem desteklenen olmasına bakılmaksızın meta verileri alma ve verme türlerini kullanma hakkında daha fazla bilgi için bkz: [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Genel Bakış  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü uygulamasıdır <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf ile birlikte gelen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Türü içinde paketlendi ekli ilkeleriyle WSDL meta verileri içe aktaran bir <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> nesnesi. İlke onaylamalarını ve varsayılan ımporters tanımadığınız WSDL uzantıları herhangi bir kayıtlı özel ilkeyi ve WSDL ımporters içeri aktarmak için geçirilir. Genellikle, ımporters alınan sözleşme değiştirmek için ya da kullanıcı tanımlı bağlama öğeleri desteklemek için uygulanır.  
  
 Bu bölümde açıklanmaktadır:  
  
1.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> özel ımporters açıklamaları oluşturulmasını ve kod oluşturma önce WSDL veri sunan arabirim. Bu arabirim inceleyin veya açıklama türleri ve meta verileri belirli bir dizi kullanılarak gerçekleştirilen kod derleme değiştirmek için kullanabilirsiniz.  
  
2.  Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> açıklama nesneleri nesil önce ımporters için ilke onaylamalarını kullanıma sunan arabirim. Bu arabirim inceleyin veya bağlama veya sözleşme indirilen ilkelerine bağlı olarak değiştirmek için kullanabilirsiniz.  
  
 Özel WSDL ve ilke onaylamalarını dışa aktarma hakkında daha fazla bilgi için bkz: [dışarı aktarma özel meta verileri WCF uzantısı için](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Özel WSDL uzantılar içeri aktarma  
 WSDL uzantıları alma desteği eklemek için uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirim ve uygulamanız için ekleme <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> özelliği. <xref:System.ServiceModel.Description.WsdlImporter> Ayrıca uygulamaları yükleyebilir ve <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirim uygulama yapılandırma dosyasında kayıtlı. WSDL ımporters bir dizi varsayılan olarak kaydedilir ve kayıtlı WSDL ımporters sırasını önemli olduğunu unutmayın.  
  
 Ne zaman özel WSDL içeri Aktarıcı yüklenen ve tarafından kullanılan <xref:System.ServiceModel.Description.WsdlImporter>, ilk <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> yöntemi meta veri alma işlemi önce değiştirilmesini etkinleştirmek için çağrılır. Ardından, sözleşmeler sonra alındığı <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> yöntemi meta verilerini içe sözleşmeleri değiştirilmesini etkinleştirmek için çağrılır. Son olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> yöntemi, içeri aktarılan uç noktaları değiştirilmesini etkinleştirmek için çağrılır.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: özel WSDL içe aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Özel ilke onaylamalarını içe aktarma  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü ve [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ilke onaylama türleri WSDL belgelere iliştirilmiş ilke ifadelerdeki çeşitli işleme otomatik olarak işler. Bu araçları toplamak, normalleştirin ve WSDL bağlamalar ve WSDL bağlantı noktaları bağlı ilke ifadelerini birleştirme.  
  
 Özel ilke onaylamalarını içe aktarmak için destek eklemek için uygulama <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirim ve uygulamanız için ekleme <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> özelliği. <xref:System.ServiceModel.Description.MetadataImporter> Ayrıca uygulamaları yükleyebilir ve <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirim uygulama yapılandırma dosyasında kayıtlı. İlke ımporters bir dizi varsayılan olarak kaydedilir ve kayıtlı ilke ımporters sırası önemlidir unutmayın.  
  
 Meta veri sistemi art arda çağırır <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> içeri aktarma yöntemini tüm kayıtlı ilkedeki her ileti, işlem ve uç nokta İlkesi konuları iliştirilmiş ilke alternatifleri birleşimi için Uzantılar. WSDL bağlantı noktası içe aktarırken, bağlantı noktası ve karşılık gelen WSDL bağlama bağlı ilkeleri ilkesi alma uzantıları içine çağırmadan önce birleştirilir. İlke alternatifleri kullanılabilir hale getirilir bir <xref:System.ServiceModel.Description.PolicyConversionContext> olarak <xref:System.ServiceModel.Description.PolicyAssertionCollection> nesneleri. Her <xref:System.ServiceModel.Description.PolicyAssertionCollection> tarafından temsil edilen ilke onaylamalarını koleksiyonudur <xref:System.Xml.XmlElement> nesneleri.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> Ve <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> özellikleri <xref:System.ServiceModel.Description.PolicyConversionContext> sunmaya nesne <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.BindingElement> WSDL içe aktarılan nesneler. İlke içeri aktarma uzantılar ilke onaylamalarını karşılık gelen değişiklik belirli bir ilkenin onaylama türünün örneklerini bularak <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Channels.BindingElement> nesneleri ve ardından karşılık gelen ilkeonaylamalarınıkaldırma<xref:System.ServiceModel.Description.PolicyAssertionCollection> örneği.  
  
 `wsp:Optional` Özniteliği ve iç içe geçmiş ilke ifadelerini Normalleştirilmemiş, bu ilke yapılarına ilkesi alma uzantıları işlemelidir şekilde. Ayrıca, ilke alma uzantıları birden çok kez aynı çağrılabilir <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.BindingElement> nesneleri nedenle ilkesi alma uzantıları için bu davranış sağlam olmalıdır.  
  
> [!IMPORTANT]
>  Geçersiz veya hatalı meta verileri alma geçirilebilir. Özel ımporters XML tüm formlara sağlam olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Özel WSDL İçe Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)  
 [Nasıl yapılır: Özel İlke Onaylamalarını İçe Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)  
 [Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
