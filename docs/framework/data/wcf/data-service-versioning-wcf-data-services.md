---
title: Veri hizmeti sürümü oluşturma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 03ac1e0a5fec2d7def91466a9dc31853e2007f57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791063"
---
# <a name="data-service-versioning-wcf-data-services"></a>Veri hizmeti sürümü oluşturma (WCF Veri Hizmetleri)
, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] İstemcilerin veri modeli tabanlı URI 'leri kullanarak verilere kaynak olarak erişebilmeleri için veri Hizmetleri oluşturmanızı sağlar. OData Ayrıca hizmet işlemlerinin tanımını da destekler. İlk dağıtımdan sonra ve ömrü boyunca birkaç kez, bu veri hizmetlerinin iş ihtiyaçlarını değiştirme, bilgi teknolojisi gereksinimleri veya diğer sorunları ele almak gibi çeşitli nedenlerle değiştirilmesi gerekebilir. Var olan bir veri hizmetinde değişiklik yaptığınızda, veri hizmetinizin yeni bir sürümünü tanımlayıp tanımlamadığınızı ve var olan istemci uygulamalarında etkisini en iyi duruma küçültmenizi göz önünde bulundurmanız gerekir. Bu konu, bir veri hizmetinin yeni bir sürümünün nasıl ve ne zaman oluşturulacağı hakkında rehberlik sağlar. Ayrıca, WCF Veri Hizmetleri OData protokolünün farklı sürümlerini destekleyen istemciler ve veri Hizmetleri arasında bir alışverişi nasıl işlediğini açıklar.

## <a name="versioning-a-wcf-data-service"></a>WCF veri hizmeti sürümü oluşturma
 Veri hizmeti dağıtıldıktan ve veriler tüketildikten sonra, veri hizmetindeki değişiklikler mevcut istemci uygulamalarıyla uyumluluk sorunlarına neden olabilir. Bununla birlikte, değişiklikler genellikle hizmetin genel iş ihtiyaçları için gerektiğinden, istemci uygulamalarında en az etki ile veri hizmetinizin yeni bir sürümünü oluşturmayı göz önünde bulundurmanız gerekir.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Yeni bir veri hizmeti sürümü için önerilen veri modeli değişiklikleri
 Bir veri hizmetinin yeni bir sürümünü yayımladığınızı düşünürken, farklı değişiklik türlerinin istemci uygulamalarını nasıl etkileyebileceğini anlamak önemlidir. Bir veri hizmetinin yeni bir sürümünü oluşturmanızı gerektirebilecek bir veri hizmetindeki değişiklikler aşağıdaki iki kategoriye ayrılabilir:

- Hizmet sözleşmesindeki değişiklikler; hizmet işlemlerine yönelik güncelleştirmeler, varlık kümelerinin erişilebilirliği (akışlar), sürüm değişiklikleri ve hizmet davranışlarındaki diğer değişiklikler dahil olmak üzere değişir.

- Veri sözleşmesindeki değişiklikler (veri modeli, akış biçimleri veya akış özelleştirmelerinde değişiklikler dahil).

 Aşağıdaki tabloda, veri hizmetinin yeni bir sürümünü yayımlamayı düşünmeniz gereken değişiklik türleri için ayrıntılar verilmiştir:

|Değişiklik türü|Yeni bir sürüm gerektirir|Yeni sürüm gerekli değil|
|--------------------|----------------------------|----------------------------|
|Hizmet işlemleri|-Yeni parametre Ekle<br />-Dönüş türünü değiştir<br />-Hizmet işlemini kaldır|-Var olan parametreyi sil<br />-Yeni hizmet işlemi Ekle|
|Hizmet davranışları|-Count isteklerini devre dışı bırak<br />-Projeksiyon desteğini devre dışı bırak<br />-Gerekli veri hizmeti sürümünü artırın|-Count isteklerini etkinleştir<br />-Projeksiyon desteğini etkinleştir<br />-Gerekli veri hizmeti sürümünü azaltın|
|Varlık kümesi izinleri|-Varlık kümesi izinlerini kısıtla<br />-Yanıt kodunu değiştir (yeni ilk basamak değeri) <sup>1</sup>|-Rahat varlık kümesi izinleri<br />-Değişiklik yanıt kodu (aynı ilk basamak değeri)|
|Varlık özellikleri|-Var olan özelliği veya ilişkiyi kaldır<br />-Nullable özelliği Ekle<br />-Var olan özelliği Değiştir|-Nullable özelliği ekleyin<sup>2</sup>|
|Varlık kümeleri|-Varlık kümesini kaldır|-Türetilmiş tür Ekle<br />-Temel türü Değiştir<br />-Varlık kümesi ekleme|
|Akış özelleştirmesi|-Varlık özelliği eşlemesini Değiştir||

 <sup>1</sup> bu, ne kadar istemci uygulamanın belirli bir hata kodunu alma ile ilgili olduğuna bağlı olabilir.

 <sup>2</sup> <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği`true` , istemcisini, istemci üzerinde tanımlanmayan veri hizmeti tarafından gönderilen yeni özellikleri yoksayacak şekilde ayarlayabilirsiniz. Ancak, ekleme yapıldığında, POST isteğindeki istemci tarafından dahil edilen özellikler varsayılan değerlerine ayarlanır. Güncelleştirmeler için, istemciye yönelik bilinmeyen bir özelliğindeki mevcut verilerin üzerine varsayılan değerler eklenebilir. Bu durumda, güncelleştirmeyi varsayılan olan bir BIRLEŞTIRME isteği olarak göndermeniz gerekir. Daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Veri hizmeti sürümü
 Gerektiğinde, yeni bir veri hizmeti sürümü, güncelleştirilmiş bir hizmet sözleşmesi veya veri modeliyle hizmetin yeni bir örneği oluşturularak tanımlanır. Bu yeni hizmet daha sonra yeni bir URI uç noktası kullanılarak sunulur ve bu, önceki sürümden farklılaştırır. Örneğin:

