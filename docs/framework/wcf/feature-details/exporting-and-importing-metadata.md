---
title: Meta Verileri Dışarı ve İçeri Aktarma
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: f07a1a10529aa1615bb00a0f3faeca9cb249aa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595537"
---
# <a name="exporting-and-importing-metadata"></a>Meta Verileri Dışarı ve İçeri Aktarma
Windows Communication Foundation (WCF) ' de, meta verileri dışarı aktarma işlemi, hizmet uç noktalarını açıklama ve bunları istemcilerin hizmeti nasıl kullanacağınızı anlamak için kullanabileceği paralel ve standartlaştırılmış bir gösterimde yansıtma işlemidir. Hizmet meta verilerinin içeri aktarılması, <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet meta verilerinden örnek veya parçalar oluşturma işlemidir.  
  
## <a name="exporting-metadata"></a>Meta veriler dışarı aktarılıyor  
 Örneklerden meta verileri dışarı aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> soyut sınıfın bir uygulamasını kullanın <xref:System.ServiceModel.Description.MetadataExporter> . <xref:System.ServiceModel.Description.WsdlExporter>Tür, <xref:System.ServiceModel.Description.MetadataExporter> WCF 'ye dahil edilen soyut sınıfın uygulamasıdır.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType>Tür, bir örnekte kapsüllenmiş ekli ilke ifadelerine sahip Web Hizmetleri Açıklama Dili (wsdl) meta verileri oluşturur <xref:System.ServiceModel.Description.MetadataSet> . <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType>Nesneler ve nesneler için meta verileri tekrarlayarak dışarı aktarmak için bir örneği kullanabilirsiniz <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.ServiceEndpoint> . Ayrıca, bir nesne koleksiyonunu dışarı aktarabilir <xref:System.ServiceModel.Description.ServiceEndpoint> ve bunları belirli bir hizmet adıyla ilişkilendirebilirsiniz.  
  
> [!NOTE]
> Yalnızca, `WsdlExporter` `ContractDescription` `ContractDescription` yöntemi kullanılarak oluşturulan `ContractDescription.GetContract` veya örneğin bir parçası olarak oluşturulan bir örnek gibi ortak DIL çalışma zamanı (CLR) tür bilgilerini içeren örneklerden meta verileri dışarı aktarmak için ' i kullanabilirsiniz `ServiceDescription` `ServiceHost` . ' `WsdlExporter` `ContractDescription` Nı, hizmet meta verilerinden içeri aktarılan örneklerden meta verileri dışarı aktarmak için kullanamazsınız veya tür bilgisi olmadan oluşturulabilir.  
  
## <a name="importing-metadata"></a>Meta veriler içeri aktarılıyor  
  
### <a name="importing-wsdl-documents"></a>WSDL belgelerini içeri aktarma  
 WCF 'de hizmet meta verilerini içeri aktarmak için soyut sınıfın bir uygulamasını kullanın <xref:System.ServiceModel.Description.MetadataImporter> . <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>Tür, <xref:System.ServiceModel.Description.MetadataImporter> WCF 'ye dahil edilen soyut sınıfın uygulamasıdır. <xref:System.ServiceModel.Description.WsdlImporter>Tür, wsdl meta verilerini bir nesnede paketlenmiş ekli ilkelerle içe aktarır <xref:System.ServiceModel.Description.MetadataSet> .  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Türü, meta verilerin nasıl içeri aktarılacağını denetlemenizi sağlar. Tüm uç noktaları, tüm bağlamaları veya sözleşmelerin tümünü içeri aktarabilirsiniz. Belirli bir WSDL hizmeti, bağlama veya bağlantı noktası türüyle ilişkili tüm uç noktaları içeri aktarabilirsiniz. Ayrıca belirli bir wsdl bağlantı noktası için, belirli bir wsdl bağlaması için bağlama veya belirli bir WSDL bağlantı noktası türü için anlaşma için uç noktayı içeri aktarabilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Ayrıca <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> içeri aktarılması gerekmeyen bir anlaşma kümesi belirtmenize olanak tanıyan bir özellik sunar. , <xref:System.ServiceModel.Description.WsdlImporter> <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> Meta verilerden aynı nitelikli ada sahip bir sözleşmeyi içeri aktarmak yerine, özelliğindeki sözleşmeleri kullanır.  
  
