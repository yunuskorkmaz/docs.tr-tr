---
title: Akış sağlayıcısı (WCF Veri Hizmetleri)
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
ms.openlocfilehash: 4d51011fddb856cf1ebd00943e9b79776d9181d0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854116"
---
# <a name="streaming-provider-wcf-data-services"></a>Akış sağlayıcısı (WCF Veri Hizmetleri)

Veri hizmeti, büyük nesne ikili verilerini açığa çıkarır. Bu ikili veriler video ve ses akışlarını, görüntüleri, belge dosyalarını veya diğer ikili medya türlerini temsil edebilir. Veri modelindeki bir varlık bir veya daha fazla ikili özellik içerdiğinde, veri hizmeti yanıt akışındaki girdinin içinde Base-64 olarak kodlanmış bu ikili verileri döndürür. Büyük ikili verilerin bu şekilde yüklenmesi ve serileştirilmesi performansı [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] etkileyebileceğinden, ait olduğu varlıktan bağımsız ikili verileri almak için bir mekanizma tanımlar. Bu, ikili verileri varlıktaki bir veya daha fazla veri akışlarına ayırarak gerçekleştirilir.

- Medya kaynağı-video, ses, görüntü veya başka türde medya kaynağı akışı gibi bir varlığa ait ikili veriler.

- Medya bağlantı girişi-ilgili medya kaynağı akışına başvuran bir varlık.

İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir akış veri sağlayıcısı uygulayarak bir ikili kaynak akışı tanımlarsınız. Akış sağlayıcısı uygulamasında, bir <xref:System.IO.Stream> nesne olarak belirli bir varlıkla ilişkili medya kaynak akışı ile veri hizmeti sağlanır. Bu uygulama, veri hizmetinin, belirtilen bir MIME türünün ikili veri akışları olarak HTTP üzerinden medya kaynaklarını kabul etmesini ve döndürmesini sağlar.

Bir veri hizmetini ikili verilerin akışını destekleyecek şekilde yapılandırmak için aşağıdaki adımlar gereklidir:

1. Veri modelindeki bir veya daha fazla varlığı bir medya bağlantı girişi olarak özniteliği. Bu varlıklar, akışa eklenecek ikili verileri içermemelidir. Bir varlığın herhangi bir ikili özelliği, her zaman girişte Base-64 kodlu ikili olarak döndürülür.

2. T:System.Data.Services.Providers.IDataServiceStreamProvider arabirimini uygulayın.

3. <xref:System.IServiceProvider> Arabirimini uygulayan bir veri hizmeti tanımlayın. Veri hizmeti, akış veri <xref:System.IServiceProvider.GetService%2A> sağlayıcısı uygulamasına erişmek için uygulamasını kullanır. Bu yöntem, uygun akış sağlayıcısı uygulamasını döndürür.

4. Web uygulaması yapılandırmasında büyük ileti akışlarını etkinleştirin.

5. Sunucuda veya bir veri kaynağında ikili kaynaklara erişimi etkinleştirin.

