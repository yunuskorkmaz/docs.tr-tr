---
title: Akış özelleştirmesi (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: 17d54210d7abc16fe91fa94f39a8f85eac866088
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854189"
---
# <a name="feed-customization-wcf-data-services"></a>Akış özelleştirmesi (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]verileri bir akış olarak göstermek içinöğesinikullanır.[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]veri akışları için hem atom hem de JavaScript Nesne Gösterimi (JSON) biçimlerini destekler. Atom akışı kullandığınızda, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] varlıklar ve ilişkiler gibi verileri, HTTP iletisinin gövdesine eklenebilecek bir XML biçiminde seri hale getirmek için standart bir yöntem sağlar. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]varlıklarda ve Atom öğelerinde bulunan veriler arasında varsayılan bir varlık özelliği eşlemesini tanımlar. Daha fazla bilgi için bkz [. OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Veri hizmeti tarafından döndürülen özellik verilerinin standart akış biçimi yerine özelleştirilmiş bir biçimde serileştirilmesi için bir uygulama senaryonuz olabilir. İle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]bir varlık özelliklerinin, bir girdinin kullanılmayan öğelerine ve özniteliklerine ya da akıştaki bir girdinin özel öğelerine eşlenilmesi için bir veri akışında serileştirme ' i özelleştirebilirsiniz.  
  
> [!NOTE]
> Akış özelleştirmesi yalnızca Atom akışları için desteklenir. Döndürülen akış için JSON biçimi istendiğinde özel akışlar döndürülmez.  
  
 İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], veri modelindeki varlık türlerine öznitelikleri el ile uygulayarak bir atom yükü için alternatif bir varlık özelliği eşlemesi tanımlayabilirsiniz. Veri hizmetinin veri kaynağı sağlayıcısı, bu özniteliklerin nasıl uygulanacağını belirler.  
  
