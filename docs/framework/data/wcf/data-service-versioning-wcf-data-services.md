---
title: Veri Hizmeti Sürümü (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121534"
---
# <a name="data-service-versioning-wcf-data-services"></a>Veri Hizmeti Sürümü (WCF Veri Hizmetleri)
Açık Veri Protokolü (OData), istemcilerin veri modelini temel alan IU'ları kullanarak verilere kaynak olarak erişebilmeleri için veri hizmetleri oluşturmanıza olanak tanır. OData ayrıca hizmet işlemlerinin tanımını da destekler. İlk dağıtımdan sonra ve kullanım ömürleri boyunca birkaç kez bu veri hizmetlerinin iş gereksinimlerini değiştirmek, bilgi teknolojisi gereksinimleri veya diğer sorunları gidermek gibi çeşitli nedenlerle değiştirilmesi gerekebilir. Varolan bir veri hizmetinde değişiklik yaptığınızda, veri hizmetinizin yeni bir sürümünü tanımlayıp tanımlamayacağınızve varolan istemci uygulamaları üzerindeki etkisini en iyi nasıl en aza indirdiğinizi göz önünde bulundurmanız gerekir. Bu konu, bir veri hizmetinin ne zaman ve nasıl oluşturulacaklarına ilişkin rehberlik sağlar. Ayrıca, WCF Veri Hizmetleri'nin istemciler ve Veri Hizmetleri arasında OData protokolünün farklı sürümlerini destekleyen bir alışverişi nasıl işleyeceğini de açıklar.

## <a name="versioning-a-wcf-data-service"></a>WCF Veri Hizmetini Sürümleme
 Bir veri hizmeti dağıtıldıktan ve veriler tüketildikten sonra, veri hizmetindeki değişiklikler varolan istemci uygulamalarıyla uyumluluk sorunlarına neden olma potansiyeline sahiptir. Ancak, değişiklikler genellikle hizmetin genel iş gereksinimleri tarafından gerekli olduğundan, istemci uygulamaları üzerinde en az etkiye sahip veri hizmetinizin yeni bir sürümünün ne zaman ve nasıl oluşturulacağını göz önünde bulundurmanız gerekir.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Yeni Veri Hizmeti Sürümü Öneren Veri Modeli Değişiklikleri
 Bir veri hizmetinin yeni bir sürümünüyayımlanıp yayımlanmayacağı düşünülürken, farklı değişiklik türlerinin istemci uygulamalarını nasıl etkileyebileceğini anlamak önemlidir. Veri hizmetinin yeni bir sürümünü oluşturmanızı gerektirebilecek bir veri hizmetinde yapılan değişiklikler aşağıdaki iki kategoriye ayrılabilir:

- Hizmet işlemlerigüncelleştirmeleri, varlık kümelerinin (özet akışlarının) erişilebilirliğindeki değişiklikleri, sürüm değişikliklerini ve hizmet davranışlarındaki diğer değişiklikleri içeren hizmet sözleşmesindeki değişiklikler.

- Veri modelinde, akış biçimlerinde veya özet akışı özelleştirmelerinde yapılan değişiklikleri içeren veri sözleşmesinde yapılan değişiklikler.

 Veri hizmetinin yeni bir sürümünü yayımlamayı düşünmeniz gereken değişiklik türlerinin ayrıntılarını aşağıdaki tablo ayrıntıları:

|Değişim Türü|Yeni bir sürüm gerektirir|Yeni sürüm gerekli değil|
|--------------------|----------------------------|----------------------------|
|Servis işlemleri|- Yeni parametre ekle<br />- İade türünü değiştir<br />- Hizmet işlemini kaldırma|- Varolan parametreyi silme<br />- Yeni hizmet işlemi ekleme|
|Hizmet davranışları|- Sayım isteklerini devre dışı<br />- Projeksiyon desteğini devre dışı<br />- Gerekli veri hizmeti sürümünü artırma|- Sayım isteklerini etkinleştirme<br />- Projeksiyon desteğini etkinleştirme<br />- Gerekli veri hizmeti sürümünü azaltma|
|Varlık belirleme izinleri|- Varlık kümesi izinlerini kısıtlama<br />- Yanıt kodunu değiştir (yeni ilk basamak değeri) <sup>1</sup>|- Relax varlık seti izinleri<br />- Yanıt kodunu değiştir (aynı ilk basamak değeri)|
|Varlık özellikleri|- Varolan özelliği veya ilişkiyi kaldırma<br />- Nullable özellik ekleme<br />- Varolan özelliği değiştirme|- Nullable özellik<sup>ekle 2</sup>|
|Varlık kümeleri|- Varlık kümesini kaldırma|- Türetilmiş tür ekleme<br />- Temel türünü değiştir<br />- Varlık kümesi ekle|
|Besleme özelleştirme|- Varlık-özellik eşlemelerini değiştirme||

 <sup>1</sup> Bu, istemci uygulamasının belirli bir hata kodu almaya ne kadar güvendiğine bağlı olabilir.

 <sup>2</sup> <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> Özelliği, `true` istemcinin veri hizmeti tarafından gönderilen ve istemciüzerinde tanımlanmayan yeni özellikleri yoksaymasını sağlayacak şekilde ayarlayabilirsiniz. Ancak, ekler yapıldığında, POST isteğine istemci tarafından dahil olmayan özellikler varsayılan değerlerine ayarlanır. Güncelleştirmeler için, istemci tarafından bilinmeyen bir özellikteki varolan veriler varsayılan değerlerle birlikte üzerine yazılmış olabilir. Bu durumda, güncelleştirmeyi varsayılan olan bir MERGE isteği olarak göndermeniz gerekir. Daha fazla bilgi için [bkz.](managing-the-data-service-context-wcf-data-services.md)

### <a name="how-to-version-a-data-service"></a>Veri Hizmeti Sürümü Nasıl Kullanılır?
 Gerektiğinde, güncelleştirilmiş bir hizmet sözleşmesi veya veri modeli ile hizmetin yeni bir örneği oluşturularak yeni bir veri hizmeti sürümü tanımlanır. Bu yeni hizmet daha sonra önceki sürümden ayıran yeni bir URI uç noktası kullanılarak ortaya çıkar. Örneğin:

- Eski sürüm:`http://services.odata.org/Northwind/v1/Northwind.svc/`

- Yeni sürüm:`http://services.odata.org/Northwind/v2/Northwind.svc/`

 Bir veri hizmetini yükseltirken, istemcilerin yeni veri hizmeti meta verilerine göre de güncelleştirilmeleri ve yeni kök URI'yi kullanmaları gerekir. Mümkün olduğunda, yeni sürümü kullanmak üzere henüz yükseltilmemiş istemcileri desteklemek için veri hizmetinin önceki sürümünü korumanız gerekir. Bir veri hizmetinin eski sürümleri artık gerekolmadığında kaldırılabilir. Veri hizmeti bitiş noktası URI'yi harici bir yapılandırma dosyasında korumayı düşünmelisiniz.

## <a name="odata-protocol-versions"></a>OData Protokolü Sürümleri
 OData'nın yeni sürümleri yayımlandıkça, istemci uygulamaları veri hizmeti tarafından desteklenen OData protokolünün aynı sürümünü kullanmıyor olabilir. Eski bir istemci uygulaması, OData'nın daha yeni bir sürümünü destekleyen bir veri hizmetine erişebilir. İstemci uygulaması, Erişilen veri hizmetinden daha yeni bir OData sürümünü destekleyen WCF Veri Hizmetleri istemci kitaplığı'nın daha yeni bir sürümünü de kullanıyor olabilir.

 WCF Veri Hizmetleri, bu tür sürüm senaryolarını işlemek için OData tarafından sağlanan destekten yararlanır. İstemci, veri hizmetinin kullandığından farklı bir OData sürümünü kullandığında istemci veri hizmeti sınıfları oluşturmak için veri modeli meta verileri oluşturma ve kullanma desteği de vardır. Daha fazla bilgi [için, OData: Genel Bakış](https://www.odata.org/documentation/odata-version-2-0/overview/) makalesindeki Protokol Sürümü bölümüne bakın.

### <a name="version-negotiation"></a>Sürüm Görüşmesi
 Veri hizmeti, istemci tarafından istenen sürümden bağımsız olarak, hizmet tarafından kullanılacak OData protokolünün en yüksek sürümünü tanımlayacak şekilde yapılandırılabilir. Bunu, veri hizmeti tarafından <xref:System.Data.Services.Common.DataServiceProtocolVersion> <xref:System.Data.Services.DataServiceBehavior> kullanılan <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> özelliği için bir değer belirterek yapabilirsiniz. Daha fazla bilgi için [bkz.](configuring-the-data-service-wcf-data-services.md)

 Bir uygulama bir veri hizmetine erişmek için WCF Veri Hizmetleri istemci kitaplıklarını kullandığında, kitaplıklar bu başlıkları Otomatik Olarak OData sürümüne ve uygulamanızda kullanılan özelliklere bağlı olarak otomatik olarak doğru değerlere ayarlar. Varsayılan olarak, WCF Veri Hizmetleri istenen işlemi destekleyen en düşük iletişim kuralı sürümünü kullanır.

 Aşağıdaki tabloda, OData protokolünün belirli sürümleri için WCF Veri Hizmetleri desteği içeren .NET Framework ve Silverlight sürümleri ayrıntılı olarak açıklamaktadır.

|OData Protokolü Sürümü|Destek tanıtıldı...|
|-----------------------------------------------------------------------------------|----------------------------|
|Sürüm 1|- .NET Framework 3.5 Servis Paketi 1 (SP1)<br />- Silverlight sürüm 3|
|Sürüm 2|- .NET Çerçeve 4<br />- Silverlight sürüm 4|

### <a name="metadata-versions"></a>Meta veri sürümleri
 Varsayılan olarak, WCF Veri Hizmetleri bir veri modelini temsil etmek için CSDL'nin 1.1 sürümünü kullanır. Bu, yansıma sağlayıcısını veya özel veri servis sağlayıcısını temel alan veri modelleri için her zaman geçerlidir. Ancak, veri modeli Varlık Çerçevesi kullanılarak tanımlandığında, döndürülen CSDL sürümü Varlık Çerçevesi tarafından kullanılan sürümle aynıdır. CSDL sürümü [Schema öğesi (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)ad alanı tarafından belirlenir.

 Döndürülen meta verilerin `DataServices` öğesi, `DataServiceVersion` yanıt iletisindeki `DataServiceVersion` üstbilgiyle aynı değere sahip bir öznitelik de içerir. Visual Studio'daki **Hizmet Başvurusu Ekle** iletişim kutusu gibi istemci uygulamaları, bu bilgileri, veri hizmetini barındıran WCF Veri Hizmetleri sürümüyle doğru çalışan istemci veri hizmeti sınıfları oluşturmak için kullanır. Daha fazla bilgi [için, OData: Genel Bakış](https://www.odata.org/documentation/odata-version-2-0/overview/) makalesindeki Protokol Sürümü bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
