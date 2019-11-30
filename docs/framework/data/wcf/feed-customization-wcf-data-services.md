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
ms.openlocfilehash: 08df16be9df6d55ab9f1426e205e56d9609ce72e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569217"
---
# <a name="feed-customization-wcf-data-services"></a>Akış özelleştirmesi (WCF Veri Hizmetleri)
WCF Veri Hizmetleri verileri akış olarak göstermek için açık veri Protokolü 'Nü (OData) kullanır. OData, veri akışları için hem atom hem de JavaScript Nesne Gösterimi (JSON) biçimlerini destekler. Atom akışı kullandığınızda OData, varlıkları ve ilişkileri gibi verileri, HTTP iletisinin gövdesine eklenebilecek bir XML biçiminde seri hale getirmek için standart bir yöntem sağlar. OData, varlıklarda ve Atom öğelerinde bulunan veriler arasında varsayılan bir varlık özelliği eşlemesini tanımlar. Daha fazla bilgi için bkz. [OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Veri hizmeti tarafından döndürülen özellik verilerinin standart akış biçimi yerine özelleştirilmiş bir biçimde serileştirilmesi için bir uygulama senaryonuz olabilir. OData ile bir varlık özelliklerinin, bir girdinin kullanılmayan öğelerine ve özniteliklerine ya da akıştaki bir girdinin özel öğelerine eşlenilmesi için bir veri akışında serileştirme ' i özelleştirebilirsiniz.  
  
> [!NOTE]
> Akış özelleştirmesi yalnızca Atom akışları için desteklenir. Döndürülen akış için JSON biçimi istendiğinde özel akışlar döndürülmez.  
  
 WCF Veri Hizmetleri ile, veri modelindeki varlık türlerine öznitelikleri el ile uygulayarak atom yükünün alternatif varlık özelliği eşlemesini tanımlayabilirsiniz. Veri hizmetinin veri kaynağı sağlayıcısı, bu özniteliklerin nasıl uygulanacağını belirler.  
  
