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
ms.openlocfilehash: 495ce51a70e8738746d62eb032d23cc0bbcd8083
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545891"
---
# <a name="feed-customization-wcf-data-services"></a>Akış özelleştirmesi (WCF Veri Hizmetleri)
WCF Veri Hizmetleri verileri akış olarak göstermek için açık veri Protokolü 'Nü (OData) kullanır. OData, veri akışları için hem atom hem de JavaScript Nesne Gösterimi (JSON) biçimlerini destekler. Atom akışı kullandığınızda OData, varlıkları ve ilişkileri gibi verileri, HTTP iletisinin gövdesine eklenebilecek bir XML biçiminde seri hale getirmek için standart bir yöntem sağlar. OData, varlıklarda ve Atom öğelerinde bulunan veriler arasında varsayılan bir varlık özelliği eşlemesini tanımlar. Daha fazla bilgi için bkz. [OData: Atom biçimi](https://www.odata.org/documentation/odata-version-2-0/atom-format/).  
  
 Veri hizmeti tarafından döndürülen özellik verilerinin standart akış biçimi yerine özelleştirilmiş bir biçimde serileştirilmesi için bir uygulama senaryonuz olabilir. OData ile bir varlık özelliklerinin, bir girdinin kullanılmayan öğelerine ve özniteliklerine ya da akıştaki bir girdinin özel öğelerine eşlenilmesi için bir veri akışında serileştirme ' i özelleştirebilirsiniz.  
  
> [!NOTE]
> Akış özelleştirmesi yalnızca Atom akışları için desteklenir. Döndürülen akış için JSON biçimi istendiğinde özel akışlar döndürülmez.  
  
 WCF Veri Hizmetleri ile, veri modelindeki varlık türlerine öznitelikleri el ile uygulayarak atom yükünün alternatif varlık özelliği eşlemesini tanımlayabilirsiniz. Veri hizmetinin veri kaynağı sağlayıcısı, bu özniteliklerin nasıl uygulanacağını belirler.  
  
