---
title: Veri Hizmeti sürüm oluşturma (WCF Veri Hizmetleri)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d795008e014deaa126dac1bb978ac825f2536208
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="data-service-versioning-wcf-data-services"></a>Veri Hizmeti sürüm oluşturma (WCF Veri Hizmetleri)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Veri Hizmetleri oluşturun, böylece istemciler URI'ler kullanarak kaynakları, bir veri modeline bağlı olarak veri erişim sağlar. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Ayrıca hizmet işlemleri tanımını destekler. İlk dağıtım ve olası birkaç kez kendi ömürleri sırasında sonra bu veri hizmetleri için çeşitli iş gereksinimlerini, bilgi teknolojisi gereksinimleri değiştirme gibi nedenlerle, değiştirilecek veya diğer sorunları gidermek için gerekebilir. Varolan bir veri hizmeti bir değişiklik yaptığınızda mi verilerinizi yeni bir sürümünü tanımlamak dikkate almanız gereken service ve mevcut istemci uygulamaları üzerindeki etkiyi en aza indirmek en iyi nasıl. Bu konu, ne zaman ve nasıl veri hizmeti, yeni bir sürümünü oluşturmak yönergeler sağlar. Ayrıca açıklanır nasıl [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir exchange istemcileri ve farklı sürümlerini destekler veri hizmetleri arasında işleme [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü.  
  
## <a name="versioning-a-wcf-data-service"></a>WCF veri hizmeti sürüm oluşturma  
 Veri Hizmeti dağıtılır ve veri tüketilen sonra veri hizmeti değişiklikleri mevcut istemci uygulamalarıyla uyumluluk sorunlarına neden olma olasılığı vardır. Ancak, değişiklikleri genellikle hizmetin genel iş gereksinimlerine göre gerekli olduğundan, veri hizmeti yeni bir sürümü ile en az etkileyen istemci uygulamaları oluşturmak nasıl ve ne zaman düşünmelisiniz.  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Yeni bir veri hizmeti sürüm önerilir veri modeli değişikliklerini  
 Veri hizmetinin yeni bir sürüm yayımlayın verilip değerlendirirken değişiklikleri farklı türde istemci uygulamaları nasıl etkileyebileceğini anlamak önemlidir. Veri Hizmeti, yeni bir sürümünü oluşturmak gereksinim duyabileceğiniz veri hizmeti değişiklikleri aşağıdaki iki kategoriye ayrılabilir:  
  
-   Değişiklikleri hizmet sözleşmesini — hizmet işlemleri, varlık kümeleri (akışları) erişilebilirliğini yapılan değişiklikler, sürüm değişikliklerini ve diğer değişiklikler hizmet davranışları için güncelleştirmeleri içerir.  
  
-   Veri sözleşmesi değişiklikleri — hangi değişiklikleri veri modeline dahil etmek, biçimleri akış veya özelleştirmeleri akış.  
  
 Hangi tür değişiklikler aşağıdaki tabloda ayrıntılarını yeni bir veri hizmeti sürümü yayımlama dikkate almanız gerekir:  
  
