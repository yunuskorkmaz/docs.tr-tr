---
title: Meta Verileri Dışarı ve İçeri Aktarma
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 39b964584cde42e6569da35f8653042f6d7432cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091947"
---
# <a name="exporting-and-importing-metadata"></a>Meta Verileri Dışarı ve İçeri Aktarma
Windows Communication Foundation (WCF) meta verileri dışarı aktarma, hizmet uç noktaları tanımlamak ve bunları istemcilere hizmetin nasıl kullanılacağını anlamak için kullanabileceğiniz bir paralel, standartlaştırılmış gösterimine yansıtma işlemidir. Hizmet meta verileri alma, oluşturma işlemi olduğundan <xref:System.ServiceModel.Description.ServiceEndpoint> örneği veya hizmet meta verileri bölümleri.  
  
## <a name="exporting-metadata"></a>Meta verileri dışarı aktarma  
 Meta verileri dışarı aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> örnekleri kullanmak uygulaması <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf. <xref:System.ServiceModel.Description.WsdlExporter> Türüdür yürütmesinin <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf ile WCF dahil.  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Türü içinde kapsüllenir iliştirilmiş ilke ifadeleri ile Web Hizmetleri Açıklama Dili (WSDL) meta verileri oluşturan bir <xref:System.ServiceModel.Description.MetadataSet> örneği. Kullanabileceğiniz bir <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> çalıştırmalarınızı için meta verileri dışarı aktarmak için örnek <xref:System.ServiceModel.Description.ContractDescription> nesneleri ve <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri. Bir koleksiyonu da verebilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri ve bunları belirli bir hizmet adı ile ilişkilendirin.  
  
> [!NOTE]
>  Yalnızca kullanabilirsiniz `WsdlExporter` meta verileri dışarı aktarmak için `ContractDescription` tür bilgilerini, gibi ortak dil çalışma zamanı (CLR) içeren örnek bir `ContractDescription` örneği kullanılarak oluşturulan `ContractDescription.GetContract` yöntemi veya parçası olarak oluşturulan `ServiceDescription` için bir `ServiceHost` örneği. Kullanamazsınız `WsdlExporter` meta verileri dışarı aktarmak için `ContractDescription` örnekleri hizmet meta verilerden içe aktarıldı veya tür bilgisi oluşturulmuş.  
  
## <a name="importing-metadata"></a>Meta verileri içe aktarma  
  
### <a name="importing-wsdl-documents"></a>WSDL belgeleri alma  
 WCF hizmet meta verileri içeri aktarmak için uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türüdür yürütmesinin <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf ile WCF dahil. <xref:System.ServiceModel.Description.WsdlImporter> Yazın WSDL meta verilerini bağlı ilkeleri ile birlikte, içeri aktarmalar bir <xref:System.ServiceModel.Description.MetadataSet> nesne.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Meta verileri içeri aktarma üzerinde denetim türü sağlar. Tüm uç noktaları, tüm bağlamaları veya tüm sözleşmelerin içeri aktarabilirsiniz. Belirli bir WSDL hizmetine, bağlama veya bağlantı noktası türü ile ilişkili uç noktaları tümünün içeri aktarabilirsiniz. Ayrıca, belirli bir WSDL bağlantı noktasını, belirli bir WSDL bağlama için bağlama veya belirli bir WSDL bağlantı türü için bir sözleşme için uç nokta içeri aktarabilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> De sunan bir <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> özelliği içeri aktarılması gerekmez sözleşmeleri kümesi belirtmenizi sağlar. <xref:System.ServiceModel.Description.WsdlImporter> Sözleşmeleri kullanan <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> aynı tam ada sahip bir sözleşme meta verileri içeri aktarma yerine özellik.  
  
### <a name="importing-policies"></a>İlkeleri alma  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü, işlem, iletiye eklenmiş ilke ifadeleri toplar ve uç noktası İlkesi konuları ve ardından <xref:System.ServiceModel.Description.IPolicyImportExtension> uygulamalarında <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> ilke ifadeleri içeri aktarmak için koleksiyon.  
  
 İlke alma mantığını otomatik olarak aynı WSDL belgesinde ilke ifadeleri ilke başvuruları işler ve ile tanımlanan bir `wsu:Id` veya `xml:id` özniteliği. İlke alma mantığını ilke döngüsel başvurular karşı uygulamalar bir ilke ifadesi 4096 düğümlerine, aşağıdaki öğeleri biri olduğu bir düğüm boyutu sınırlayarak korur: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 İlke alma mantığını ilke ifadeleri otomatik olarak normalleştirir. İlke ifadeleri iç içe geçmiş ve `wsp:Optional` özniteliği Normalleştirilmemiş. Bitti normalleştirme işleme miktarı her adım burada verir İlkesi eklemesi veya alt öğesi 4096 adımlarına sınırlıdır bir `wsp:ExactlyOne` öğesi.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü farklı WSDL ilke konuları iliştirilmiş ilke alternatifleri 32 adede kadar bir birleşimiyle çalışır. Birleşimi düzgün bir şekilde içeri aktarırsa, ilk birleşim kısmi özel bağlama oluşturmak için kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 Hem <xref:System.ServiceModel.Description.MetadataExporter> ve <xref:System.ServiceModel.Description.MetadataImporter> türler açığa bir `Errors` hata ve uyarı iletilerini sırasıyla dışarı ve içeri aktarma işlemi sırasında karşılaşılan bir koleksiyonu içerebilir, kullanılabilen araçları uygularken özelliği.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Türüne karşılık gelen bir hata ekler ve içeri aktarma işlemi sırasında yakalanan özel durum için bir özel durum genellikle oluşturur, `Errors` özelliği. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, Ve <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> yöntemleri, ancak değil throw bu özel durumlar işaretlemeniz gerekir böylece `Errors` özellik sorunları bu yöntemleri çağrılırken oluşup olmadığını belirlemek için.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Beklerseniz dışarı aktarma işlemi sırasında yakalanan özel durumların türü. Hata olarak bu özel durumları yakalanmaz `Errors` özelliği. Bir kez <xref:System.ServiceModel.Description.WsdlExporter> özel durumu oluşturur, hatalı bir durumda olduğundan ve kullanılamayacak. <xref:System.ServiceModel.Description.WsdlExporter> Uyarıları ekleyin, `Errors` özelliğine bir işlem joker Eylemler ve yinelenen bağlama adları ne zaman karşılaşılan kullandığından dışarı aktarılamaz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Açıklama nesnelerini indirilen meta verileri içe aktarmayı açıklar.  
  
 [Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Meta verilere açıklama nesneleri dışa aktarmayı açıklar.  
  
 [ServiceDescription ve WSDL Başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 WSDL ve açıklama nesneler arasındaki eşlemeyi tanımlar.  
  
 [Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Hizmetleri, sözleşmeler ve derlenmiş bütünleştirilmiş kodlar içindeki veri türleri için meta verileri dışarı aktarmak için Svcutil.exe kullanımı açıklanmaktadır.  
  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Açıklar, XML Şeması (tarafından kullanılan XSD) alt <xref:System.Runtime.Serialization.DataContractSerializer> açıklayan ortak dil çalışma zamanı (CLR) için XML serileştirme türleri.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
