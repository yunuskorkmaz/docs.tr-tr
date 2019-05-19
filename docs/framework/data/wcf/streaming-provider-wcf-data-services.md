---
title: Akış sağlayıcısı (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
ms.openlocfilehash: eff4ee3cb8502645d3b6d9a8986c9c410fe73f1a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877587"
---
# <a name="streaming-provider-wcf-data-services"></a>Akış sağlayıcısı (WCF Data Services)

Bir veri hizmeti, büyük nesne ikili verilerini açığa çıkarabilir. Bu ikili veriler, video ve ses akışları, görüntüleri, belge dosyaları ya da diğer ikili medya türleri temsil edebilir. Bir varlık veri Modeli'nde bir veya daha fazla ikili özellikleri içerdiğinde, bu ikili veri akışı yanıt giriş içinde base 64 olarak kodlanmış veri hizmeti döndürür. Yükleme ve bu şekilde büyük ikili verileri seri hale getirme, performansı etkileyebilir çünkü [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] ait olduğu varlığı bağımsız ikili verileri almak için bir mekanizma tanımlar. Bu işlem, ikili veri varlıktan bir veya daha fazla veri akışlarını ayrılarak gerçekleştirilir.

- Medya kaynağı - video, ses, görüntü veya diğer türdeki bir medya kaynak akışı gibi bir varlığa ait ikili veriler.

- Medya bağlantı giriş - ilgili medya kaynak akışı başvurusu olan bir varlık.

İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir akış veri sağlayıcısı uygulayarak bir ikili kaynak akışı tanımlayın. Akış sağlayıcısı uygulaması belirli bir varlıkla ilişkili medya kaynak akışı ile veri hizmeti sağlayan bir <xref:System.IO.Stream> nesne. Bu uygulama kabul edin ve ortam kaynakları belirtilen MIME türünün ikili veri akışları olarak HTTP üzerinden döndürmek veri hizmeti sağlar.

İkili verilerden akış desteklemek için bir veri hizmeti yapılandırma aşağıdakileri gerektirir:

1. Bir medya bağlantısı olarak giriş veri modeli'ndeki varlıkları bir veya daha fazla öznitelik. Bu varlıklar, ikili veri akışını içermemelidir. Bir varlığın herhangi bir ikili özelliği her zaman giriş base-64 kodlu ikili döndürülür.

2. T:System.Data.Services.Providers.IDataServiceStreamProvider arabirim uygular.

3. Uygulayan bir veri hizmeti tanımlayan <xref:System.IServiceProvider> arabirimi. Veri hizmeti kullanan <xref:System.IServiceProvider.GetService%2A> akış veri sağlayıcı uygulaması erişmek için uygulama. Bu yöntem, uygun Akış sağlayıcısı uygulamasını döndürür.

4. Büyük ileti akışları Web uygulama yapılandırmasında etkinleştirin.

5. Sunucuda veya bir veri kaynağındaki ikili kaynaklara erişimini etkinleştirir.

Bu konudaki örnekleri akış derinlemesine gönderisinde açıklanan fotoğraf hizmeti, bir örneği temel alarak [Veri Hizmetleri Akış sağlayıcısı serisi: Bir Akış sağlayıcısı (Bölüm 1) uygulama](https://go.microsoft.com/fwlink/?LinkID=198989). Bu örnek hizmeti için kaynak kodu kullanılabilir [akış fotoğraf veri hizmeti örnek sayfası](https://go.microsoft.com/fwlink/?LinkID=198988) MSDN Kod Galerisi'nde.

## <a name="defining-a-media-link-entry-in-the-data-model"></a>Veri modelinde bir medya bağlantısı girişinin tanımlama

Veri kaynağı sağlayıcı bir varlık veri modeli bir medya bağlantı giriş olarak tanımlandığı şekilde belirler.

**Entity Framework Sağlayıcısı**

Bir varlığa bir medya bağlantısı girişinin olduğunu belirtmek için ekleme `HasStream` aşağıdaki örnekteki gibi kavramsal modelin varlık tür tanımında öznitelik:

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Ad alanı da eklemelisiniz `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` veya varlık veri modelini tanımlar .edmx veya .csdl dosyasının kök.

Veri hizmetinin kullanan bir örnek [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı ve ortaya çıkaran bir medya kaynağı gönderiye bakın [Veri Hizmetleri Akış sağlayıcısı serisi: Bir Akış sağlayıcısı (Bölüm 1) uygulama](https://go.microsoft.com/fwlink/?LinkID=198989).

**Yansıma Sağlayıcısı**

Bir varlığa bir medya bağlantısı girişinin olduğunu belirtmek için ekleme <xref:System.Data.Services.Common.HasStreamAttribute> yansıma sağlayıcısı varlık türü tanımlayan sınıf.

**Özel veri hizmeti sağlayıcısı**

Özel hizmet sağlayıcıları kullanırken, uygulamanız <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> veri hizmetinizi için meta verileri tanımlamak için arabirim. Daha fazla bilgi için [özel veri hizmeti sağlayıcılarını](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Bir ikili kaynak akışı ait olduğunu belirten bir <xref:System.Data.Services.Providers.ResourceType> ayarlayarak <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> özelliğini `true` üzerinde <xref:System.Data.Services.Providers.ResourceType> medya bağlantısı girişinin varlık türünü temsil eder.

## <a name="implementing-the-idataservicestreamprovider-interface"></a>IDataServiceStreamProvider arabirimini uygulama

İkili veri akışlarını destekleyen bir veri hizmeti oluşturmak için uygulamanız gereken <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi. Bu uygulama, ikili veri akışı olarak istemciye döndürür ve istemciden gönderilen bir akış olarak ikili verileri kullanmak veri hizmeti sağlar. Veri Hizmeti, ikili veri akışı olarak erişim gerektiğinde bu arabirim örneği oluşturur. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Arabirimi aşağıdaki üyeleri belirtir:

|Üye adı|Açıklama|
|-----------------|-----------------|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Bu yöntem, medya bağlantısı girişinin silindiğinde karşılık gelen medya kaynağı silmek için veri hizmeti tarafından çağrılır. Uyguladığınızda <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, bu yöntem, sağlanan media link entry ile ilişkili medya kaynağı siler kodu içerir.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Bu yöntem, bir akış olarak bir medya kaynağı döndürmek için veri hizmeti tarafından çağrılır. Uyguladığınızda <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, bu yöntem veri hizmeti tarafından sağlanan media link entry ile ilişkili olan dönüş medya kaynağı için kullanılan bir akış sağladığı kodunu içerir.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Bu yöntem, medya kaynağı için media link entry istemek için kullanılan URI döndürmek için veri hizmeti tarafından çağrılır. Bu değer oluşturmak için kullanılan `src` media link entry ve içerik öğesindeki özniteliği veri akışını istemek için kullanılır. Bu yöntem döndürdüğünde `null`, veri hizmeti otomatik olarak URI belirler. Akış sağlayıcısı kullanmadan istemciler ikili verilere doğrudan erişime olanak sağlamak, ihtiyacınız olduğunda bu yöntemi kullanın.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Bu yöntem, belirtilen media link entry ile ilişkili medya kaynağı Content-Type değerini döndürmek için veri hizmeti tarafından çağrılır.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Bu yöntem, belirtilen varlık ile ilişkili veri akışının eTag döndürmek için veri hizmeti tarafından çağrılır. İkili veriler için eşzamanlılık yönettiğinizde, bu yöntem kullanılır. Bu yöntem null değeri döndürür, veri hizmeti eşzamanlılık izlemez.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Bu yöntem, akış alma istemciden gönderilirken kullanılan akış almak için veri hizmeti tarafından çağrılır. Uyguladığınızda <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, veri hizmeti yazma alınan akış verilerini yazılabilir bir akış döndürmelidir.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Veri Hizmeti çalışma zamanı eklenmekte medya kaynağı için veri akışı ile ilişkili olan media link entry oluşturmalıdır türünü temsil eden bir ad alanıyla nitelenen tür adı döndürür.|

## <a name="creating-the-streaming-data-service"></a>Akış veri hizmeti oluşturma

Sağlamak üzere [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] erişimi olan çalışma zamanı <xref:System.Data.Services.Providers.IDataServiceStreamProvider> uygulama, oluşturduğunuz veri hizmeti uygulanmalı ayrıca <xref:System.IServiceProvider> arabirimi. Aşağıdaki örnek nasıl uygulayacağınızı gösteren <xref:System.IServiceProvider.GetService%2A> örneği döndürülecek yöntemi `PhotoServiceStreamProvider` uygulayan sınıf <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.

[!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_service/cs/photodata.svc.cs#photoservicestreamingprovider)]
[!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_service/vb/photodata.svc.vb#photoservicestreamingprovider)]

Bir veri hizmeti oluşturma hakkında genel bilgi için bkz. [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Büyük ikili akışlar barındırma ortamında etkinleştirme

Bir ASP.NET Web uygulamasında veri hizmeti oluşturduğunuzda, Windows Communication Foundation (WCF) HTTP protokolü uygulamasını sağlamak için kullanılır. Varsayılan olarak, WCF HTTP iletileri yalnızca 65 K bayt boyutunu sınırlar. Büyük ikili veri akışı için ve veri hizmetinden kullanabilmek için Web uygulaması büyük ikili dosyaları etkinleştirmek ve aktarım için akışları kullanmak için yapılandırmanız gerekir. Bunu yapmak için aşağıdaki ekleyin `<configuration />` uygulamanın Web.config dosyasının öğe:

> [!NOTE]
> Kullanmanız gereken bir <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> istek ve yanıt iletilerindeki ikili veri akışı ve WCF tarafından arabelleğe değil emin olmak için aktarım modu.

Daha fazla bilgi için [ileti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) ve [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).

Varsayılan olarak, Internet Information Services (IIS) istekleri 4 MB boyutunu da sınırlar. Veri hizmetinizi IIS üzerinde çalışan akışlar 4 MB'tan büyük alma etkinleştirmek için de ayarlamalısınız `maxRequestLength` özniteliği [httpRuntime öğesi (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)) içinde `<system.web />` yapılandırma bölümü olarak Aşağıdaki örnekte gösterilen:

## <a name="using-data-streams-in-a-client-application"></a>Bir istemci uygulamasında veri akışlarını kullanma

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci Kitaplığı hem alma hem de istemcide ikili akış olarak sunulan bu kaynakları güncelleştirme olanak sağlar. Daha fazla bilgi için [ikili verilerle çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).

## <a name="considerations-for-working-with-a-streaming-provider"></a>Bir akış sağlayıcı ile çalışma konuları

Akış sağlayıcısı uyguladığınızda ve ortam kaynaklarına eriştiğinizde veri hizmetinden göz önünde bulundurulması gerekenler şunlardır:

- Birleştirme isteklerini medya kaynakları için desteklenmez. Bir PUT İsteği, var olan bir varlığın medya kaynağı değiştirmek için kullanın.

- Bir POST isteği yeni bir medya bağlantısı girişinin oluşturmak için kullanılamaz. Bunun yerine, yeni bir medya kaynağı oluşturmak için bir POST isteği yayımlamanız gerekir ve veri hizmeti yeni bir medya bağlantısı girişinin varsayılan değerlerle oluşturur. Bu yeni bir varlık, bir sonraki birleştirme veya PUT isteği tarafından güncelleştirilebilir. Ayrıca, varlık önbelleğe almayı düşünün ve POST isteğinde başlık üstbilgisi değerini özellik değerini ayarlamak gibi disposer güncelleştirmeleri yapmanız.

- Bir POST isteği alındığında çağrıları veri hizmeti <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> kendisinden önce medya kaynağı oluşturmak için çağırdığı <xref:System.Data.Services.IUpdatable.SaveChanges%2A> medya bağlantısı girişinin oluşturma.

- Uygulanışı <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> değil döndürmelidir bir <xref:System.IO.MemoryStream> nesne. Bu tür bir akışı kullandığınızda, hizmet çok büyük veri akışlarını aldığında bellek kaynağı sorunları ortaya çıkar.

- Ortam kaynakları bir veritabanında saklarken göz önünde bulundurulması gerekenler şunlardır:

  - Veri modelinde bir medya kaynağı olan bir ikili özellik eklenmemelidir. Bir veri modeli kullanıma sunulan tüm özellikler, Giriş akışı bir yanıt döndürülür.

  - Büyük ikili akışı performansı artırmak için veritabanında ikili verileri depolamak için bir özel akış sınıf oluşturmanızı öneririz. Bu sınıf tarafından döndürülen, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> uygulama ve ikili veri öbekleri veritabanına gönderir. Bir SQL Server veritabanı için ikili verileri 1 MB'den büyük olduğunda bir FILESTREAM veri akışı veritabanına kullanmanızı öneririz.

  - Veritabanınızı, veri hizmeti tarafından alınabilmesi için olan büyük ikili akışlar depolamak için tasarlandığından emin olun.

  - Bir istemci bir medya bağlantı Giriş bir medya kaynağı ile tek bir istekte eklemek için bir POST isteği gönderdiğinde <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> veri hizmeti veritabanına yeni bir varlık ekler önce akışa almak için çağrılır. Bir akış sağlayıcı uygulaması bu verileri hizmet davranışı işleyebilir olması gerekir. İkili verileri veya varlık sonra kadar bir dosyadaki veri akışını veritabanına eklenmiş deposu depolamak için ayrı veri tablosu kullanmayı düşünün.

- Uyguladığınızda <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, veya <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> yöntemlerini kullanmanız gerekir eTag ve sağlanan içerik türü değerleri yöntem parametreleri. ETag veya Content-Type üst bilgilerinde ayarlı değil, <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcısı uygulaması.

- Varsayılan olarak, istemci bir öbekli HTTP Transfer-Encoding kullanarak büyük ikili akışlar gönderir. ASP.NET geliştirme sunucusu bu tür kodlamayı desteklemediği için büyük ikili akışlar kabul etmesi gereken bir akış veri hizmeti barındırmak için bu Web sunucusu kullanamazsınız. ASP.NET Geliştirme Sunucusu hakkında daha fazla bilgi için bkz. [ASP.NET Web projeleri için Visual Studio'daki Web sunucuları](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

<a name="versioning"></a>

## <a name="versioning-requirements"></a>Sürüm gereksinimleri

Aşağıdaki Akış sağlayıcısı olan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokolü sürüm gereksinimleri:

- Akış sağlayıcısı, veri hizmeti 2.0 sürümünü desteklemesini gerektirir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol ve sonraki sürümler.

Daha fazla bilgi için [veri hizmeti sürümü oluşturma](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Özel Veri Hizmeti Sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
- [İkili Verilerle Çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
