---
title: Veri Hizmeti sürümü oluşturma (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 9a92346267012d3651d04648b357bbf530097e34
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565645"
---
# <a name="data-service-versioning-wcf-data-services"></a>Veri Hizmeti sürümü oluşturma (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Veri Hizmetleri oluşturun, böylece istemciler URI'lerini kullanarak kaynakları, bir veri modelini temel olarak veri erişim sağlar. OData hizmet işlemleri tanımı da destekler. İlk dağıtım ve potansiyel olarak kendi ömürlerine sırasında birkaç kez sonra çeşitli iş gereksinimlerini, bilgi teknolojisi gereksinimlerini değiştirme gibi nedenlerle, değiştirilecek veya diğer sorunları gidermek için şu veri hizmetlerini gerekebilir. Mevcut bir veri hizmetine değişiklik yaptığınızda olup verilerinizi yeni bir sürümü tanımlamak dikkate almanız gereken hizmet ve istemci uygulamalarınız üzerindeki etkiyi en aza indirmek en iyi nasıl. Bu konu, ne zaman ve nasıl bir veri hizmeti, yeni bir sürümünü oluşturmak yönergeler sağlar. WCF Veri Hizmetleri bir exchange istemcileri ve farklı sürümlerini OData protokolünü destekleyen veri hizmetleri arasında nasıl işlediğini açıklar.

## <a name="versioning-a-wcf-data-service"></a>WCF veri hizmeti sürümü oluşturma
 Bir veri hizmeti dağıtılan ve veri tüketilen sonra veri hizmetine yapılan mevcut istemci uygulamalarıyla uyumluluk sorunlarına neden olma olasılığı vardır. Ancak, değişiklikler genellikle hizmet genel iş gereksinimlerine göre gerekli olduğundan, veri hizmetinizin yeni bir sürümü en az etkileyerek istemci uygulamaları oluşturmak nasıl ve ne zaman düşünmelisiniz.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Yeni bir veri hizmeti sürümü önerilir veri modeli değişikliklerini
 Veri hizmetinin yeni bir sürüm yayınlanıp yayınlanmayacağını dikkate alındığında, farklı türde değişiklikler istemci uygulamaları nasıl etkileyebileceğini anlamak önemlidir. Bir veri hizmeti, yeni bir sürümünü oluşturmak gerektirebilir veri hizmetine değişiklikler aşağıdaki iki kategoriye ayrılabilir:

-   Değişiklikleri için hizmet sözleşmesi — hizmet işlemleri, varlık kümelerini (akışları) erişilebilirliğini değişiklikler, sürüm değişikliklerini ve hizmet davranışlarını diğer değişiklikler için güncelleştirmeleri içerir.

-   Değişiklikler için veri anlaşması — hangi değişiklikleri veri modeline dahil etmek, biçimleri akışı veya özelleştirmeleri akış.

 Aşağıdaki tablo, hangi türde değişiklikler için yeni bir veri hizmeti sürümü yayımlamalıyım ayrıntıları:

|Değişiklik türü|Yeni bir sürümünü gerektirir|Yeni sürüm gerekli|
|--------------------|----------------------------|----------------------------|
|Hizmet işlemleri|-Yeni parametre Ekle<br />-Dönüş türünü değiştir<br />-Hizmet işlemi Kaldır|-Var olan bir parametreyi Sil<br />-Yeni bir hizmet işlemi ekleme|
|Hizmet davranışları|-Count istekleri devre dışı bırak<br />-Projeksiyon desteğini devre dışı bırak<br />-Gerekli veri hizmeti sürümü artırın|-Count isteklerini etkinleştir<br />-Projeksiyon desteğini etkinleştir<br />-Gerekli veri hizmeti sürümü Azalt|
|Varlık izinleri ayarlayın|-Varlık kümesi izinleri kısıtla<br />-Yanıt kodu değiştirin (yeni ilk basamak değeri) <sup>1</sup>|-Varlık kümesi izinlerini ılımlı hale getirme<br />-Yanıt kodu değiştirin (aynı ilk basamak değeri)|
|Varlık özellikleri|-Varolan bir özellik veya ilişki kaldırma<br />-Atanamayan özellik ekleme<br />-Mevcut özelliğini değiştirme|-Nullable özelliği ekleme<sup>2</sup>|
|Varlık kümeleri|-Varlık kümesini Kaldır|-Türetilmiş bir tür ekleme<br />-Temel türünü değiştirme<br />-Varlık kümesi Ekle|
|Akış özelleştirme|-Varlık özellik eşlemesi değiştirin||

 <sup>1</sup> nasıl kesin olarak belirli bir kodu alınmasına bir istemci uygulaması dayanır bağlı olabilir.

 <sup>2</sup> ayarlayabileceğiniz <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliğini `true` ve istemciye istemcide tanımlanmayan veri hizmeti tarafından gönderilen herhangi bir özelliği yoksayın. Ancak, eklemeleri yapıldığında POST isteği istemci tarafından bulunmayan özellikleri varsayılan değerlerine ayarlanır. Güncelleştirmeler için varsayılan değerlerle istemciye Bilinmeyen özellik mevcut tüm verilerin üzerine. Bu durumda, güncelleştirme varsayılandır ve birleştirme isteği göndermesi gerekir. Daha fazla bilgi için [veri hizmeti bağlamını yönetme](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Bir veri hizmeti sürümü oluşturma
 Gerektiğinde, yeni bir veri hizmeti sürümü, güncelleştirilmiş hizmet sözleşmesi veya veri modeliyle hizmetinin yeni bir örneğini oluşturarak tanımlanır. Bu yeni hizmet, ardından önceki sürümden ayırır yeni bir URI endpoint kullanarak kullanıma sunulur. Örneğin:

-   Eski sürümü: `http://services.odata.org/Northwind/v1/Northwind.svc/`

-   Yeni sürüm: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Bir veri hizmeti yükseltirken, istemciler yeni kök URI'nin kullanılacak ve yeni veri hizmeti meta verilere göre de güncelleştirilmesi gerekir. Mümkün olduğunda, henüz yeni sürümü kullanmak için yükseltilmemiş olan istemcileri desteklemek için veri hizmeti önceki sürümünü korumanız gerekir. Veri hizmetinin eski sürümleri artık gerekli olmadığında kaldırılabilir. Veri Hizmeti uç noktası URI'si bir dış yapılandırma dosyasında koruma dikkate almanız gerekir.

## <a name="odata-protocol-versions"></a>OData protokol sürümleri
 OData yeni sürümlerini yayımlanan gibi istemci uygulamaları aynı veri hizmeti tarafından desteklenen OData protokolü sürümünü kullanmıyor olabilirsiniz. Daha eski bir istemci uygulama, OData daha yeni bir sürümünü destekleyen bir veri hizmeti erişebilir. Bir istemci uygulaması da erişiliyor veri hizmeti daha yeni bir sürümü, OData destekler WCF Veri Hizmetleri İstemci Kitaplığı'nın daha yeni bir sürümü kullanıyor olabilirsiniz.

 WCF Veri Hizmetleri OData gibi sürüm oluşturma senaryoları işlemek için sağlanan desteğin yararlanır. Oluşturma ve veri modelinin meta verilerini kullanarak istemci OData veri sürümünden farklı bir sürüm kullandığında, istemci veri hizmeti sınıfları oluşturma desteği de mevcuttur hizmeti kullanır. Daha fazla bilgi için [OData: Protokolü sürüm](https://go.microsoft.com/fwlink/?LinkId=186071).

### <a name="version-negotiation"></a>Sürüm belirleme
 Veri Hizmeti istemci tarafından istenen sürümünden bağımsız olarak hizmeti tarafından kullanılacak olan OData protokolü en yüksek sürümü tanımlamak için yapılandırılabilir. Belirterek bunu yapabilirsiniz bir <xref:System.Data.Services.Common.DataServiceProtocolVersion> değerini <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> özelliği <xref:System.Data.Services.DataServiceBehavior> veri hizmeti tarafından kullanılır. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

 Bir uygulama bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplıkları kullandığında, kitaplıkları otomatik olarak bu üstbilgileri OData ve uygulamanızda kullanılan özelliklere sürümüne bağlı olarak doğru değerleri ayarlayın. Varsayılan olarak, WCF Veri Hizmetleri istenen işlem destekleyen en düşük protokol sürümü kullanır.

 Aşağıdaki tabloda sürümleri ayrıntıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] WCF Veri Hizmetleri OData protokolünü belirli sürümlerini desteği içerir.

|OData protokolü sürümü|Sunulan destek...|
|-----------------------------------------------------------------------------------|----------------------------|
|Sürüm 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Hizmet Paketi 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] sürüm 3|
|Sürüm 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Bir güncelleştirme [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Güncelleştirmeyi yükleyip [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] sürüm 4|
|sürüm 3|- İndirip destekleyen OData sürümü 3 yayın öncesi bir sürümü yükleyin [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Meta veri sürümleri
 WCF Veri Hizmetleri, varsayılan olarak, bir veri modeli temsil etmek için CSDL 1.1 sürümünü kullanır. Bu her zaman bir yansıma sağlayıcısı veya özel veri hizmeti sağlayıcısı dayalı veri modelleri için geçerlidir. Ancak, ne zaman veri modeli tanımlanmıştır kullanarak [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], CSDL sürümünü döndürülen tarafından kullanılan sürümü aynı [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. CSDL sürümü ad alanı tarafından belirlenir [şema öğesi](https://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f). Daha fazla bilgi için bkz: belirtimi [ \[MC CSDL\]: kavramsal şema tanım dosyası biçimi](https://go.microsoft.com/fwlink/?LinkId=159072).

 `DataServices` Döndürülen meta veri öğesi de içeren bir `DataServiceVersion` aynı değer özniteliği olarak `DataServiceVersion` yanıt iletisinde üst bilgi. İstemci uygulamaları gibi **hizmet Başvurusu Ekle** iletişim kutusu Visual Studio'da veri hizmetini barındıran WCF Data Services sürümü ile düzgün çalışmak istemci veri hizmeti sınıfları oluşturmak için bu bilgileri kullanın. Daha fazla bilgi için [OData: Protokolü sürüm](https://go.microsoft.com/fwlink/?LinkId=186071).

## <a name="see-also"></a>Ayrıca Bkz.

- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
