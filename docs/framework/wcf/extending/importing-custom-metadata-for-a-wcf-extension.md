---
title: WCF Uzantısı için Özel Meta Verileri İçe Aktarma
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: b231ff676ffc81666713987a24605b8ae98bb6d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254629"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF Uzantısı için Özel Meta Verileri İçe Aktarma

Windows Communication Foundation (WCF) ' de, meta veri içeri aktarma işlemi, bir hizmetin soyut temsilini veya meta verilerinden bir bileşen parçalarını oluşturma işlemidir. Örneğin, WCF <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Channels.Binding> <xref:System.ServiceModel.Description.ContractDescription> bir HIZMET için bir wsdl belgesinden örnekleri, örnekleri veya örnekleri içeri aktarabilir. WCF 'de hizmet meta verilerini içeri aktarmak için soyut sınıfın bir uygulamasını kullanın <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> . Sınıfından türetilen türler <xref:System.ServiceModel.Description.MetadataImporter> , WCF 'deki WS-Policy içeri aktarma mantığının avantajlarından yararlanan meta veri biçimleri içeri aktarma desteği uygular.  
  
 Özel meta veriler, sistem tarafından belirtilen meta veri içe aktarıcılar tarafından içeri aktarılamıyor XML öğelerinden oluşur. Genellikle buna özel WSDL uzantıları ve özel ilke onayları dahildir.  
  
 Bu bölümde, özel WSDL uzantıları ve ilke onaylamaları 'nın nasıl içeri aktarılacağı açıklanmaktadır. İçeri aktarma işlemine odaklanmaz. Meta verilerin özel veya sistem tarafından desteklenmesinden bağımsız olarak dışa ve içeri aktarılan türleri kullanma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](../feature-details/exporting-and-importing-metadata.md)aktarma.  
  
## <a name="overview"></a>Genel Bakış  

 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Tür, <xref:System.ServiceModel.Description.MetadataImporter> WCF 'ye dahil edilen soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlImporter>Türü, wsdl meta verilerini bir nesnede paketlenmiş ekli ilkelerle içe aktarır <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> . Varsayılan içeri aktarıcılar tanımayan ilke onayları ve WSDL uzantıları, içeri aktarmaya yönelik kayıtlı özel ilkeye ve WSDL ımporallara geçirilir. Genellikle Importers, Kullanıcı tanımlı bağlama öğelerini desteklemek veya içeri aktarılan sözleşmeyi değiştirmek için uygulanır.  
  
 Bu bölümde şunları açıklar:  
  
1. <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>Açıklamaları oluşturma ve kod oluşturma öncesinde özel içeri aktarıcılar IÇIN WSDL verilerini kullanıma sunan arabirimini uygulama ve kullanma. Bu arabirimi, belirli bir meta veri kümesi kullanılarak gerçekleştirilen açıklama türlerini ve kod derlemesini incelemek veya değiştirmek için kullanabilirsiniz.  
  
