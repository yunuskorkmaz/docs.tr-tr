---
title: WCF Uzantısı için Özel Meta Verileri İçe Aktarma
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 830829be98202c97a9fc2b34e31da25967292efb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766772"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri İçe Aktarma
Windows Communication Foundation (WCF) meta verileri alma, meta verilerinden bir hizmet veya bileşen parçalarından soyut bir temsilini oluşturma işlemidir. Örneğin, WCF aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri <xref:System.ServiceModel.Channels.Binding> örnekleri veya <xref:System.ServiceModel.Description.ContractDescription> bir WSDL örneklerden belge için bir hizmet. WCF hizmet meta verileri içeri aktarmak için uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> soyut sınıf. Öğesinden türetilen türler <xref:System.ServiceModel.Description.MetadataImporter> WS-Policy yararlanan alma meta veri biçimleri WCF mantığı içeri aktarmak için sınıf uygulama desteği.  
  
 Özel meta verileri, sistem tarafından sağlanan meta verileri ımporters içeri aktarılamıyor XML öğelerden oluşur. Genellikle, bu özel WSDL uzantı ve özel ilke onaylamalarını içerir.  
  
 Bu bölüm, özel WSDL uzantı ve ilke onaylamalarını içe aktarmayı açıklar. İçeri aktarma işlemi kendisini odaklı değildir. Meta veriler özel ya da sistem tarafından desteklenen olmasına bakılmaksızın meta verileri alma ve verme türleri kullanma hakkında daha fazla bilgi için bkz. [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Genel Bakış  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türüdür yürütmesinin <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf ile WCF dahil. <xref:System.ServiceModel.Description.WsdlImporter> Türü içinde paketlenir ekli ilkeleriyle WSDL meta verileri alır bir <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> nesne. İlke onaylamalarını ve varsayılan ımporters tarafından tanınmayan bir WSDL uzantıları herhangi bir kayıtlı özel ilkeyi ve WSDL ımporters almak için geçirilir. Genellikle, ımporters içeri aktarılan sözleşme değiştirmek için ya da kullanıcı tanımlı bağlama öğeleri desteklemek için uygulanır.  
  
 Bu bölümde açıklanmaktadır:  
  
1. Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi, özel ımporters açıklamalarını oluşturma ve kod oluşturulmasını önce WSDL verileri gösterir. Bu arabirim incelemek veya belirli bir meta veri kümesi kullanılarak gerçekleştirilen kod derleme ve açıklama türünü değiştirmek için kullanabilirsiniz.  
  
2. Uygulamak ve kullanmak nasıl <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> açıklama nesneleri nesil önce ımporters için ilke onaylamalarını sunan arabirimi. Bu arabirim incelemek veya bağlama veya sözleşme indirilen ilkelerine bağlı olarak değiştirmek için kullanabilirsiniz.  
  
 Özel WSDL ve ilke onaylamalarını dışa aktarma hakkında daha fazla bilgi için bkz. [WCF uzantısı için özel meta verme](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Özel WSDL içe aktarma uzantıları  
 WSDL uzantıları almak için destek eklemek üzere uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirim ve uygulamanız için eklersiniz <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> özelliği. <xref:System.ServiceModel.Description.WsdlImporter> Uygulamaları da yükleyebilirsiniz <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi, uygulama yapılandırma dosyasında kayıtlı. WSDL ımporters bir dizi varsayılan olarak kaydedilir ve kaydedilen WSDL ımporters sırası önemlidir unutmayın.  
  
 Özel WSDL içeri Aktarıcı olduğunda yüklendi ve tarafından kullanılan <xref:System.ServiceModel.Description.WsdlImporter>, ilk <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> yöntemi meta verileri içeri aktarma işlemi öncesinde değiştirilmesini etkinleştirmek için çağrılır. Ardından, anlaşmalar sonra alındığı <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> yöntemi meta verilerden içe aktarıldı sözleşmeleri değiştirilmesini etkinleştirmek için çağrılır. Son olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> yöntemi, içeri aktarılan uç noktaları değiştirilmesini etkinleştirmek için çağrılır.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel WSDL içe](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Özel ilke onaylamalarını içe aktarma  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü ve [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ilke onaylama türleri WSDL belgeleri iliştirilmiş ilke ifadelerde çeşitli işlem otomatik olarak işler. Bu araçlar toplamak, Normalleştir ve WSDL bağlamaları ve WSDL bağlantı noktalarına bağlı ilke ifadelerini birleştirme.  
  
 Özel ilke onaylamalarını içe aktarma için destek eklemek üzere uygulama <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirim ve uygulamanız için eklersiniz <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> özelliği. <xref:System.ServiceModel.Description.MetadataImporter> Uygulamaları da yükleyebilirsiniz <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimi, uygulama yapılandırma dosyasında kayıtlı. Varsayılan olarak bir dizi ilke ımporters kaydedilir ve kayıtlı ilke ımporters sırası önemlidir unutmayın.  
  
 Meta veri sistemini tekrar tekrar çağırır <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> yöntemi tüm kayıtlı ilke içeri her ileti, işlem ve uç noktası İlkesi konuları iliştirilmiş ilke alternatifleri birleşimi için Uzantılar. Bir WSDL bağlantı noktası içeri aktarırken, bağlantı noktasına ve karşılık gelen WSDL bağlama bağlı ilkeler ilke içeri aktarma uzantıları içine çağırmadan önce birleştirilir. İlke alternatifleri kullanılabilir hale getirilir bir <xref:System.ServiceModel.Description.PolicyConversionContext> olarak <xref:System.ServiceModel.Description.PolicyAssertionCollection> nesneleri. Her <xref:System.ServiceModel.Description.PolicyAssertionCollection> tarafından temsil edilen ilke onaylamalarını koleksiyonudur <xref:System.Xml.XmlElement> nesneleri.  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> Ve <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> özellikleri <xref:System.ServiceModel.Description.PolicyConversionContext> sunmaya nesne <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.BindingElement> WSDL'den aktarılan nesneleri. İlke içeri aktarma uzantıları için karşılık gelen değişiklik yapmadan bir belirli ilke onaylama işlemi türü örneklerini bularak ilke onaylamalarını işlem <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Channels.BindingElement> nesneleri ve ardından karşılık gelen ilkeonaylamalarınıkaldırma<xref:System.ServiceModel.Description.PolicyAssertionCollection> örneği.  
  
 `wsp:Optional` Özniteliği ve iç içe geçmiş ilke ifadeleri Normalleştirilmemiş, bu ilke yapılarına ilke içeri aktarma uzantıları işlemesi için. Ayrıca, ilke içeri aktarma uzantıları birden çok kez aynı çağrılabilir <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.BindingElement> ilke içeri aktarma uzantıları için bu davranışı sağlam bu nedenle, nesneler.  
  
> [!IMPORTANT]
>  Geçersiz ya da yanlış meta veri alma için geçirilebilir. Özel ımporters için tüm form XML sağlam olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel WSDL içeri aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Nasıl yapılır: Özel ilke onaylamalarını içe aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Nasıl yapılır: ServiceContractGenerator için uzantı yazma](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