> [!IMPORTANT]
> Özel akışlar tanımladığınızda, tanımlanmış özel eşlemeleri olan tüm varlık özelliklerinin projeksiyonda dahil edildiğini garanti etmeniz gerekir. Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Entity Framework sağlayıcı ile akışları özelleştirme  
 Entity Framework sağlayıcısıyla kullanılan veri modeli. edmx dosyasında XML olarak temsil edilir. Bu durumda, özel akışları tanımlayan öznitelikler ve `EntityType` `Property` , veri modelindeki varlık türlerini ve özelliklerini temsil eden öğelerine eklenir. Bu akış özelleştirme öznitelikleri mc-csdl [\]içinde \[tanımlı değil: Entity Framework sağlayıcının veri modelini tanımlamak](https://go.microsoft.com/fwlink/?LinkId=159072)için kullandığı biçim olan kavramsal şema tanım dosyası biçimi. Bu nedenle, akış özelleştirme özniteliklerini, olarak `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`tanımlanan belirli bir şema ad alanında bildirmeniz gerekir. Aşağıdaki `Property` XML parçası `ProductName`, `Products` ,ve`UnitsInStock` özelliklerini tanımlayan varlık türünün öğelerine uygulanan akış özelleştirme özniteliklerini gösterir. `ReorderLevel`  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Bu öznitelikler `Products` varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur. `ProductName` Özelleştirilmiş veri akışında, özellik değeri hem `author` öğesinde hem de `ProductName` Özellik öğesi olarak görüntülenir ve `UnitsInStock` özelliği, kendi benzersiz ad alanı ve ile olan özel bir öğede görüntülenir öznitelik `ReorderLevel` olarak özelliği:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Daha fazla bilgi için [nasıl yapılır: Entity Framework sağlayıcı](how-to-customize-feeds-with-ef-provider-wcf-data-services.md)ile akışları özelleştirin.  
  
> [!NOTE]
> Veri modeli uzantıları Entity Desisgner tarafından desteklenmediğinden, veri modelini içeren XML dosyasını el ile değiştirmeniz gerekir. Varlık Veri Modeli araçları tarafından oluşturulan. edmx dosyası hakkında daha fazla bilgi için bkz. [. edmx dosyasına genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Özel akış öznitelikleri  
 Aşağıdaki tabloda, veri modelini tanımlayan kavramsal şema tanım diline (CSDL) ekleyebileceğiniz Özet akışları özelleştiren XML öznitelikleri gösterilmektedir. Bu öznitelikler, yansıma sağlayıcısıyla <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> kullanılan özellikleriyle eşdeğerdir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|`FC_ContentKind`|İçeriğin türünü gösterir. Aşağıdaki anahtar sözcükler, dağıtım içerik türlerini tanımlar.<br /><br /> `text:`Özellik değeri akışta metin olarak görüntülenir.<br /><br /> `html:`Özellik değeri akışta HTML olarak görüntülenir.<br /><br /> `xhtml:`Özellik değeri, akışta XML biçimli HTML olarak görüntülenir.<br /><br /> Bu anahtar sözcükler, yansıma sağlayıcısıyla kullanılan <xref:System.Data.Services.Common.SyndicationTextContentKind> numaralandırmanın değerlerine eşdeğerdir.<br /><br /> `FC_NsPrefix` Ve`FC_NsUri` öznitelikleri kullanıldığında bu öznitelik desteklenmez.<br /><br /> `xhtml` Özniteliği için bir değer belirttiğinizde, özellik değerinin düzgün biçimli xml içerdiğinden emin olmanız gerekir. `FC_ContentKind` Veri hizmeti herhangi bir dönüştürme yapılmadan değeri döndürür. Ayrıca, döndürülen XML 'deki tüm XML öğesi öneklerinde, eşlenmiş akışta tanımlanmış bir ad alanı URI 'SI ve öneki olduğundan emin olmanız gerekir.|  
|`FC_KeepInContent`|Başvurulan özellik değerinin hem akışın içerik bölümüne hem de eşlenmiş konuma dahil edileceğini gösterir. Geçerli değerler ve `true` ' `false`dir. Elde edilen akışın önceki sürümleriyle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]geriye dönük olarak uyumlu olmasını sağlamak için, değerinin akışın içerik bölümüne eklendiğinden emin olmak `true` için değerini belirtin.|  
|`FC_NsPrefix`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı öneki. Bu özniteliğin özniteliğiyle kullanılması `FC_NsUri` gerekir ve `FC_ContentKind` özniteliğiyle birlikte kullanılamaz.|  
|`FC_NsUri`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı URI 'SI. Bu özniteliğin özniteliğiyle kullanılması `FC_NsPrefix` gerekir ve `FC_ContentKind` özniteliğiyle birlikte kullanılamaz.|  
|`FC_SourcePath`|Bu akış eşleme kuralının uygulandığı varlığın özelliğinin yolu. Bu öznitelik yalnızca bir `EntityType` öğede kullanıldığında desteklenir.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Özelliği bir karmaşık türe doğrudan başvuramaz. Karmaşık türler için, özellik adlarının ters eğik çizgi (`/`) karakteriyle ayrıldığı bir yol ifadesi kullanmanız gerekir. Örneğin, bir tamsayı özelliğine `Person` `Age` ve karmaşık özelliğe sahip bir varlık türü için aşağıdaki değerlere izin verilir<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> Özellik <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> , bir boşluk veya bir özellik adında geçerli olmayan herhangi bir karakter içeren bir değere ayarlanamaz.|  
|`FC_TargetPath`|Özelliği eşlemek için sonuç olan akışın hedef öğesinin adı. Bu öğe, atom belirtimi veya özel bir öğe tarafından tanımlanan bir öğe olabilir.<br /><br /> Aşağıdaki anahtar sözcükler, bir akıştaki belirli bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] konuma işaret eden önceden tanımlanmış dağıtım hedefi yol değerleridir.<br /><br /> `SyndicationAuthorEmail:``atom:author` Öğenin `atom:email` alt öğesi.<br /><br /> `SyndicationAuthorName:``atom:author` Öğenin `atom:name` alt öğesi.<br /><br /> `SyndicationAuthorUri:``atom:author` Öğenin `atom:uri` alt öğesi.<br /><br /> `SyndicationContributorEmail:``atom:contributor` Öğenin `atom:email` alt öğesi.<br /><br /> `SyndicationContributorName:``atom:contributor` Öğenin `atom:name` alt öğesi.<br /><br /> `SyndicationContributorUri:``atom:contributor` Öğenin `atom:uri` alt öğesi.<br /><br /> `SyndicationCustomProperty:`Özel bir özellik öğesi. Özel bir öğeyle eşleme yaparken hedef, iç içe yerleştirilmiş öğelerin ters eğik çizgi (`/`) ile ayrıldığı ve öznitelikleri bir ampersan (`@`) ile belirtilen bir yol ifadesi olmalıdır. Aşağıdaki örnekte, dize `UnitsInStock/@ReorderLevel` bir özellik değerini kök girdi öğesi adlı `UnitsInStock` alt öğe üzerinde adlı `ReorderLevel` bir özniteliğe eşler.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Hedef bir özel öğe adı olduğunda, `FC_NsPrefix` ve `FC_NsUri` öznitelikleri de belirtilmelidir.<br /><br /> `SyndicationPublished:``atom:published` Öğesi.<br /><br /> `SyndicationRights:``atom:rights` Öğesi.<br /><br /> `SyndicationSummary:``atom:summary` Öğesi.<br /><br /> `SyndicationTitle:``atom:title` Öğesi.<br /><br /> `SyndicationUpdated:``atom:updated` Öğesi.<br /><br /> Bu anahtar sözcükler, yansıma sağlayıcısıyla kullanılan <xref:System.Data.Services.Common.SyndicationItemProperty> numaralandırmanın değerlerine eşdeğerdir.|  
  
> [!NOTE]
> Öznitelik adları ve değerleri büyük/küçük harfe duyarlıdır. Öznitelikler `EntityType` öğesine veya bir ya da daha fazla `Property` öğeye uygulanabilir, ancak her ikisine birden uygulanamaz.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile akışları özelleştirme  
 Yansıma sağlayıcısı kullanılarak uygulanan bir veri modeline ait akışları özelleştirmek için, veri modelindeki varlık türlerini temsil eden sınıflara <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> özniteliğin bir veya daha fazla örneğini ekleyin. <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> Sınıfının özellikleri, önceki bölümde açıklanan akış özelleştirme özniteliklerine karşılık gelir. Aşağıdaki, her iki özellik için tanımlanan özel akış eşlemesi `Order` ile türün bildirimine bir örnektir.  
  
> [!NOTE]
> Bu örneğe [ilişkin veri modeli, konusunda nasıl yapılır: Yansıma sağlayıcısını](create-a-data-service-using-rp-wcf-data-services.md)kullanarak bir veri hizmeti oluşturun.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Bu öznitelikler `Orders` varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur. Bu özelleştirilmiş `OrderId` akışta, özellik değeri yalnızca `title` öğesinin `Customer` öğesinde `entry` `author` ve özellik değeri hem öğesinde hem de `Customer` Özellik öğesi olarak görüntülenir:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Daha fazla bilgi için [nasıl yapılır: Akışları yansıma sağlayıcısıyla](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)özelleştirin.  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Özel bir veri hizmeti sağlayıcısı ile akışları özelleştirme  
 Özel veri hizmeti sağlayıcısı kullanılarak tanımlanan bir veri modeli için akış özelleştirmesi, veri modelindeki bir varlık türünü temsil <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> <xref:System.Data.Services.Providers.ResourceType> eden öğesine çağırarak bir kaynak türü için tanımlanır. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Özel akışlar kullanma  
 Uygulamanız doğrudan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış tükettiği zaman, döndürülen akıştaki özelleştirilmiş öğeleri ve öznitelikleri işleyebilmelidir. Data Service sağlayıcısından bağımsız olarak veri modelinize özel akışlar uyguladıysanız, `$metadata` uç nokta, veri hizmeti tarafından döndürülen csdl içindeki özel akış öznitelikleri olarak özel akış bilgileri döndürür. İstemci veri hizmeti sınıfları oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda, veri hizmetine yönelik isteklerin ve yanıtların doğru şekilde işleneceğini garantilemek için özelleştirilmiş akış öznitelikleri kullanılır.  
  
## <a name="feed-customization-considerations"></a>Akış özelleştirme konuları  
 Özel akış eşlemelerini tanımlarken aşağıdakileri göz önünde bulundurmanız gerekir.  
  
- İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , bir akışdaki eşlenmiş öğeleri yalnızca boşluk içerdiğinde boş olarak değerlendirir. Bu nedenle, yalnızca beyaz boşluk içeren eşlenmiş öğeler istemcide aynı boşluk ile gerçekleştirilmez. Bu alanı istemcide korumak için, değerini `KeepInContext` akış eşleme özniteliğinde olarak `true` ayarlamanız gerekir.  
  
## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  
 Akış özelleştirmesi aşağıdaki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol sürümü oluşturma gereksinimlerine sahiptir:  
  
- Akış özelleştirmesi hem istemci hem de veri hizmetinin [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol ve sonraki sürümlerin 2,0 sürümünü desteklemesini gerektirir.  
  
 Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
