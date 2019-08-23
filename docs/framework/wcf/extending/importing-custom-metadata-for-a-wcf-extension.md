---
title: WCF Uzantısı için Özel Meta Verileri İçe Aktarma
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 36bc4c9291b60ae5ad6e9964c361ed9e7a7c8317
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963492"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri İçe Aktarma
Windows Communication Foundation (WCF) ' de, meta veri içeri aktarma işlemi, bir hizmetin soyut temsilini veya meta verilerinden bir bileşen parçalarını oluşturma işlemidir. Örneğin, WCF bir hizmet için <xref:System.ServiceModel.Description.ServiceEndpoint> bir wsdl <xref:System.ServiceModel.Channels.Binding> belgesinden örnekleri <xref:System.ServiceModel.Description.ContractDescription> , örnekleri veya örnekleri içeri aktarabilir. WCF 'de hizmet meta verilerini içeri aktarmak için <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> soyut sınıfın bir uygulamasını kullanın. <xref:System.ServiceModel.Description.MetadataImporter> Sınıfından türetilen türler, WCF 'deki WS-Policy Import mantığının avantajlarından yararlanan meta veri biçimlerini içeri aktarmaya yönelik destek uygular.  
  
 Özel meta veriler, sistem tarafından belirtilen meta veri içe aktarıcılar tarafından içeri aktarılamıyor XML öğelerinden oluşur. Genellikle buna özel WSDL uzantıları ve özel ilke onayları dahildir.  
  
 Bu bölümde, özel WSDL uzantıları ve ilke onaylamaları 'nın nasıl içeri aktarılacağı açıklanmaktadır. İçeri aktarma işlemine odaklanmaz. Meta verilerin özel veya sistem tarafından desteklenmesinden bağımsız olarak dışa ve içeri aktarılan türleri kullanma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)aktarma.  
  
## <a name="overview"></a>Genel Bakış  
 Tür, WCF 'ye dahil edilen <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü <xref:System.ServiceModel.Description.WsdlImporter> , wsdl meta verilerini bir <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> nesnede paketlenmiş ekli ilkelerle içe aktarır. Varsayılan içeri aktarıcılar tanımayan ilke onayları ve WSDL uzantıları, içeri aktarmaya yönelik kayıtlı özel ilkeye ve WSDL ımporallara geçirilir. Genellikle Importers, Kullanıcı tanımlı bağlama öğelerini desteklemek veya içeri aktarılan sözleşmeyi değiştirmek için uygulanır.  
  
 Bu bölümde şunları açıklar:  
  
1. Açıklamaları oluşturma ve kod oluşturma öncesinde <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> özel içeri aktarıcılar için WSDL verilerini kullanıma sunan arabirimini uygulama ve kullanma. Bu arabirimi, belirli bir meta veri kümesi kullanılarak gerçekleştirilen açıklama türlerini ve kod derlemesini incelemek veya değiştirmek için kullanabilirsiniz.  
  