2. <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>Açıklama nesnelerinden oluşturmadan önce içeri aktarıcılar için ilke onayları sunan arabirimini uygulama ve kullanma. Bu arabirimi, indirilen ilkelere göre bağlamayı veya sözleşmeyi incelemek veya değiştirmek için kullanabilirsiniz.  
  
 Özel WSDL ve ilke onayları dışarı aktarma hakkında daha fazla bilgi için bkz. [BIR WCF uzantısı Için özel meta verileri dışarı aktarma](exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Özel WSDL uzantılarını içeri aktarma  

 WSDL uzantılarını içeri aktarma desteği eklemek için, arabirimini uygulayın <xref:System.ServiceModel.Description.IWsdlImportExtension> ve ardından uygulamanıza ekleyin <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> . , <xref:System.ServiceModel.Description.WsdlImporter> <xref:System.ServiceModel.Description.IWsdlImportExtension> Uygulama yapılandırma dosyanıza kayıtlı arabirimin uygulamalarını da yükleyebilir. Bir dizi WSDL Importers kaydı varsayılan olarak kaydedilir ve kayıtlı WSDL Importers sırası önemli olur.  
  
 Özel WSDL İçeri Aktarıcı tarafından yüklenip kullanıldığında, <xref:System.ServiceModel.Description.WsdlImporter> ilk olarak <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> yöntemi içeri aktarma işleminden önce meta verilerin değiştirilmesini etkinleştirmek için çağırılır. Ardından, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> meta verilerden içeri aktarılan sözleşmelerin değiştirilmesini sağlamak için yöntemi çağrılmadan sonra anlaşmalar içeri aktarılır. Son olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> içeri aktarılan uç noktaların değiştirilmesini etkinleştirmek için yöntemi çağırılır.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: özel wsdl alma](how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Özel Ilke onaylamalarını içeri aktarma  

 <xref:System.ServiceModel.Description.WsdlImporter>Tür ve [ServiceModel meta veri yardımcı programı aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , WSDL belgelerine eklenen ilke ifadelerinde çeşitli ilke onaylama türlerini otomatik olarak işler. Bu araçlar, WSDL bağlamaları ve WSDL bağlantı noktalarına eklenen ilke ifadelerini toplar, normalleştirin ve birleştirir.  
  
 Özel ilke onayları alma desteği eklemek için, <xref:System.ServiceModel.Description.IPolicyImportExtension> arabirimini uygulayın ve ardından uygulamanıza ekleyin <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> . , <xref:System.ServiceModel.Description.MetadataImporter> <xref:System.ServiceModel.Description.IPolicyImportExtension> Uygulama yapılandırma dosyanıza kayıtlı arabirimin uygulamalarını da yükleyebilir. Bir dizi ilke içe aktarıcılar varsayılan olarak kaydedilir ve kayıtlı ilke içe aktarıcılar önemli olur.  
  
 Meta veri sistemi, <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> ileti, işlem ve uç nokta ilkesi ilgililere eklenen her ilke alternatifindeki her bir bileşim için tüm kayıtlı ilke içeri aktarma uzantılarında yöntemi sürekli olarak çağırır. Bir WSDL bağlantı noktası içeri aktarılırken, ilke içeri aktarma uzantılarına çağrılmadan önce, bağlantı noktasına ve ilgili WSDL bağlamasına bağlı ilkeler birleştirilir. İlke alternatifleri bir as nesneleri aracılığıyla kullanılabilir hale <xref:System.ServiceModel.Description.PolicyConversionContext> getirilir <xref:System.ServiceModel.Description.PolicyAssertionCollection> . <xref:System.ServiceModel.Description.PolicyAssertionCollection>, Nesneleri tarafından temsil edilen ilke onayları koleksiyonudur <xref:System.Xml.XmlElement> .  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A>Nesnesindeki ve <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> ÖZELLIKLERI, <xref:System.ServiceModel.Description.PolicyConversionContext> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.BindingElement> WSDL 'den içeri aktarılan ve nesnelerini kullanıma sunar. İlke içeri aktarma uzantıları, belirli bir ilke onaylama türünün örneklerini bularak, veya nesnelerinde ilgili değişiklikleri yaparak <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.BindingElement> ve ardından ilgili örnekten ilke onayları kaldırarak ilke onaylamalarını işler <xref:System.ServiceModel.Description.PolicyAssertionCollection> .  
  
 `wsp:Optional`Öznitelik ve iç içe geçmiş ilke ifadeleri normalleştirilmez, bu nedenle ilke içeri aktarma uzantıları bu ilke yapılarını işlemelidir. Ayrıca, ilke içeri aktarma uzantıları aynı ve nesneleriyle birden çok kez çağrılabilir <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.BindingElement> , bu nedenle ilke içeri aktarma uzantıları bu davranışa sağlam olmalıdır.  
  
> [!IMPORTANT]
> İçeri aktarıcıya geçersiz ya da yanlış metaveri geçirilebilir. Özel içeri aktarıcılar tüm XML formlarına sağlam olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Özel WSDL İçeri Aktarma](how-to-import-custom-wsdl.md)
- [Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma](how-to-import-custom-policy-assertions.md)
- [Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma](how-to-write-an-extension-for-the-servicecontractgenerator.md)