### <a name="importing-policies"></a>Ilkeleri içeri aktarma  
 <xref:System.ServiceModel.Description.WsdlImporter>Türü ileti, işlem ve uç nokta ilkesi ilgililere ekli ilke ifadelerini toplar ve ardından <xref:System.ServiceModel.Description.IPolicyImportExtension> <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> ilke ifadelerini içeri aktarmak için koleksiyondaki uygulamaları kullanır.  
  
 İlke içeri aktarma mantığı, aynı WSDL belgesindeki ilke ifadelerine ilke başvurularını otomatik olarak işler ve bir veya özniteliği ile tanımlanır `wsu:Id` `xml:id` . İlke içeri aktarma mantığı, bir ilke ifadesinin boyutunu 4096 düğüm olarak sınırlayarak, bir düğüm aşağıdaki öğelerden biri olduğunda, uygulamaları döngüsel ilke başvurularına karşı korur: `wsp:Policy` , `wsp:All` , `wsp:ExactlyOne` , `wsp:policyReference` .  
  
 İlke içeri aktarma mantığı ayrıca ilke ifadelerini otomatik olarak normalleştirir. İç içe geçmiş ilke ifadeleri ve `wsp:Optional` özniteliği normalleştirilemez. Gerçekleştirilen normalleştirme işlemi miktarı 4096 adımla sınırlıdır, burada her bir adım bir ilke onaylama veya bir öğenin alt öğesi oluşturur `wsp:ExactlyOne` .  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Tür, farklı WSDL ilkesi konularıyla eklenmiş olan en fazla 32 ilke alternatiflerinin bir düzeyini gerçekleştirmeye çalışır. Hiçbir birleşim düzgün bir şekilde içeri aktarılmadığında, ilk bileşim kısmi özel bağlama oluşturmak için kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 Hem <xref:System.ServiceModel.Description.MetadataExporter> hem de <xref:System.ServiceModel.Description.MetadataImporter> türleri, `Errors` Araçlar uygularken kullanılabilecek, sırasıyla dışarı ve içeri aktarma işlemlerinde karşılaşılan bir hata ve uyarı iletisi koleksiyonu içerebilen bir özelliği kullanıma sunar.  
  
 <xref:System.ServiceModel.Description.WsdlImporter>Tür genellikle içeri aktarma işlemi sırasında yakalanan özel durum için bir özel durum oluşturur ve özelliğine karşılık gelen bir hata ekler `Errors` . <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>Ancak, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> , <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> ve <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> yöntemleri bu özel durumları oluşturmaz, `Errors` Bu nedenle bu yöntemleri çağırırken herhangi bir sorun olup olmadığını öğrenmek için özelliği denetlemeniz gerekir.  
  
 <xref:System.ServiceModel.Description.WsdlExporter>Tür, dışa aktarma işlemi sırasında yakalanan tüm özel durumları yeniden oluşturur. Bu özel durumlar, özelliğinde hata olarak yakalanmaz `Errors` . <xref:System.ServiceModel.Description.WsdlExporter>Bir özel durum oluşturduğunda, hata hatalı durumdadır ve yeniden kullanılamaz. , <xref:System.ServiceModel.Description.WsdlExporter> `Errors` Joker karakter eylemlerini kullandığından ve yinelenen bağlama adlarına rastlana kadar bir işlem verilemediği zaman, özelliğine uyarı ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma](how-to-import-metadata-into-service-endpoints.md)  
 İndirilen meta verilerin açıklama nesnelerine nasıl içeri aktarılacağını açıklar.  
  
 [Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışarı Aktarma](how-to-export-metadata-from-service-endpoints.md)  
 Açıklama nesnelerinin meta verilere nasıl dışarı aktarılacağını açıklar.  
  
 [ServiceDescription ve WSDL Başvurusu](servicedescription-and-wsdl-reference.md)  
 Açıklama nesneleri ve WSDL arasındaki eşlemeyi açıklar.  
  
 [Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Derlenmiş derlemelerde hizmetlerin, sözleşmelerin ve veri türlerinin meta verilerini dışarı aktarmak için Svcutil. exe ' nin kullanımını açıklar.  
  
 [Veri Sözleşmesi Şema Başvurusu](data-contract-schema-reference.md)  
 <xref:System.Runtime.Serialization.DataContractSerializer>XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini açıklayan, tarafından kullanılan XML şemasının (xsd) alt kümesini açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma](../extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../extending/importing-custom-metadata-for-a-wcf-extension.md)