2. Açıklama nesnelerinden oluşturmadan önce içeri aktarıcılar için ilke onayları sunan <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> arabirimini uygulama ve kullanma. Bu arabirimi, indirilen ilkelere göre bağlamayı veya sözleşmeyi incelemek veya değiştirmek için kullanabilirsiniz.  
  
 Özel WSDL ve ilke onayları dışarı aktarma hakkında daha fazla bilgi için bkz. [BIR WCF uzantısı Için özel meta verileri dışarı aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Özel WSDL uzantılarını içeri aktarma  
 WSDL uzantılarını içeri aktarma desteği eklemek için, <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimini uygulayın ve ardından uygulamanıza <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> ekleyin. , <xref:System.ServiceModel.Description.WsdlImporter> Uygulama yapılandırma dosyanıza kayıtlı <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimin uygulamalarını da yükleyebilir. Bir dizi WSDL Importers kaydı varsayılan olarak kaydedilir ve kayıtlı WSDL Importers sırası önemli olur.  
  
 Özel wsdl İçeri Aktarıcı tarafından <xref:System.ServiceModel.Description.WsdlImporter>yüklenip kullanıldığında, <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> ilk olarak yöntemi içeri aktarma işleminden önce meta verilerin değiştirilmesini etkinleştirmek için çağırılır. Ardından, meta verilerden içeri aktarılan sözleşmelerin değiştirilmesini sağlamak <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> için yöntemi çağrılmadan sonra anlaşmalar içeri aktarılır. Son olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> içeri aktarılan uç noktaların değiştirilmesini etkinleştirmek için yöntemi çağırılır.  
  
 Daha fazla bilgi için [nasıl yapılır: Özel WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)'yi içeri aktar.  
  
### <a name="importing-custom-policy-assertions"></a>Özel Ilke onaylamalarını içeri aktarma  
 Type <xref:System.ServiceModel.Description.WsdlImporter> ve [ServiceModel Metadata Utility aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , WSDL belgelerine eklenen ilke ifadelerinde çeşitli ilke onaylama türlerini otomatik olarak işler. Bu araçlar, WSDL bağlamaları ve WSDL bağlantı noktalarına eklenen ilke ifadelerini toplar, normalleştirin ve birleştirir.  
  
 Özel ilke onayları alma desteği eklemek için, <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimini uygulayın ve ardından uygulamanıza <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> ekleyin. , <xref:System.ServiceModel.Description.MetadataImporter> Uygulama yapılandırma dosyanıza kayıtlı <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimin uygulamalarını da yükleyebilir. Bir dizi ilke içe aktarıcılar varsayılan olarak kaydedilir ve kayıtlı ilke içe aktarıcılar önemli olur.  
  
 Meta veri sistemi, ileti, <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> işlem ve uç nokta ilkesi ilgililere eklenen her ilke alternatifindeki her bir bileşim için tüm kayıtlı ilke içeri aktarma uzantılarında yöntemi sürekli olarak çağırır. Bir WSDL bağlantı noktası içeri aktarılırken, ilke içeri aktarma uzantılarına çağrılmadan önce, bağlantı noktasına ve ilgili WSDL bağlamasına bağlı ilkeler birleştirilir. İlke alternatifleri bir <xref:System.ServiceModel.Description.PolicyConversionContext> as <xref:System.ServiceModel.Description.PolicyAssertionCollection> nesneleri aracılığıyla kullanılabilir hale getirilir. , Nesneleri tarafından <xref:System.Xml.XmlElement> temsil edilen ilke onayları koleksiyonudur. <xref:System.ServiceModel.Description.PolicyAssertionCollection>  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> <xref:System.ServiceModel.Description.ContractDescription> Nesnesindeki ve <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> özellikleri <xref:System.ServiceModel.Channels.BindingElement> , WSDL 'den içeri aktarılan ve nesnelerini kullanıma sunar. <xref:System.ServiceModel.Description.PolicyConversionContext> İlke içeri aktarma uzantıları, belirli bir ilke onaylama türünün örneklerini bularak, <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Channels.BindingElement> nesnelerinde ilgili değişiklikleri yaparak ve ardından ilke onaylamalarını karşılık gelen <xref:System.ServiceModel.Description.PolicyAssertionCollection> örnek.  
  
 `wsp:Optional` Öznitelik ve iç içe geçmiş ilke ifadeleri normalleştirilmez, bu nedenle ilke içeri aktarma uzantıları bu ilke yapılarını işlemelidir. Ayrıca, ilke içeri aktarma uzantıları aynı <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.BindingElement> nesneleriyle birden çok kez çağrılabilir, bu nedenle ilke içeri aktarma uzantıları bu davranışa sağlam olmalıdır.  
  
> [!IMPORTANT]
> İçeri aktarıcıya geçersiz ya da yanlış metaveri geçirilebilir. Özel içeri aktarıcılar tüm XML formlarına sağlam olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel WSDL 'yi içeri aktar](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Nasıl yapılır: Özel Ilke onaylamalarını içeri aktar](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Nasıl yapılır: ServiceContractGenerator için bir uzantı yazma](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
