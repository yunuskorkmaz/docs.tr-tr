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
ms.openlocfilehash: d65ea58bc2e98ab2607ce105b496ac0a870362b0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="streaming-provider-wcf-data-services"></a>Akış sağlayıcısı (WCF Veri Hizmetleri)
Veri Hizmeti ikili büyük nesne veri getirebilir. Bu ikili verileri, video ve ses akışları, görüntüler, belge dosyaları veya diğer ikili medya türleri temsil edebilir. Bir veya daha fazla ikili özelliklerinin bir varlık veri modeli içerir, bu ikili veri akışı yanıt girişi içinde base-64 olarak kodlanmış veri hizmeti döndürür. Yükleme ve bu şekilde büyük ikili verileri seri hale getirme performansını etkileyebilir çünkü [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] ait olduğu varlık bağımsız ikili veri almak için bir mekanizma tanımlar. Bu, bir veya daha fazla veri akışlara varlıktan ikili veri ayırarak gerçekleştirilir.  
  
-   Medya kaynağı - video, ses, görüntü veya diğer medya kaynak akışı türü gibi bir varlığa ait ikili veriler.  
  
-   Medya girdisi - ilgili medya kaynak akışı başvuruyor bir varlık bağlantısı.  
  
 İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir akış veri sağlayıcısı uygulayarak bir ikili kaynak akışı tanımlayın. Akış sağlayıcısı uygulaması belirli bir varlık olarak ilişkili medya kaynak akışı ile veri hizmeti sağlayan bir <xref:System.IO.Stream> nesnesi. Bu uygulama kabul edin ve ortam kaynakları HTTP üzerinden belirtilen MIME türünün ikili veri akışları olarak döndürmek veri hizmeti sağlar.  
  
 İkili verileri akış desteklemek için veri hizmeti yapılandırma aşağıdakileri gerektirir:  
  
1.  Bir medya bağlantısı gibi giriş veri modelindeki bir veya daha fazla varlık özniteliği. Bu varlıklar akışını ikili veri içermemesi gerekir. İkili özelliklerinin bir varlık hiçbirini her zaman girişi base-64 kodlu ikili döndürülür.  
  
2.  T:System.Data.Services.Providers.IDataServiceStreamProvider arabirimini uygular.  
  
3.  Arabirimini uygulayan bir veri hizmeti tanımlamak <xref:System.IServiceProvider> arabirimi. Veri hizmeti kullanan <xref:System.IServiceProvider.GetService%2A> akış veri sağlayıcı uygulaması erişmek için uygulama. Bu yöntem, uygun akış sağlayıcı uygulaması döndürür.  
  
4.  Web uygulama yapılandırmasında büyük ileti akışları etkinleştirin.  
  