|Değişiklik türü|Yeni bir sürümünü gerektirir|Gerekli yeni sürümü|  
|--------------------|----------------------------|----------------------------|  
|Hizmet işlemleri|-Yeni parametre ekleme<br />-Dönüş türü Değiştir<br />-Hizmet işlemi Kaldır|-Mevcut parametreyi Sil<br />-Yeni hizmet işlemi ekleyin|  
|Hizmet davranışları|-Count isteklerini devre dışı bırakın<br />-Projeksiyon desteğini devre dışı bırakın<br />-Artış gerekli veri hizmeti sürümü|-Count isteklerini etkinleştirme<br />-Projeksiyon desteğini etkinleştir<br />-Gerekli veri hizmetinin sürüm azaltma|  
|Varlık izinleri ayarlama|-Varlık kümesi izinleri kısıtla<br />-Yanıt kodunu değiştirme (yeni ilk basamaklı değeri) <sup>1</sup>|-Hafifletin varlık izinleri ayarlama<br />-Yanıt kodunu değiştirme (aynı ilk basamaklı değeri)|  
|Varlık özellikleri|-Mevcut özellik veya ilişki kaldırma<br />-Null özellik ekleme<br />-Mevcut özellik değiştirme|-Add nullable özelliği<sup>2</sup>|  
|Varlık kümeleri|-Varlık kümesini Kaldır|-Türetilen tür ekleyin<br />-Temel türünü değiştirme<br />-Varlık kümesini ekleyin|  
|Akış özelleştirme|-Değişiklik varlığın özellik eşlemesi||  
  
 <sup>1</sup> nasıl kesinlikle bir istemci uygulaması belirli bir kodu alma kullanır bağlı olabilir.  
  
 <sup>2</sup> ayarlayabileceğiniz <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliğine `true` bir istemcinin istemci üzerinde tanımlı değil veri hizmeti tarafından gönderilen tüm yeni özellikleri yoksay. Ancak, eklemeleri yapıldığında, POST isteğini dosyasındaki istemci tarafından bulunmayan özellikler varsayılan değerlerine ayarlanır. Güncelleştirmeler için varsayılan değerlerle istemciye Bilinmeyen özellik varolan tüm verilerin üzerine. Bu durumda, güncelleştirme varsayılan birleştirme isteği göndermesi gerekir. Daha fazla bilgi için bkz: [veri Hizmet bağlamı yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
### <a name="how-to-version-a-data-service"></a>Veri Hizmeti sürüm nasıl  
 Gerektiğinde, yeni bir veri hizmeti sürüm bir güncelleştirilmiş hizmet sözleşmesi veya veri modeli ile hizmet yeni bir örneğini oluşturarak tanımlanır. Bu yeni hizmet önceki bir sürümden ayıran bir yeni URI uç noktası aracılığıyla sunulur. Örneğin:  
  
-   Eski sürümü: `http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   Yeni sürüm: `http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 Veri Hizmeti yükseltirken, istemciler temelinde yeni veri hizmeti meta verilerini ve yeni kök URI kullanmayı da güncelleştirilmesi gerekir. Mümkün olduğunda, henüz yeni sürümü kullanmak için yükseltilmemiş istemcileri desteklemek için veri hizmeti önceki sürümünü korumanız gerekir. Artık gerektiğinde daha eski bir veri hizmeti sürümleri kaldırılabilir. Veri Hizmeti uç noktası URI bir dış yapılandırma dosyasında koruma göz önünde bulundurmalısınız.  
  
## <a name="odata-protocol-versions"></a>OData protokol sürümleri  
 Yeni sürümlerini olarak [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] olan yayımlanan, istemci uygulamaları aynı sürümünü kullanıyor olabilirsiniz değil [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri hizmeti tarafından desteklenen protokol. Eski istemci uygulamanın daha yeni bir sürümünü destekleyen bir veri hizmeti erişebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Bir istemci uygulaması da daha yeni bir sürümü kullanılarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] daha yeni bir sürümünü destekleyen istemci Kitaplığı [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] erişiliyor veri hizmeti daha.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tarafından sağlanan destek yararlanır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bu sürüm senaryolara işlemek için. Ayrıca oluşturma ve veri modelinin meta verilerini kullanarak istemci farklı bir sürümünü kullanırken istemci veri hizmeti sınıfları oluşturma desteği yoktur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri hizmeti kullanır. Daha fazla bilgi için bkz: [OData: iletişim kuralı sürüm](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
### <a name="version-negotiation"></a>Sürüm anlaşması  
 Veri Hizmeti yüksek sürümü tanımlamak için yapılandırılabilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bakılmaksızın istemci tarafından istenilen hizmeti tarafından kullanılan protokol. Bunu belirterek yapmak bir <xref:System.Data.Services.Common.DataServiceProtocolVersion> değerini <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> özelliği <xref:System.Data.Services.DataServiceBehavior> veri hizmeti tarafından kullanılan. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Bir uygulama kullandığında [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplıkları bir veri hizmeti otomatik olarak erişmek için istemci kitaplıkları sürümüne bağlı olarak doğru değerlerin bu üstbilgileri kümesine [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ve uygulamanızda kullanılan özellik. Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istenen işlem desteklediği en düşük protokol sürümünü kullanır.  
  
 Aşağıdaki tabloda sürümleri ayrıntıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] içeren [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] belirli sürümleri için destek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü.  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokol sürümü|Sürümünde sunulan destek...|  
|-----------------------------------------------------------------------------------|----------------------------|  
|Sürüm 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] Sürüm 3|  
|Sürüm 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Bir güncelleştirme [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Güncelleştirmeyi yükleyip [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] sürüm 4|  
|Sürüm 3|-Karşıdan yükleyip destekleyen bir yayın öncesi sürüm [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 3 sürümünden [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=203885).|  
  
### <a name="metadata-versions"></a>Meta veri sürümleri  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir veri modeli temsil etmek için CSDL 1.1 sürümünü kullanır. Bu her zaman bir yansıma sağlayıcısı veya bir özel veri hizmeti sağlayıcısı dayanarak veri modelleri için geçerlidir. Ancak, ne zaman veri modeli tanımlanmış kullanarak [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], CSDL sürümü döndürülen tarafından kullanılan sürümüyle aynı [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. CSDL sürümü ad alanı tarafından belirlenir [Schema öğesi](http://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] belirtimi [ \[MC CSDL\]: kavramsal şema tanım dosyası biçimi](http://go.microsoft.com/fwlink/?LinkId=159072).  
  
 `DataServices` Döndürülen meta veri öğesi de içerir bir `DataServiceVersion` değerin aynısıdır özniteliği olarak `DataServiceVersion` üstbilgisi yanıt iletisi. İstemci uygulamaları gibi **hizmet Başvurusu Ekle** Visual Studio, istemci veri hizmeti oluşturmak için bu bilgileri doğru sürümü ile çalışan sınıfları kullanım iletişim kutusunda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmeti ana bilgisayar. Daha fazla bilgi için bkz: [OData: iletişim kuralı sürüm](http://go.microsoft.com/fwlink/?LinkId=186071).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