> [!IMPORTANT]
> Özel akışlar tanımladığınızda, tanımlanmış özel eşlemeleri olan tüm varlık özelliklerinin projeksiyonda dahil edildiğini garanti etmeniz gerekir. Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Entity Framework sağlayıcı ile akışları özelleştirme  
 Entity Framework sağlayıcısıyla kullanılan veri modeli. edmx dosyasında XML olarak temsil edilir. Bu durumda, özel akışları tanımlayan öznitelikler `EntityType` ve, `Property` veri modelindeki varlık türlerini ve özelliklerini temsil eden öğelerine eklenir. Bu akış özelleştirme öznitelikleri, [ \[ mc-csdl \] : kavramsal şema tanımı dosya biçiminde](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12)tanımlanmamıştır, bu biçim Entity Framework sağlayıcının veri modelini tanımlamak için kullandığı biçimdir. Bu nedenle, akış özelleştirme özniteliklerini, olarak tanımlanan belirli bir şema ad alanında bildirmeniz gerekir `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"` . Aşağıdaki XML parçası `Property` `Products` ,, ve özelliklerini tanımlayan varlık türünün öğelerine uygulanan akış özelleştirme özniteliklerini gösterir `ProductName` `ReorderLevel` `UnitsInStock` .  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Bu öznitelikler varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur `Products` . Özelleştirilmiş veri akışında, `ProductName` özellik değeri hem öğesinde hem de `author` Özellik öğesinde görüntülenir ve özellik, `ProductName` `UnitsInStock` kendi benzersiz ad alanı olan ve `ReorderLevel` özelliği bir öznitelik olarak olan özel bir öğede görüntülenir:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Entity Framework sağlayıcı Ile akışları özelleştirme](how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
> Veri modeli uzantıları Entity Desisgner tarafından desteklenmediğinden, veri modelini içeren XML dosyasını el ile değiştirmeniz gerekir. Varlık Veri Modeli araçları tarafından oluşturulan. edmx dosyası hakkında daha fazla bilgi için bkz. [. edmx dosyasına genel bakış (Entity Framework)](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Özel akış öznitelikleri  
 Aşağıdaki tabloda, veri modelini tanımlayan kavramsal şema tanım diline (CSDL) ekleyebileceğiniz Özet akışları özelleştiren XML öznitelikleri gösterilmektedir. Bu öznitelikler, <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> yansıma sağlayıcısıyla kullanılan özellikleriyle eşdeğerdir.  
  
|Öznitelik adı|Description|  
|--------------------|-----------------|  
|`FC_ContentKind`|İçeriğin türünü gösterir. Aşağıdaki anahtar sözcükler, dağıtım içerik türlerini tanımlar.<br /><br /> `text:` Özellik değeri akışta metin olarak görüntülenir.<br /><br /> `html:` Özellik değeri akışta HTML olarak görüntülenir.<br /><br /> `xhtml:` Özellik değeri, akışta XML biçimli HTML olarak görüntülenir.<br /><br /> Bu anahtar sözcükler, <xref:System.Data.Services.Common.SyndicationTextContentKind> yansıma sağlayıcısıyla kullanılan numaralandırmanın değerlerine eşdeğerdir.<br /><br /> `FC_NsPrefix`Ve öznitelikleri kullanıldığında bu öznitelik desteklenmez `FC_NsUri` .<br /><br /> Özniteliği için bir değer belirttiğinizde `xhtml` `FC_ContentKind` , özellik değerinin düzgün biçimli xml içerdiğinden emin olmanız gerekir. Veri hizmeti herhangi bir dönüştürme yapılmadan değeri döndürür. Ayrıca, döndürülen XML 'deki tüm XML öğesi öneklerinde, eşlenmiş akışta tanımlanmış bir ad alanı URI 'SI ve öneki olduğundan emin olmanız gerekir.|  
|`FC_KeepInContent`|Başvurulan özellik değerinin hem akışın içerik bölümüne hem de eşlenmiş konuma dahil edileceğini gösterir. Geçerli değerler `true` ve ' dir `false` . Elde edilen akışı daha önceki WCF Veri Hizmetleri sürümleriyle uyumlu hale getirmek için, değerin `true` akışın içerik bölümüne eklendiğinden emin olmak için değerini belirtin.|  
|`FC_NsPrefix`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı öneki. Bu özniteliğin özniteliğiyle kullanılması gerekir `FC_NsUri` ve özniteliğiyle birlikte kullanılamaz `FC_ContentKind` .|  
|`FC_NsUri`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı URI 'SI. Bu özniteliğin özniteliğiyle kullanılması gerekir `FC_NsPrefix` ve özniteliğiyle birlikte kullanılamaz `FC_ContentKind` .|  
|`FC_SourcePath`|Bu akış eşleme kuralının uygulandığı varlığın özelliğinin yolu. Bu öznitelik yalnızca bir öğede kullanıldığında desteklenir `EntityType` .<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A>Özelliği bir karmaşık türe doğrudan başvuramaz. Karmaşık türler için, özellik adlarının ters eğik çizgi () karakteriyle ayrıldığı bir yol ifadesi kullanmanız gerekir `/` . Örneğin, bir `Person` tamsayı özelliğine `Age` ve karmaşık özelliğe sahip bir varlık türü için aşağıdaki değerlere izin verilir<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> Özellik, bir <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> boşluk veya bir özellik adında geçerli olmayan herhangi bir karakter içeren bir değere ayarlanamaz.|  
|`FC_TargetPath`|Özelliği eşlemek için sonuç olan akışın hedef öğesinin adı. Bu öğe, atom belirtimi veya özel bir öğe tarafından tanımlanan bir öğe olabilir.<br /><br /> Aşağıdaki anahtar sözcükler, bir OData akışındaki belirli bir konuma işaret eden önceden tanımlanmış dağıtım hedef yolu değerleridir.<br /><br /> `SyndicationAuthorEmail:``atom:email`Öğenin alt öğesi `atom:author` .<br /><br /> `SyndicationAuthorName:``atom:name`Öğenin alt öğesi `atom:author` .<br /><br /> `SyndicationAuthorUri:``atom:uri`Öğenin alt öğesi `atom:author` .<br /><br /> `SyndicationContributorEmail:``atom:email`Öğenin alt öğesi `atom:contributor` .<br /><br /> `SyndicationContributorName:``atom:name`Öğenin alt öğesi `atom:contributor` .<br /><br /> `SyndicationContributorUri:``atom:uri`Öğenin alt öğesi `atom:contributor` .<br /><br /> `SyndicationCustomProperty:` Özel bir özellik öğesi. Özel bir öğeyle eşleme yaparken hedef, iç içe yerleştirilmiş öğelerin ters eğik çizgi () ile ayrıldığı `/` ve öznitelikleri bir ampersan () ile belirtilen bir yol ifadesi olmalıdır `@` . Aşağıdaki örnekte, dize `UnitsInStock/@ReorderLevel` bir özellik değerini `ReorderLevel` `UnitsInStock` kök girdi öğesi adlı alt öğe üzerinde adlı bir özniteliğe eşler.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Hedef bir özel öğe adı olduğunda, `FC_NsPrefix` ve `FC_NsUri` öznitelikleri de belirtilmelidir.<br /><br /> `SyndicationPublished:``atom:published`Öğesi.<br /><br /> `SyndicationRights:``atom:rights`Öğesi.<br /><br /> `SyndicationSummary:``atom:summary`Öğesi.<br /><br /> `SyndicationTitle:``atom:title`Öğesi.<br /><br /> `SyndicationUpdated:``atom:updated`Öğesi.<br /><br /> Bu anahtar sözcükler, <xref:System.Data.Services.Common.SyndicationItemProperty> yansıma sağlayıcısıyla kullanılan numaralandırmanın değerlerine eşdeğerdir.|  
  
> [!NOTE]
> Öznitelik adları ve değerleri büyük/küçük harfe duyarlıdır. Öznitelikler `EntityType` öğesine veya bir ya da daha fazla öğeye uygulanabilir `Property` , ancak her ikisine birden uygulanamaz.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile akışları özelleştirme  
 Yansıma sağlayıcısı kullanılarak uygulanan bir veri modeline ait akışları özelleştirmek için, <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> veri modelindeki varlık türlerini temsil eden sınıflara özniteliğin bir veya daha fazla örneğini ekleyin. Sınıfının özellikleri, <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> önceki bölümde açıklanan akış özelleştirme özniteliklerine karşılık gelir. Aşağıdaki, `Order` her iki özellik için tanımlanan özel akış eşlemesi ile türün bildirimine bir örnektir.  
  
> [!NOTE]
> Bu örneğe ilişkin veri modeli, [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md)konusunda tanımlanmıştır.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Bu öznitelikler varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur `Orders` . Bu özelleştirilmiş akışta, `OrderId` özellik değeri yalnızca öğesinin `title` öğesinde `entry` ve `Customer` özellik değeri hem öğesinde hem de `author` `Customer` özellik öğesi olarak görüntülenir:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: yansıma sağlayıcısı Ile akışları özelleştirme](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Özel bir veri hizmeti sağlayıcısı ile akışları özelleştirme  
 Özel veri hizmeti sağlayıcısı kullanılarak tanımlanan bir veri modeli için akış özelleştirmesi, <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> <xref:System.Data.Services.Providers.ResourceType> veri modelindeki bir varlık türünü temsil eden öğesine çağırarak bir kaynak türü için tanımlanır. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Özel akışlar kullanma  
 Uygulamanız bir OData akışını doğrudan tükettiği zaman, döndürülen akıştaki özelleştirilmiş öğeleri ve öznitelikleri işleyebilmelidir. Data Service sağlayıcısından bağımsız olarak veri modelinize özel akışlar uyguladıysanız, `$metadata` uç nokta, veri hizmeti tarafından döndürülen csdl içindeki özel akış öznitelikleri olarak özel akış bilgileri döndürür. İstemci veri hizmeti sınıfları oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya [datasvcutil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda, veri hizmetine yönelik isteklerin ve yanıtların doğru şekilde işleneceğini garantilemek için özelleştirilmiş akış öznitelikleri kullanılır.  
  
## <a name="feed-customization-considerations"></a>Akış özelleştirme konuları  
 Özel akış eşlemelerini tanımlarken aşağıdakileri göz önünde bulundurmanız gerekir.  
  
- WCF Veri Hizmetleri istemcisi, bir akışdaki eşlenmiş öğeleri yalnızca boşluk içerdiğinde boş olarak değerlendirir. Bu nedenle, yalnızca beyaz boşluk içeren eşlenmiş öğeler istemcide aynı boşluk ile gerçekleştirilmez. Bu alanı istemcide korumak için, değerini `KeepInContext` `true` akış eşleme özniteliğinde olarak ayarlamanız gerekir.  
  
## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  
 Akış özelleştirmesi aşağıdaki OData protokol sürümü oluşturma gereksinimlerine sahiptir:  
  
- Akış özelleştirmesi hem istemci hem de veri hizmetinin OData protokolünün ve sonraki sürümlerinin 2,0 sürümünü desteklemesini gerektirir.  
  
 Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