> [!IMPORTANT]
> Özel akışlar tanımladığınızda, tanımlanmış özel eşlemeleri olan tüm varlık özelliklerinin projeksiyonda dahil edildiğini garanti etmeniz gerekir. Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Entity Framework sağlayıcı ile akışları özelleştirme  
 Entity Framework sağlayıcısıyla kullanılan veri modeli. edmx dosyasında XML olarak temsil edilir. Bu durumda, özel akışları tanımlayan öznitelikler, veri modelindeki varlık türlerini ve özelliklerini temsil eden `EntityType` ve `Property` öğelerine eklenir. Bu akış özelleştirme öznitelikleri [\[mc-CSDL\]: kavramsal şema tanımı dosya biçiminde](https://go.microsoft.com/fwlink/?LinkId=159072)tanımlanmamıştır, bu biçim Entity Framework sağlayıcının veri modelini tanımlamak için kullandığı biçimdir. Bu nedenle, akış özelleştirme özniteliklerini, `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`olarak tanımlanan belirli bir şema ad alanında bildirmeniz gerekir. Aşağıdaki XML parçası `ProductName`, `ReorderLevel`ve `UnitsInStock` özelliklerini tanımlayan `Products` varlık türünün `Property` öğelerine uygulanan akış özelleştirme özniteliklerini gösterir.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Bu öznitelikler `Products` varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur. Özelleştirilmiş veri akışında `ProductName` Özellik değeri hem `author` öğesinde hem de `ProductName` Özellik öğesinde ve `UnitsInStock` özelliği, kendi benzersiz ad alanına sahip olan ve bir öznitelik olarak `ReorderLevel` özelliği olan özel bir öğede görüntülenir:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Entity Framework sağlayıcı Ile akışları özelleştirme](how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
> Veri modeli uzantıları Entity Desisgner tarafından desteklenmediğinden, veri modelini içeren XML dosyasını el ile değiştirmeniz gerekir. Varlık Veri Modeli araçları tarafından oluşturulan. edmx dosyası hakkında daha fazla bilgi için bkz. [. edmx dosyasına genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Özel akış öznitelikleri  
 Aşağıdaki tabloda, veri modelini tanımlayan kavramsal şema tanım diline (CSDL) ekleyebileceğiniz Özet akışları özelleştiren XML öznitelikleri gösterilmektedir. Bu öznitelikler, yansıma sağlayıcısıyla kullanılan <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> özellikleriyle eşdeğerdir.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|`FC_ContentKind`|İçeriğin türünü gösterir. Aşağıdaki anahtar sözcükler, dağıtım içerik türlerini tanımlar.<br /><br /> `text:` Özellik değeri akışta metin olarak görüntülenir.<br /><br /> `html:` Özellik değeri akışta HTML olarak görüntülenir.<br /><br /> `xhtml:` Özellik değeri akışta XML biçimli HTML olarak görüntülenir.<br /><br /> Bu anahtar sözcükler, yansıma sağlayıcısıyla kullanılan <xref:System.Data.Services.Common.SyndicationTextContentKind> sabit listesi değerlerine eşdeğerdir.<br /><br /> `FC_NsPrefix` ve `FC_NsUri` öznitelikleri kullanıldığında bu öznitelik desteklenmez.<br /><br /> `FC_ContentKind` özniteliği için bir `xhtml` değeri belirttiğinizde, özellik değerinin düzgün biçimlendirildiğinden XML içerdiğinden emin olmanız gerekir. Veri hizmeti herhangi bir dönüştürme yapılmadan değeri döndürür. Ayrıca, döndürülen XML 'deki tüm XML öğesi öneklerinde, eşlenmiş akışta tanımlanmış bir ad alanı URI 'SI ve öneki olduğundan emin olmanız gerekir.|  
|`FC_KeepInContent`|Başvurulan özellik değerinin hem akışın içerik bölümüne hem de eşlenmiş konuma dahil edileceğini gösterir. Geçerli değerler `true` ve `false`. Elde edilen akışı daha önceki WCF Veri Hizmetleri sürümleriyle uyumlu hale getirmek için, değerin akışın içerik bölümüne eklendiğinden emin olmak için bir `true` değeri belirtin.|  
|`FC_NsPrefix`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı öneki. Bu öznitelik `FC_NsUri` özniteliğiyle birlikte kullanılmalıdır ve `FC_ContentKind` özniteliğiyle birlikte kullanılamaz.|  
|`FC_NsUri`|Bir dağıtım olmayan eşlemede XML öğesinin ad alanı URI 'SI. Bu öznitelik `FC_NsPrefix` özniteliğiyle birlikte kullanılmalıdır ve `FC_ContentKind` özniteliğiyle birlikte kullanılamaz.|  
|`FC_SourcePath`|Bu akış eşleme kuralının uygulandığı varlığın özelliğinin yolu. Bu öznitelik yalnızca bir `EntityType` öğesinde kullanıldığında desteklenir.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> özelliği bir karmaşık türe doğrudan başvuramaz. Karmaşık türler için, özellik adlarının ters eğik çizgi (`/`) karakteriyle ayrıldığı bir yol ifadesi kullanmanız gerekir. Örneğin, bir tamsayı özelliği `Age` ve karmaşık bir özellik ile `Person` varlık türü için aşağıdaki değerlere izin verilir<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> özelliği, bir boşluk veya bir özellik adında geçerli olmayan herhangi bir karakter içeren bir değere ayarlanamaz.|  
|`FC_TargetPath`|Özelliği eşlemek için sonuç olan akışın hedef öğesinin adı. Bu öğe, atom belirtimi veya özel bir öğe tarafından tanımlanan bir öğe olabilir.<br /><br /> Aşağıdaki anahtar sözcükler, bir OData akışındaki belirli bir konuma işaret eden önceden tanımlanmış dağıtım hedef yolu değerleridir.<br /><br /> `atom:author` öğesinin `atom:email` alt öğesi `SyndicationAuthorEmail:`.<br /><br /> `atom:author` öğesinin `atom:name` alt öğesi `SyndicationAuthorName:`.<br /><br /> `atom:author` öğesinin `atom:uri` alt öğesi `SyndicationAuthorUri:`.<br /><br /> `atom:contributor` öğesinin `atom:email` alt öğesi `SyndicationContributorEmail:`.<br /><br /> `atom:contributor` öğesinin `atom:name` alt öğesi `SyndicationContributorName:`.<br /><br /> `atom:contributor` öğesinin `atom:uri` alt öğesi `SyndicationContributorUri:`.<br /><br /> özel bir özellik öğesi `SyndicationCustomProperty:`. Özel bir öğeyle eşleme yaparken hedef, iç içe yerleştirilmiş öğelerin ters eğik çizgiyle (`/`) ayrıldığı ve özniteliklerin bir ampersan (`@`) ile belirtildiği bir yol ifadesi olmalıdır. Aşağıdaki örnekte, dize `UnitsInStock/@ReorderLevel` bir özellik değerini kök giriş öğesinin `UnitsInStock` adlı alt öğe üzerinde `ReorderLevel` adlı bir özniteliğe eşler.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Hedef bir özel öğe adı olduğunda, `FC_NsPrefix` ve `FC_NsUri` özniteliklerinin de belirtilmesi gerekir.<br /><br /> `atom:published` öğesi `SyndicationPublished:`.<br /><br /> `atom:rights` öğesi `SyndicationRights:`.<br /><br /> `atom:summary` öğesi `SyndicationSummary:`.<br /><br /> `atom:title` öğesi `SyndicationTitle:`.<br /><br /> `atom:updated` öğesi `SyndicationUpdated:`.<br /><br /> Bu anahtar sözcükler, yansıma sağlayıcısıyla kullanılan <xref:System.Data.Services.Common.SyndicationItemProperty> sabit listesi değerlerine eşdeğerdir.|  
  
> [!NOTE]
> Öznitelik adları ve değerleri büyük/küçük harfe duyarlıdır. Öznitelikler `EntityType` öğesine veya bir ya da daha fazla `Property` öğesine uygulanabilir, ancak her ikisine birden uygulanamaz.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile akışları özelleştirme  
 Yansıma sağlayıcısı kullanılarak uygulanan bir veri modeline ait akışları özelleştirmek için, veri modelindeki varlık türlerini temsil eden sınıflara <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> özniteliğin bir veya daha fazla örneğini ekleyin. <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> sınıfının özellikleri, önceki bölümde açıklanan akış özelleştirme özniteliklerine karşılık gelir. Aşağıda her iki özellik için tanımlanan özel akış eşlemesi ile `Order` türünün bildirimine bir örnek verilmiştir.  
  
> [!NOTE]
> Bu örneğe ilişkin veri modeli, [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md)konusunda tanımlanmıştır.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Bu öznitelikler `Orders` varlık kümesi için aşağıdaki özelleştirilmiş veri akışını oluşturur. Bu özelleştirilmiş akışta `OrderId` Özellik değeri yalnızca `entry` `title` öğesinde ve `Customer` özelliği değeri hem `author` öğesinde hem de `Customer` Property öğesi olarak görüntülenir:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: yansıma sağlayıcısı Ile akışları özelleştirme](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Özel bir veri hizmeti sağlayıcısı ile akışları özelleştirme  
 Özel veri hizmeti sağlayıcısı kullanılarak tanımlanan bir veri modeli için akış özelleştirmesi, veri modelindeki bir varlık türünü temsil eden <xref:System.Data.Services.Providers.ResourceType> <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> çağırarak bir kaynak türü için tanımlanmıştır. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Özel akışlar kullanma  
 Uygulamanız bir OData akışını doğrudan tükettiği zaman, döndürülen akıştaki özelleştirilmiş öğeleri ve öznitelikleri işleyebilmelidir. Veri modelinize bakılmaksızın özel akışlar uyguladıysanız, veri hizmeti sağlayıcısı ne olursa olsun `$metadata` uç noktası, veri hizmeti tarafından döndürülen CSDL içindeki özel akış öznitelikleri olarak özel akış bilgileri döndürür. İstemci veri hizmeti sınıfları oluşturmak için **hizmet başvurusu Ekle** iletişim kutusunu veya [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) aracını kullandığınızda, veri hizmetine yönelik isteklerin ve yanıtların doğru şekilde işleneceğini garantilemek için özelleştirilmiş akış öznitelikleri kullanılır.  
  
## <a name="feed-customization-considerations"></a>Akış özelleştirme konuları  
 Özel akış eşlemelerini tanımlarken aşağıdakileri göz önünde bulundurmanız gerekir.  
  
- WCF Veri Hizmetleri istemcisi, bir akışdaki eşlenmiş öğeleri yalnızca boşluk içerdiğinde boş olarak değerlendirir. Bu nedenle, yalnızca beyaz boşluk içeren eşlenmiş öğeler istemcide aynı boşluk ile gerçekleştirilmez. İstemcide bu boşluğu korumak için `KeepInContext` değerini akış eşleme özniteliğinde `true` olarak ayarlamanız gerekir.  
  
## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  
 Akış özelleştirmesi aşağıdaki OData protokol sürümü oluşturma gereksinimlerine sahiptir:  
  
- Akış özelleştirmesi hem istemci hem de veri hizmetinin OData protokolünün ve sonraki sürümlerinin 2,0 sürümünü desteklemesini gerektirir.  
  
 Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
