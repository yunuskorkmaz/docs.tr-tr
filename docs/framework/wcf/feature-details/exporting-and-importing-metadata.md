---
title: Meta Verileri Dışarı ve İçeri Aktarma
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 692382de81459ad52d306ca7fd05546b4e36294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963659"
---
# <a name="exporting-and-importing-metadata"></a>Meta Verileri Dışarı ve İçeri Aktarma
Windows Communication Foundation (WCF) ' de, meta verileri dışarı aktarma işlemi, hizmet uç noktalarını açıklama ve bunları istemcilerin hizmeti nasıl kullanacağınızı anlamak için kullanabileceği paralel ve standartlaştırılmış bir gösterimde yansıtma işlemidir. Hizmet meta verilerinin içeri aktarılması, hizmet meta <xref:System.ServiceModel.Description.ServiceEndpoint> verilerinden örnek veya parçalar oluşturma işlemidir.  
  
## <a name="exporting-metadata"></a>Meta veriler dışarı aktarılıyor  
 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> Örneklerden meta verileri dışarı aktarmak için <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıfın bir uygulamasını kullanın. Tür, WCF 'ye dahil edilen <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlExporter>  
  
 Tür <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> , bir <xref:System.ServiceModel.Description.MetadataSet> örnekte kapsüllenmiş ekli ilke ifadelerine sahip Web Hizmetleri Açıklama Dili (wsdl) meta verileri oluşturur. Nesneler ve <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ContractDescription>nesneleriçin meta verileri tekrarlayarak dışarı aktarmak için bir örneği kullanabilirsiniz. <xref:System.ServiceModel.Description.ServiceEndpoint> Ayrıca, bir <xref:System.ServiceModel.Description.ServiceEndpoint> nesne koleksiyonunu dışarı aktarabilir ve bunları belirli bir hizmet adıyla ilişkilendirebilirsiniz.  
  
> [!NOTE]
> `WsdlExporter` Yalnızca, `ContractDescription` `ContractDescription` yöntemi kullanılarak oluşturulan veya`ServiceDescription` bir parçası olarak oluşturulan bir örnek gibi ortak dil çalışma zamanı (CLR) tür bilgilerini içeren örneklerden meta verileri dışarı aktarmak için ' i kullanabilirsiniz. `ContractDescription.GetContract` bir `ServiceHost` örnek için. ' Nı, `WsdlExporter` hizmet meta verilerinden içeri aktarılan `ContractDescription` örneklerden meta verileri dışarı aktarmak için kullanamazsınız veya tür bilgisi olmadan oluşturulabilir.  
  
## <a name="importing-metadata"></a>Meta veriler içeri aktarılıyor  
  
### <a name="importing-wsdl-documents"></a>WSDL belgelerini içeri aktarma  
 WCF 'de hizmet meta verilerini içeri aktarmak için <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıfın bir uygulamasını kullanın. Tür, WCF 'ye dahil edilen <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Tür <xref:System.ServiceModel.Description.WsdlImporter> , wsdl meta verilerini bir <xref:System.ServiceModel.Description.MetadataSet> nesnede paketlenmiş ekli ilkelerle içe aktarır.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü, meta verilerin nasıl içeri aktarılacağını denetlemenizi sağlar. Tüm uç noktaları, tüm bağlamaları veya sözleşmelerin tümünü içeri aktarabilirsiniz. Belirli bir WSDL hizmeti, bağlama veya bağlantı noktası türüyle ilişkili tüm uç noktaları içeri aktarabilirsiniz. Ayrıca belirli bir wsdl bağlantı noktası için, belirli bir wsdl bağlaması için bağlama veya belirli bir WSDL bağlantı noktası türü için anlaşma için uç noktayı içeri aktarabilirsiniz.  
  
 Ayrıca içeri aktarılması gerekmeyen <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> bir anlaşma kümesi belirtmenize olanak tanıyan bir özellik sunar. <xref:System.ServiceModel.Description.WsdlImporter> , <xref:System.ServiceModel.Description.WsdlImporter> Meta verilerden aynı nitelikli ada <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> sahip bir sözleşmeyi içeri aktarmak yerine, özelliğindeki sözleşmeleri kullanır.  
  