- Eski sürüm:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Yeni sürüm:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Bir veri hizmetini yükseltirken, istemcilerin yeni veri hizmeti meta verilerine göre de güncelleştirilmeleri ve yeni kök URI 'yi kullanması gerekir. Mümkün olduğunda, yeni sürümü kullanmak üzere henüz yükseltilmemiş istemcileri desteklemek için veri hizmetinin önceki sürümünü korumanız gerekir. Daha eski bir veri hizmeti sürümü, artık gerekli olmadığında kaldırılabilir. Veri hizmeti uç noktası URI 'sini bir dış yapılandırma dosyasında tutmak düşünmelisiniz.

## <a name="odata-protocol-versions"></a>OData protokol sürümleri
 OData 'in yeni sürümleri yayınlanarak, istemci uygulamaları veri hizmeti tarafından desteklenen aynı OData protokolü sürümünü kullanmıyor olabilir. Daha eski bir istemci uygulaması, OData 'in daha yeni bir sürümünü destekleyen bir veri hizmetine erişebilir. Bir istemci uygulaması, WCF Veri Hizmetleri istemci kitaplığının daha yeni bir sürümünü kullanıyor olabilir. Bu, erişilmekte olan veri hizmetiyle daha yeni bir OData sürümü destekler.

 WCF Veri Hizmetleri, bu sürüm oluşturma senaryolarını işlemek için OData tarafından sunulan destekten yararlanır. İstemci, veri hizmetinin kullandığı farklı bir OData sürümü kullandığında istemci veri hizmeti sınıfları oluşturmak için veri modeli meta verilerini oluşturma ve kullanma desteği de mevcuttur. Daha fazla bilgi için bkz [. OData: Protokol sürümü](https://go.microsoft.com/fwlink/?LinkId=186071)oluşturma.

### <a name="version-negotiation"></a>Sürüm anlaşması
 Veri hizmeti, istemci tarafından istenen sürümden bağımsız olarak, hizmet tarafından kullanılacak olan OData protokolünün en yüksek sürümünü tanımlayacak şekilde yapılandırılabilir. Bunu, veri hizmeti tarafından <xref:System.Data.Services.Common.DataServiceProtocolVersion> <xref:System.Data.Services.DataServiceBehavior> kullanılan <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> özelliği için bir değer belirterek yapabilirsiniz. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

 Bir uygulama bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplıklarını kullandığında, bu üst bilgileri OData sürümüne ve uygulamanızda kullanılan özelliklere bağlı olarak doğru değerlere otomatik olarak ayarlar. Varsayılan olarak, WCF Veri Hizmetleri istenen işlemi destekleyen en düşük protokol sürümünü kullanır.

 Aşağıdaki tabloda, OData protokolünün belirli sürümleri için WCF Veri Hizmetleri desteği içeren .NET Framework ve Silverlight sürümlerinin ayrıntıları verilmiştir.

|OData protokol sürümü|Destek sunulan...|
|-----------------------------------------------------------------------------------|----------------------------|
|Sürüm 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Hizmet paketi 1 (SP1)<br />-Silverlight sürüm 3|
|Sürüm 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-SP1 için [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] bir güncelleştirme. Güncelleştirmeyi [Microsoft Indirme merkezi](https://go.microsoft.com/fwlink/?LinkId=158125)' nden indirip yükleyebilirsiniz.<br />-Silverlight sürüm 4|
|Sürüm 3|- [Microsoft Indirme merkezi](https://go.microsoft.com/fwlink/?LinkId=203885)'nden OData sürüm 3 ' ü destekleyen bir yayın öncesi sürümü indirebilir ve yükleyebilirsiniz.|

### <a name="metadata-versions"></a>Meta veri sürümleri
 WCF Veri Hizmetleri, varsayılan olarak, bir veri modelini temsil etmek için CSDL 1,1 sürümünü kullanır. Bu, bir yansıma sağlayıcısına veya özel bir veri hizmeti sağlayıcısına dayalı veri modelleri için her zaman durumdur. Ancak, veri modeli kullanılarak [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]tanımlandığında, döndürülen CSDL sürümü, [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]tarafından kullanılan sürümle aynıdır. CSDL sürümü, [şema öğesinin (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)ad alanı tarafından belirlenir.

 Döndürülen meta verilerin `DataServiceVersion` `DataServiceVersion` `DataServices` öğesi, yanıt iletisindeki üst bilgiyle aynı değer olan bir özniteliği de içerir. Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusu gibi istemci uygulamaları, bu bilgileri, veri hizmetini barındıran WCF veri Hizmetleri sürümü ile düzgün çalışan istemci veri hizmeti sınıfları oluşturmak için kullanır. Daha fazla bilgi için bkz [. OData: Protokol sürümü](https://go.microsoft.com/fwlink/?LinkId=186071)oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
