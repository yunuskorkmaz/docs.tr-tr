---
title: "Meta Verileri Dışarı ve İçeri Aktarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a2785f74d9a07b267d836a9f6e6749d259a1ab21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exporting-and-importing-metadata"></a>Meta Verileri Dışarı ve İçeri Aktarma
İçinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], meta verileri dışarı aktarma işlemidir hizmet uç noktaları açıklayan ve istemcilerin Hizmeti'nin nasıl kullanılacağını anlamak için kullanabileceği bir paralel, standartlaştırılmış gösterimine yansıtma. Hizmet meta verilerini alma işlemidir oluşturmanın <xref:System.ServiceModel.Description.ServiceEndpoint> örneği veya hizmet meta verilerini parçalarını.  
  
## <a name="exporting-metadata"></a>Meta verileri dışarı aktarma  
 Meta verilerini dışa aktarmak için <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> örnekleri, kullanın uygulaması <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf. <xref:System.ServiceModel.Description.WsdlExporter> Türü uygulamasıdır <xref:System.ServiceModel.Description.MetadataExporter> soyut sınıf ile birlikte gelen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> Türü olarak kapsüllenmiş iliştirilmiş ilke ifadelerle Web Hizmetleri Açıklama Dili (WSDL) meta veri oluşturur bir <xref:System.ServiceModel.Description.MetadataSet> örneği. Kullanabileceğiniz bir <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> tekrarlayarak meta verilerini dışa aktarmak için örnek <xref:System.ServiceModel.Description.ContractDescription> nesneleri ve <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri. Bir koleksiyonu dışarı aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri ve belirli hizmet adı ile ilişkilendirin.  
  
> [!NOTE]
>  Yalnızca kullanabilirsiniz `WsdlExporter` meta verilerini dışa aktarmak için `ContractDescription` ortak dil çalışma zamanı (CLR) içeren örnekleri tür bilgilerini, gibi bir `ContractDescription` kullanılarak oluşturulan örnek `ContractDescription.GetContract` yöntemi veya bir parçası olarak oluşturulan `ServiceDescription` için bir `ServiceHost` örneği. Kullanamazsınız `WsdlExporter` meta verilerini dışa aktarmak için `ContractDescription` örnekleri hizmet meta verilerinden içeri aktarılan veya tür bilgileri oluşturulur.  
  
## <a name="importing-metadata"></a>Meta verileri içe aktarma  
  
### <a name="importing-wsdl-documents"></a>WSDL belge alma  
 Hizmet meta verilerde almak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uygulaması kullanmak <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf. <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> Türü uygulamasıdır <xref:System.ServiceModel.Description.MetadataImporter> soyut sınıf ile birlikte gelen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Description.WsdlImporter> Yazın WSDL meta verilerini bağlı ilkeleri ile birlikte içeri aktarmalar bir <xref:System.ServiceModel.Description.MetadataSet> nesnesi.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Meta verileri içeri aktarma üzerinden denetim türü sağlar. Tüm bağlamaları veya tüm sözleşmelerin bitiş noktalarının tümü içeri aktarabilirsiniz. Özel WSDL hizmeti, bağlama veya bağlantı noktası türü ile ilişkili bitiş noktalarının tümü içeri aktarabilirsiniz. Belirli bir WSDL bağlantı noktasını, belirli bir WSDL bağlama için bağlama veya özel bir WSDL bağlantı türü için anlaşma için uç noktaya da içeri aktarabilirsiniz.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> De kullanıma sunan bir <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> aktarılması gerekmez sözleşmeleri kümesi belirtmenize olanak tanır özelliği. <xref:System.ServiceModel.Description.WsdlImporter> Sözleşmelerinde kullanan <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> aynı tam ada sahip bir sözleşme meta verileri içe aktarma yerine özelliği.  
  
### <a name="importing-policies"></a>İlkeleri içe aktarma  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü, işlem iletisine ilke ifadelerini toplar ve son nokta İlkesi konuları ve ardından <xref:System.ServiceModel.Description.IPolicyImportExtension> uygulamalarında <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> ilke ifadelerini almak için koleksiyonu.  
  
 İlke alma mantığını otomatik olarak ilke ifadelerini aynı WSDL belgesinde İlkesi başvurular işler ve ile tanımlanan bir `wsu:Id` veya `xml:id` özniteliği. Bir ilke ifadesi bir düğüm, aşağıdaki öğeleri biri olduğu 4096 düğümlere boyutunu sınırlayarak döngüsel İlkesi başvuruları karşı uygulamalar ilkesi alma mantığı korur: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 İlke içeri aktarma mantığı da otomatik olarak ilke ifadelerini normalleştirir. İlke ifadeleri iç içe geçmiş ve `wsp:Optional` özniteliği Normalleştirilmemiş. Bitti normalleştirme işleme miktarı her adım burada verir İlkesi onaylama ya da bir alt öğesi 4096 adımlarına sınırlıdır bir `wsp:ExactlyOne` öğesi.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü farklı WSDL İlkesi konuları iliştirilmiş ilke alternatifleri en fazla 32 birleşimlerini çalışır. Hiçbir birlikte düzgün bir şekilde alınıyorsa, ilk birleşim kısmi özel bağlama oluşturmak için kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 Hem <xref:System.ServiceModel.Description.MetadataExporter> ve <xref:System.ServiceModel.Description.MetadataImporter> türleri kullanıma bir `Errors` hata ve uyarı iletileri dışarı ve içeri aktarma işlemi sırasında sırasıyla karşılaştı koleksiyonu içerebilir, kullanılabilen araçlar uygularken özelliği.  
  
 <xref:System.ServiceModel.Description.WsdlImporter> Türü genellikle aykırı bir özel durum içeri aktarma işlemi sırasında yakalanan ve karşılık gelen bir hata ekler için kendi `Errors` özelliği. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, Ve <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> yöntemleri, ancak değil throw bu özel durumlar işaretlemeniz gerekir böylece `Errors` sorunları bu yöntemleri çağrılırken oluştu belirlemek için özellik.  
  
 <xref:System.ServiceModel.Description.WsdlExporter> Türü dışa aktarma işlemi sırasında yakalanan özel durumlar yeniden oluşturur. Bu özel durumlar olarak hatalar yakalanmaz `Errors` özelliği. Bir kez <xref:System.ServiceModel.Description.WsdlExporter> özel durumu verir, hatalı bir durumda olduğundan ve yeniden kullanılamaz. <xref:System.ServiceModel.Description.WsdlExporter> Uyarıları Ekle kendi `Errors` joker eylemleri ve yinelenen bağlamayı adları zaman karşılaşılan kullandığından bir işlem verilemez zaman özelliği.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Açıklama nesnelerine indirilen meta verileri içe aktarmayı açıklar.  
  
 [Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışarı Aktarma](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Açıklama nesneleri meta verileri dışarı aktarmak açıklar.  
  
 [ServiceDescription ve WSDL Başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 WSDL ve açıklama nesneleri arasındaki eşlemeyi açıklar.  
  
 [Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Hizmetleri, sözleşmeler ve derlenmiş derlemelerde veri türlerini meta verilerini dışa aktarmak için Svcutil.exe kullanımını açıklar.  
  
 [Veri Sözleşmesi Şema Başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Alt, XML Şeması (tarafından kullanılan XSD) açıklar <xref:System.Runtime.Serialization.DataContractSerializer> ortak dil tanımlamak için XML serileştirmesi için çalışma zamanı (CLR) türleri.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Uzantısı için Özel Meta Verileri Dışarı Aktarma](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 [WCF Uzantısı için Özel Meta Verileri İçe Aktarma](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