### <a name="importing-policies"></a>Ilkeleri içeri aktarma  
 Türü ileti, işlem ve uç nokta ilkesi ilgililere ekli ilke ifadelerini toplar ve ardından ilke ifadelerini içeri aktarmak için <xref:System.ServiceModel.Description.IPolicyImportExtension> <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> koleksiyondaki uygulamaları kullanır. <xref:System.ServiceModel.Description.WsdlImporter>  
  
 İlke içeri aktarma mantığı, aynı WSDL belgesindeki ilke ifadelerine ilke başvurularını otomatik olarak işler ve bir `wsu:Id` veya `xml:id` özniteliği ile tanımlanır. İlke içeri aktarma mantığı, bir ilke ifadesinin boyutunu 4096 düğüm olarak sınırlayarak, bir düğüm aşağıdaki öğelerden biri olduğunda, uygulamaları döngüsel ilke başvurularına karşı korur `wsp:Policy`:, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 İlke içeri aktarma mantığı ayrıca ilke ifadelerini otomatik olarak normalleştirir. İç içe geçmiş ilke ifadeleri `wsp:Optional` ve özniteliği normalleştirilemez. Gerçekleştirilen normalleştirme işlemi miktarı 4096 adımla sınırlıdır, burada her bir adım bir ilke onaylama veya bir `wsp:ExactlyOne` öğenin alt öğesi oluşturur.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Tür, farklı WSDL ilkesi konularıyla eklenmiş olan en fazla 32 ilke alternatiflerinin bir düzeyini gerçekleştirmeye çalışır. Hiçbir birleşim düzgün bir şekilde içeri aktarılmadığında, ilk bileşim kısmi özel bağlama oluşturmak için kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 <xref:System.ServiceModel.Description.MetadataExporter> Hem `Errors` hem de türleri,Araçlaruygularkenkullanılabilecek,sırasıyladışarıveiçeriaktarmaişlemlerindekarşılaşılanbirhataveuyarıiletisikoleksiyonuiçerebilenbir<xref:System.ServiceModel.Description.MetadataImporter> özelliği kullanıma sunar.  
  
 Tür genellikle içeri aktarma işlemi sırasında yakalanan özel durum için bir özel durum oluşturur ve `Errors` özelliğine karşılık gelen bir hata ekler. <xref:System.ServiceModel.Description.WsdlImporter> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> Ancak,<xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> , ve yöntemleri bu özel durumları oluşturmaz, bu nedenle bu yöntemleri çağırırken herhangi bir sorun olup olmadığını `Errors` öğrenmek için özelliği denetlemeniz gerekir. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Tür, dışa aktarma işlemi sırasında yakalanan tüm özel durumları yeniden oluşturur. Bu özel durumlar, `Errors` özelliğinde hata olarak yakalanmaz. Bir özel durum oluşturduğunda, hata hatalı durumdadır ve yeniden kullanılamaz. <xref:System.ServiceModel.Description.WsdlExporter> , <xref:System.ServiceModel.Description.WsdlExporter> Joker karakter eylemlerini kullandığından ve `Errors` yinelenen bağlama adlarına rastlana kadar bir işlem verilemediği zaman, özelliğine uyarı ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Meta verileri hizmet uç noktalarına aktar](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 İndirilen meta verilerin açıklama nesnelerine nasıl içeri aktarılacağını açıklar.  
  
 [Nasıl yapılır: Hizmet uç noktalarından meta verileri dışarı aktar](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Açıklama nesnelerinin meta verilere nasıl dışarı aktarılacağını açıklar.  
  
 [ServiceDescription ve WSDL Başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Açıklama nesneleri ve WSDL arasındaki eşlemeyi açıklar.  
  
 [Nasıl yapılır: Meta verileri derlenmiş hizmet kodundan dışarı aktarmak için Svcutil. exe kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Derlenmiş derlemelerde hizmetlerin, sözleşmelerin ve veri türlerinin meta verilerini dışarı aktarmak için Svcutil. exe ' nin kullanımını açıklar.  
  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini <xref:System.Runtime.Serialization.DataContractSerializer> açıklayan, tarafından kullanılan XML şemasının (xsd) alt kümesini açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