Bu konudaki örnekler, [veri hizmetleri akış sağlayıcısı serisinde derinlemesine bir şekilde açıklanan örnek bir akış fotoğrafı hizmetini temel alır: Akış sağlayıcısı uygulama (1. bölüm)](https://go.microsoft.com/fwlink/?LinkID=198989). Bu örnek hizmetin kaynak kodu, MSDN kod galerisindeki [akış fotoğrafı veri hizmeti örnek sayfasında](https://go.microsoft.com/fwlink/?LinkID=198988) bulunur.

## <a name="defining-a-media-link-entry-in-the-data-model"></a>Veri modelinde medya bağlantısı girişi tanımlama

Veri kaynağı sağlayıcısı, bir varlığın veri modelinde medya bağlantı girişi olarak nasıl tanımlandığını belirler.

**Entity Framework Sağlayıcısı**

Bir varlığın medya bağlantı girişi olduğunu belirtmek için, aşağıdaki örnekte olduğu gibi `HasStream` , kavramsal modeldeki varlık türü tanımına özniteliği ekleyin:

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

Ayrıca, ad alanını `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` varlığa ya da veri modelini tanımlayan. edmx veya. csdl dosyasının köküne eklemeniz gerekir.

Entity Framework sağlayıcıyı kullanan ve bir medya kaynağı sunan bir veri hizmeti örneği için bkz. Post [Data Services akış sağlayıcısı serisi: Akış sağlayıcısı uygulama (1. bölüm)](https://go.microsoft.com/fwlink/?LinkID=198989).

**Yansıma Sağlayıcısı**

Bir varlığın medya bağlantı girişi olduğunu göstermek için, ' yi yansıma sağlayıcısında <xref:System.Data.Services.Common.HasStreamAttribute> varlık türünü tanımlayan sınıfına ekleyin.

**Özel veri hizmeti sağlayıcısı**

Özel hizmet sağlayıcıları kullanırken, veri hizmetiniz için meta <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> verileri tanımlamak üzere arabirimini uygulayın. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md). Bir ikili kaynak akışının öğesine, bir medya bağlantı girişi <xref:System.Data.Services.Providers.ResourceType> olan varlık türünü <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> temsil <xref:System.Data.Services.Providers.ResourceType> eden `true` öğesine özelliği ayarlanarak ait olduğunu belirtirsiniz.

## <a name="implementing-the-idataservicestreamprovider-interface"></a>IDataServiceStreamProvider arabirimini uygulama

İkili veri akışlarını destekleyen bir veri hizmeti oluşturmak için, <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimini uygulamanız gerekir. Bu uygulama, veri hizmetinin ikili verileri istemciye bir akış olarak döndürmesini ve ikili verileri istemciden gönderilen akış olarak kullanmasını sağlar. Veri hizmeti, ikili verilere akış olarak erişmesi gerektiğinde bu arabirimin bir örneğini oluşturur. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Arabirim aşağıdaki üyeleri belirtir:

|Üye adı|Açıklama|
|-----------------|-----------------|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Bu yöntem, medya bağlantısı girişi silindiğinde ilgili medya kaynağını silmek için veri hizmeti tarafından çağrılır. Uygulamasını uyguladığınızda, bu yöntem sağlanan medya bağlantısı girdisiyle ilişkili medya kaynağını silen kodu içerir. <xref:System.Data.Services.Providers.IDataServiceStreamProvider>|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Bu yöntem, bir medya kaynağını akış olarak döndürmek için veri hizmeti tarafından çağrılır. Uygulamasını uyguladığınızda, bu yöntem, veri hizmeti tarafından sağlanan medya bağlantı girdisiyle ilişkili döndürülen medya kaynağına kullanılan bir akış sağlayan kodu içerir. <xref:System.Data.Services.Providers.IDataServiceStreamProvider>|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Bu yöntem, medya bağlantısı girişinin medya kaynağını istemek için kullanılan URI 'yi döndürmek için veri hizmeti tarafından çağrılır. Bu değer, ortam bağlantı girişinin içerik `src` öğesinde özniteliği oluşturmak için kullanılır ve veri akışını istemek için kullanılır. Bu yöntem döndüğünde `null`, veri hizmeti URI 'yi otomatik olarak belirler. İstemcilere, Steme sağlayıcısını kullanmadan ikili verilere doğrudan erişim sağlamanız gerektiğinde bu yöntemi kullanın.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Bu yöntem, belirtilen medya bağlantısı girdisiyle ilişkili Medya kaynağının Içerik türü değerini döndürmek için veri hizmeti tarafından çağrılır.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Bu yöntem, belirtilen varlıkla ilişkili veri akışının eTag 'i döndürmek için veri hizmeti tarafından çağrılır. Bu yöntem, ikili veriler için eşzamanlılık yönetirken kullanılır. Bu yöntem null döndürdüğünde veri hizmeti eşzamanlılık izlemez.|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Bu yöntem, istemciden gönderilen akış alınırken kullanılan akışı almak için veri hizmeti tarafından çağrılır. Uygulamasını uyguladığınızda, veri hizmetinin alınan akış verilerini yazdığı yazılabilir bir akış döndürmelidir. <xref:System.Data.Services.Providers.IDataServiceStreamProvider>|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Eklenmekte olan medya kaynağı için veri akışıyla ilişkili medya bağlantı girişi için veri hizmeti çalışma zamanının oluşturulması gereken türü temsil eden bir ad alanı nitelenmiş tür adı döndürür.|

## <a name="creating-the-streaming-data-service"></a>Akış veri hizmeti oluşturuluyor

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Çalışma zamanının <xref:System.Data.Services.Providers.IDataServiceStreamProvider> uygulamaya erişimi sağlamak için, <xref:System.IServiceProvider> oluşturduğunuz veri hizmetinin de arabirimi uygulaması gerekir. Aşağıdaki örnek, uygulayan <xref:System.IServiceProvider.GetService%2A> `PhotoServiceStreamProvider` <xref:System.Data.Services.Providers.IDataServiceStreamProvider>sınıfının bir örneğini döndürmek için yönteminin nasıl uygulanacağını gösterir.

[!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_service/cs/photodata.svc.cs#photoservicestreamingprovider)]
[!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_service/vb/photodata.svc.vb#photoservicestreamingprovider)]

Veri hizmeti oluşturma hakkında genel bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Barındırma ortamında büyük Ikili akışları etkinleştirme

Bir ASP.NET Web uygulamasında bir veri hizmeti oluşturduğunuzda, HTTP protokol uygulamasını sağlamak için Windows Communication Foundation (WCF) kullanılır. Varsayılan olarak, WCF HTTP iletilerinin boyutunu yalnızca 65K bayt olarak sınırlandırır. Veri hizmetinden büyük ikili veri akışı oluşturabilmek için, büyük ikili dosyaları etkinleştirmek ve aktarım için akışları kullanmak üzere Web uygulamasını da yapılandırmanız gerekir. Bunu yapmak için, uygulamanın Web. config dosyasının `<configuration />` öğesine aşağıdakini ekleyin:

> [!NOTE]
> Hem istek hem de <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> yanıt iletilerindeki ikili verilerin aynı şekilde ve WCF tarafından arabelleğe alınmadığından emin olmak için bir aktarım modu kullanmanız gerekir.

Daha fazla bilgi için bkz. [akış Ileti aktarımı](../../wcf/feature-details/streaming-message-transfer.md) ve [Aktarım kotaları](../../wcf/feature-details/transport-quotas.md).

Varsayılan olarak, Internet Information Services (IIS) isteklerin boyutunu 4MB olarak sınırlandırır. Veri hizmetinizin IIS üzerinde çalışırken 4 MB 'tan büyük akışları almasını sağlamak için, aşağıdaki şekilde gösterildiği gibi, `maxRequestLength` `<system.web />` yapılandırma bölümündeki [httpRuntime öğesinin (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)) özniteliğini de ayarlamanız gerekir örneğinde

## <a name="using-data-streams-in-a-client-application"></a>Istemci uygulamasında veri akışlarını kullanma

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, bu kullanıma sunulan kaynakları istemcide ikili akışlar olarak hem alıp hem de güncelleştirmenizi sağlar. Daha fazla bilgi için bkz. [Ikili verilerle çalışma](working-with-binary-data-wcf-data-services.md).

## <a name="considerations-for-working-with-a-streaming-provider"></a>Bir akış sağlayıcısıyla çalışmaya yönelik konular

Aşağıda, bir akış sağlayıcısı uyguladığınızda ve bir veri hizmetinden medya kaynaklarına eriştiğinizde dikkate alınması gereken noktalar verilmiştir.

- Medya kaynakları için BIRLEŞTIRME istekleri desteklenmez. Var olan bir varlığın medya kaynağını değiştirmek için bir PUT isteği kullanın.

- POST isteği yeni bir medya bağlantı girişi oluşturmak için kullanılamaz. Bunun yerine, yeni bir medya kaynağı oluşturmak için bir POST isteği oluşturmanız gerekir ve veri hizmeti varsayılan değerlerle yeni bir medya bağlantısı girişi oluşturur. Bu yeni varlık, sonraki bir BIRLEŞTIRME veya PUT isteği tarafından güncelleştirilemeyebilir. Ayrıca, varlık önbelleğini de göz önünde bulundurmanız ve özellik değerini POST isteğindeki başlık üst bilgisinin değerine ayarlamak gibi bir ilke oluşturmanız da gerekebilir.

- Bir post isteği alındığında, veri hizmeti medya bağlantısı girişi oluşturmak <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> için çağırmadan <xref:System.Data.Services.IUpdatable.SaveChanges%2A> önce medya kaynağını oluşturmak için çağırır.

- Uygulamasının bir<xref:System.IO.MemoryStream> nesnesi döndürmemelidir. <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> Bu tür bir akış kullandığınızda, hizmet çok büyük veri akışları aldığında bellek kaynağı sorunları oluşur.

- Aşağıda, medya kaynaklarını bir veritabanında depolarken göz önünde bulundurmanız gereken noktalar verilmiştir:

  - Medya kaynağı olan bir ikili özelliğin veri modeline dahil edilmemelidir. Bir veri modelinde kullanıma sunulan tüm özellikler bir yanıt akışındaki girişte döndürülür.

  - Büyük bir ikili akış ile performansı artırmak için, ikili verileri veritabanında depolamak üzere özel bir akış sınıfı oluşturmanızı öneririz. Bu sınıf, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> uygulamanız tarafından döndürülür ve ikili verileri öbeklerdeki veritabanına gönderir. Bir SQL Server veritabanı için, ikili veriler 1 MB 'tan büyükse veritabanına veri akışı için bir FıLESTREAM kullanmanızı öneririz.

  - Veritabanınızın, veri hizmetiniz tarafından alınacak ikili büyük akışları depolamak için tasarlandığından emin olun.

  - İstemci tek bir istekte medya kaynağı içeren bir medya bağlantısı girişi eklemek üzere bir post isteği gönderdiğinde, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> veri hizmeti yeni varlığı veritabanına eklemeden önce akışı almak için çağırılır. Bir akış sağlayıcısı uygulamasının bu veri hizmeti davranışını işleyebilmesi gerekir. İkili verileri depolamak için ayrı bir veri tablosu kullanmayı düşünün veya veri akışını varlık veritabanına eklenene kadar bir dosyada depolayın.

- <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A> ,<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, Veya<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> yöntemlerini uyguladığınızda, yöntem parametreleri olarak sağlanan ETag ve içerik türü değerlerini kullanmanız gerekir. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Sağlayıcı uygulamanızda ETag veya Content-Type üst bilgilerini ayarlamayın.

- Varsayılan olarak, istemci, öbekli bir HTTP aktarım kodlaması kullanarak büyük ikili akışlar gönderir. ASP.NET Development Server bu tür kodlamayı desteklemediğinden, büyük ikili akışları kabul etmesi gereken bir akış veri hizmetini barındırmak için bu Web sunucusunu kullanamazsınız. ASP.NET Development Server hakkında daha fazla bilgi için bkz. [Visual Studio 'Da Web sunucuları for ASP.NET Web Projects](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

<a name="versioning"></a>

## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri

Akış sağlayıcısı aşağıdaki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol sürümü oluşturma gereksinimlerine sahiptir:

- Akış sağlayıcısı, veri hizmetinin [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol ve sonraki sürümlerin sürüm 2,0 ' i desteklemesini gerektirir.

Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Özel Veri Hizmeti Sağlayıcıları](custom-data-service-providers-wcf-data-services.md)
- [İkili Verilerle Çalışma](working-with-binary-data-wcf-data-services.md)