5.  Sunucuda veya bir veri kaynağında ikili kaynaklarına erişimi etkinleştirme.  
  
 Bu konudaki örnekler ayrıntılı post olarak ele alınmıştır fotoğraf hizmet akış bir örneği temel alarak [Veri Hizmetleri Akış sağlayıcısı serisi: bir akış sağlayıcı (Kısım 1) uygulama](http://go.microsoft.com/fwlink/?LinkID=198989). Bu örnek hizmeti için kaynak kodunu kullanılabilir [akış fotoğraf veri hizmeti örnek sayfası](http://go.microsoft.com/fwlink/?LinkID=198988) MSDN kod Galerisi'nden üzerinde.  
  
## <a name="defining-a-media-link-entry-in-the-data-model"></a>Veri modelinde Media Link Entry tanımlama  
 Veri kaynağı sağlayıcısı bir varlık veri modeli medya bağlantısı girdi olarak tanımlanır şeklini belirler.  
  
 **Entity Framework Sağlayıcısı**  
 Bir varlık bir medya bağlantısı girişinin olduğunu belirtmek için ekleme `HasStream` özniteliği aşağıdaki örnekte olduğu gibi kavramsal modelde varlık türü tanımı:  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Ad alanı da eklemelisiniz `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` varlık veya veri modeli tanımlayan .edmx veya .csdl dosyası kök.  
  
 Bir örnek kullanan bir veri hizmeti için [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı ve bir medya kaynağı gösterir gönderiye bakın [Veri Hizmetleri Akış sağlayıcısı serisi: bir akış sağlayıcı (Kısım 1) uygulama](http://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Yansıma Sağlayıcısı**  
 Bir varlığa bir medya bağlantısı girişinin olduğunu belirtmek için ekleme <xref:System.Data.Services.Common.HasStreamAttribute> sınıfına yansıma sağlayıcısında varlık türünü tanımlar.  
  
 **Özel veri hizmet sağlayıcısı**  
 Özel hizmet sağlayıcıları kullanırken, uygulamanız <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> veri hizmetiniz için meta verileri tanımlamak için arabirim. Daha fazla bilgi için bkz: [özel veri hizmeti sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md). Bir ikili kaynak akışı ait olduğunu belirten bir <xref:System.Data.Services.Providers.ResourceType> ayarlayarak <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> özelliğine `true` üzerinde <xref:System.Data.Services.Providers.ResourceType> temsil eden bir medya bağlantısı girişi varlık türü.  
  
## <a name="implementing-the-idataservicestreamprovider-interface"></a>IDataServiceStreamProvider arabirimi uygulama  
 İkili veri akışlarını destekleyen bir veri hizmeti oluşturmak için uygulamanız gereken <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi. Bu uygulama ikili veri akışı olarak istemciye Döndür ve istemciden gönderilen bir akış olarak ikili verileri kullanmak veri hizmeti sağlar. İkili veri akışı olarak erişmesi gereken her veri hizmeti bu arabiriminin bir örneğini oluşturur. <xref:System.Data.Services.Providers.IDataServiceStreamProvider> Arabirimi aşağıdaki üyeleri belirtir:  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Bu yöntem, medya bağlantısı girdisini silindiğinde karşılık gelen medya kaynağı silmek için veri hizmeti tarafından çağrılır. Ne zaman uygulamanız <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, bu yöntem sağlanan medya bağlantısı girişle ilişkili medya kaynağı siler kodunu içerir.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Bu yöntem, bir medya kaynağı bir akış olarak döndürmek için veri hizmeti tarafından çağrılır. Ne zaman uygulamanız <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, bu yöntem, sağlanan media link entry ile ilişkili dönüş medya kaynağı için veri hizmeti tarafından kullanılan bir akış sunar kodunu içerir.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Bu yöntem, media link entry medya kaynağı istemek için kullanılan URI döndürmek için veri hizmeti tarafından çağrılır. Bu değer oluşturmak için kullanılan `src` özniteliği media link entry ve içerik öğesindeki veri akışı istemek için kullanılır. Bu yöntem döndürdüğünde `null`, veri hizmeti otomatik olarak URI belirler. Akış sağlayıcısı kullanmadan istemcileri ikili veriler doğrudan erişim sağlamak istediğinizde bu yöntemi kullanın.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Bu yöntem, belirtilen media link entry ile ilişkili medya kaynağı Content-Type değerini döndürmek için veri hizmeti tarafından çağrılır.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Bu yöntem, belirtilen varlık ile ilişkili veri akışının eTag döndürmek için veri hizmeti tarafından çağrılır. İkili veriler için eşzamanlılık yönetirken bu yöntem kullanılır. Bu yöntem null değeri döndürür, veri hizmeti eşzamanlılık izlemez.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Bu yöntem, akış alma istemciden gönderildiğinde, kullanılan akış almak için veri hizmeti tarafından çağrılır. Ne zaman uygulamanız <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, veri hizmeti alınan yazma veri akışı yazılabilir bir akış döndürmesi gerekir.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Veri Hizmeti çalışma zamanı eklenmekte medya kaynağı için veri akışı ile ilişkilendirilmiş media link entry oluşturmalıdır türünü temsil eden bir ad alanı nitelenmiş tür adını döndürür.|  
  
## <a name="creating-the-streaming-data-service"></a>Akış veri hizmeti oluşturma  
 Sağlamak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çalışma zamanı erişimi <xref:System.Data.Services.Providers.IDataServiceStreamProvider> gerekir oluşturduğunuz veri hizmeti uygulaması, ayrıca uygulama <xref:System.IServiceProvider> arabirimi. Aşağıdaki örnekte nasıl uygulanacağını gösterir <xref:System.IServiceProvider.GetService%2A> örneği döndürülecek yöntemi `PhotoServiceStreamProvider` uygulayan sınıf <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Veri hizmeti oluşturma hakkında genel bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>Barındırma ortamında büyük ikili akışlar etkinleştirme  
 Bir veri hizmeti oluşturduğunuzda bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması, Windows Communication Foundation (WCF) HTTP protokolü uygulamasını sağlamak için kullanılır. Varsayılan olarak, WCF HTTP iletileri yalnızca 65 K bayt boyutu sınırlar. Büyük ikili veri akışı için ve veri hizmeti kullanabilmek için Web uygulaması büyük ikili dosyaları etkinleştirmek ve akışlar aktarımı için kullanmak için yapılandırmanız gerekir. Bunu yapmak için aşağıdakileri ekleyin `<configuration />` uygulamanın Web.config dosyasının öğesi:  
  
  
  
> [!NOTE]
>  Kullanmalısınız bir <xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType> aktarım modu istek ve yanıt iletilerinde ikili veri akışı ve WCF tarafından arabelleğe değil olduğundan emin olun.  
  
 Daha fazla bilgi için bkz: [ileti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) ve [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Varsayılan olarak, Internet Information Services (IIS) 4 MB isteklerine boyutunu de sınırlar. IIS üzerinde çalışan akışları 4 MB'den daha büyük almak, veri hizmeti etkinleştirmek için de ayarlamalısınız `maxRequestLength` özniteliği [httpRuntime öğesi (ASP.NET Ayarlar Şeması)](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369) içinde `<system.web />` yapılandırma bölümü olarak Aşağıdaki örnekte gösterilen:  
  
  
  
## <a name="using-data-streams-in-a-client-application"></a>Bir istemci uygulamasında veri akışlarını kullanma  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci Kitaplığı hem almak ve ikili akışlar istemcide olarak sunulan bu kaynakları güncelleştirmenize olanak sağlar. Daha fazla bilgi için bkz: [ikili verileri ile çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="considerations-for-working-with-a-streaming-provider"></a>Bir akış sağlayıcı ile çalışma konuları  
 Akış sağlayıcısı ne zaman uygulamak ve veri hizmetinden veri medya kaynaklarına eriştiğinizde göz önünde bulundurmanız gerekenler şunlardır:  
  
-   MERGE isteklerini medya kaynaklar için desteklenmez. Var olan bir varlığın medya kaynağı değiştirmek için bir PUT İsteği kullanın.  
  
-   Bir POST isteği bağlantı girişi yeni bir ortam oluşturmak için kullanılamaz. Bunun yerine, yeni bir medya kaynağı oluşturmak için bir POST isteği yayımlamanız gerekir ve veri hizmeti yeni bir ortam bağlantı girdisini varsayılan değerlerle oluşturur. Bu yeni bir varlık, bir sonraki birleştirme veya PUT isteği tarafından güncelleştirilebilir. Ayrıca, varlık önbelleğe alma göz önünde bulundurun ve özellik değeri için POST isteğinde başlık üstbilgisi değerini ayarlama gibi disposer, güncelleştirmelerinin olması.  
  
-   Bir POST isteği alındığında, veri çağrıları hizmeti <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> önceki medya kaynağı oluşturmak için çağırdığı <xref:System.Data.Services.IUpdatable.SaveChanges%2A> bağlantı girdisini medyayı oluşturmak için.  
  
-   Uygulaması <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> değil döndürmelidir bir <xref:System.IO.MemoryStream> nesnesi. Bu tür bir akış kullandığınızda, hizmeti çok büyük veri akışlarını aldığında bellek kaynağı sorunları ortaya çıkar.  
  
-   Ortam kaynakları bir veritabanında saklarken göz önünde bulundurmanız gerekenler şunlardır:  
  
    -   Bir medya kaynağı olan bir ikili özellik veri modelinde eklenmemelidir. Bir veri modeli kullanıma sunulan tüm özellikler akış yanıt girdisinde döndürülür.  
  
    -   Büyük bir ikili akış performansınızı artırmak için ikili veri veritabanında depolamak için bir özel akış sınıf oluşturmanızı öneririz. Bu sınıf tarafından döndürülen, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> uygulama ve ikili veri öbekleri veritabanına gönderir. SQL Server veritabanı için ikili veriler 1 MB'den büyük olduğunda bir FILESTREAM veri akışı için veritabanına kullanmanızı öneririz.  
  
    -   Veritabanınız, veri hizmeti tarafından alınabilmesi için ikili büyük akış depolamak için tasarlanmıştır emin olun.  
  
    -   Bir istemci tek bir istekte bir medya kaynağı ile media bağlantı girdisini eklemek için bir POST isteği gönderdiğinde <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> veri hizmeti veritabanına yeni bir varlık ekler önce akış elde etmek için çağrılır. Bir akış sağlayıcı uygulaması bu verileri hizmet davranışı kaldırabilir olmalıdır. İkili veriler veya varlık sonra kadar dosyasındaki veri akışı veritabanına eklenen deposunda depolamak için ayrı veri tablosu kullanmayı düşünün.  
  
-   Ne zaman uygulamanız <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>, veya <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> yöntemlerini kullanmanız gerekir eTag ve sağlanan Content-Type değerleri yöntem parametreleri. ETag veya Content-Type üst bilgilerinde ayarlı değil, <xref:System.Data.Services.Providers.IDataServiceStreamProvider> sağlayıcısı uygulaması.  
  
-   Varsayılan olarak, istemci bir öbekli HTTP Transfer-Encoding kullanarak büyük ikili akışlar gönderir. Çünkü [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] büyük ikili akışlar kabul etmelisiniz akış bir veri hizmeti barındırmak için bu Web sunucusu kullanamazsınız, geliştirme sunucusu, bu tür kodlama desteklemiyor. Daha fazla bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] geliştirme sunucusu bkz [ASP.NET Web projeleri için Visual Studio'da Web sunucuları](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  
 Aşağıdaki Akış sağlayıcısı sahip [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] iletişim kuralı sürüm gereksinimleri:  
  
-   Akış sağlayıcısı, veri hizmeti sürüm 2.0 desteği gerektirir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü ve sonraki sürümler.  
  
 Daha fazla bilgi için bkz: [veri hizmeti sürüm](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetleri Sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Özel Veri Hizmeti Sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)  
 [İkili Verilerle Çalışma](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
