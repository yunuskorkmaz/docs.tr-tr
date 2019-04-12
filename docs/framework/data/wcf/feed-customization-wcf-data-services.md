---
title: Akış özelleştirme (WCF Data Services)
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
ms.openlocfilehash: 51da86d6c0f565d1baa58452a661ccbaa321538c
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517323"
---
# <a name="feed-customization-wcf-data-services"></a>Akış özelleştirme (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kullanan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] veri bir akış olarak kullanıma sunmak için. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] için veri akışı hem Atom hem de JavaScript nesne gösterimi (JSON) biçimlerini destekler. Atom akışı, kullandığınızda [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] varlıklar ve ilişkiler, HTTP ileti gövdesine eklenebilir bir XML biçimine gibi verileri seri hale getirmek için standart bir yöntemini sağlar. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] varlıklarda bulunan verileri ve Atom öğeleri arasında varsayılan varlık özelliği eşlemeyi tanımlar. Daha fazla bilgi için [OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Veri Hizmeti tarafından döndürülen özellik verileri, özelleştirilmiş bir şekilde yerine standart akış biçiminde seri hale gerektiren bir uygulama senaryosunda olabilir. İle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], veri akışı olarak seri hale getirme özellikleri bir varlığın eşlenebilir, kullanılmayan öğeleri ve özniteliklerinin bir girdinin veya akışta bir girdinin özel öğeler için özelleştirebilirsiniz.  
  
> [!NOTE]
>  Atom akışları için akış özelleştirme yalnızca desteklenir. JSON biçimi için döndürülen akışa istendiğinde özel akışları döndürülmez.  
  
 İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], veri modelindeki varlık türleri için el ile öznitelikleri uygulayarak bir Atom yükü için bir alternatif varlık özelliği eşleme tanımlayabilirsiniz. Veri hizmetinin veri kaynağı sağlayıcı, bu öznitelikler nasıl uygulanacağını belirler.  
  
> [!IMPORTANT]
>  Özel akışları tanımladığınızda, tanımlanan özel eşlemelere sahip tüm varlık özellikleri projeksiyonda içerdiği garanti etmeniz gerekir. Projeksiyon eşlenen varlık özelliği bulunmayan, veri kaybı oluşabilir. Daha fazla bilgi için [sorgu projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Entity Framework sağlayıcısı ile akışları özelleştirme  
 Veri modeli ile kullanılan [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı .edmx dosyası içinde XML olarak temsil edilir. Bu durumda, özel akışları tanımlama öznitelikleri eklenme `EntityType` ve `Property` varlık türleri ve veri modelinde özelliklerini temsil eden öğeler. Bu akış özelleştirme öznitelikleri içinde tanımlı değil [ \[MC CSDL\]: Kavramsal şema tanım dosyası biçimi](https://go.microsoft.com/fwlink/?LinkId=159072), biçim, [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı veri modeli tanımlamak için kullanır. Bu nedenle, akış özelleştirme öznitelikleri olarak tanımlanan belirli bir şema ad alanında bildirmeniz gerekir `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Aşağıdaki XML parçası için uygulanan akış özelleştirme öznitelikleri gösterir `Property` öğelerini `Products` tanımlayan varlık türü `ProductName`, `ReorderLevel`, ve `UnitsInStock` özellikleri.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Aşağıdaki özelleştirilmiş veri akışı için bu özniteliği üretmek `Products` varlık kümesi. Akış, özelleştirilmiş veri `ProductName` özellik değeri hem de görüntülenir `author` öğesi ve `ProductName` özellik öğesi ve `UnitsInStock` özelliği ile ve kendi benzersiz bir ad alanına sahip özel bir öğe görüntülenir `ReorderLevel` özelliği bir öznitelik olarak:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Daha fazla bilgi için [nasıl yapılır: Entity Framework sağlayıcısı ile akışları özelleştirme](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Veri modeline uzantıları varlık tasarımcısı tarafından desteklenmediği için veri modeli içeren XML dosyasını el ile değiştirmeniz gerekir. Tarafından oluşturulan .edmx dosyasını hakkında daha fazla bilgi için [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] araçları, görmek [.edmx dosyasını genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Özel öznitelik akışı  
 Aşağıdaki tabloda, veri modeli tanımlayan kavramsal şema tanım dili için (CSDL) ekleyebileceğiniz akışları özelleştirme XML öznitelikleri gösterir. Bu öznitelikler özelliklerine eşdeğerdir <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> yansıma sağlayıcısı ile kullanılır.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|`FC_ContentKind`|İçerik türünü belirtir. Aşağıdaki anahtar sözcükler, içerik dağıtım türlerini tanımlayın.<br /><br /> `text:` Özellik değeri, akışta metin olarak görüntülenir.<br /><br /> `html:` Özellik değeri, akışta HTML olarak görüntülenir.<br /><br /> `xhtml:` Özellik değeri, akışta XML biçimli bir HTML olarak görüntülenir.<br /><br /> Bu anahtar sözcükler değerleri eşdeğerdir <xref:System.Data.Services.Common.SyndicationTextContentKind> yansıma sağlayıcısı ile kullanılan sabit listesi.<br /><br /> Bu öznitelik değil ne zaman desteklenen `FC_NsPrefix` ve `FC_NsUri` öznitelikleri kullanılır.<br /><br /> Değerini belirttiğinizde `xhtml` için `FC_ContentKind` özniteliği emin olmanız gerekir özelliği değer düzgün biçimlendirilmiş XML içeriyor. Veri Hizmeti dönüştürmeler yapmadan değeri döndürür. Ayrıca tüm XML öğesi öneklerini döndürülen XML ad alanı URI ve eşlenen akışında tanımlı öneki olduğundan emin olun.|  
|`FC_KeepInContent`|Başvurulan özellik değeri hem de içerik akışı bölümünü eşlenen konumda eklenmesi gerektiğini belirtir. Geçerli değerler `true` ve `false`. Sonuçta elde edilen akışı önceki sürümleriyle geriye dönük olarak uyumlu hale getirmek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], değerini belirtirseniz `true` değeri akış içeriği bölümünde eklendiğinden emin olmak için.|  
|`FC_NsPrefix`|Bir dağıtım olmayan eşleme XML öğesi ad alanı öneki. Bu öznitelik ile birlikte kullanılmalıdır `FC_NsUri` özniteliği ve kullanılamaz `FC_ContentKind` özniteliği.|  
|`FC_NsUri`|Ad alanı URI bir dağıtım olmayan eşleme XML öğesi. Bu öznitelik ile birlikte kullanılmalıdır `FC_NsPrefix` özniteliği ve kullanılamaz `FC_ContentKind` özniteliği.|  
|`FC_SourcePath`|Bu eşleme kuralı akış varlık özelliğinin yolu geçerlidir. İçinde kullanıldığında bu öznitelik yalnızca desteklenen bir `EntityType` öğesi.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Özelliği, bir karmaşık tür doğrudan başvuramaz. Karmaşık türler için özellik adları ters eğik çizgi ile ayrıldığı bir yol ifadesi kullanmalısınız (`/`) karakter. Örneğin, bir varlık türü için aşağıdaki değerleri izin `Person` bir tamsayı özelliği ile `Age` ve karmaşık bir özellik<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Özelliği, bir alan veya özellik adı, geçerli olmayan başka bir karakter içeren bir değere ayarlanamaz.|  
|`FC_TargetPath`|Hedef öğe özelliği eşleştirmek için elde edilen akışın adı. Bu öğe, Atom belirtimi tarafından tanımlanan bir öğe veya özel bir öğe olabilir.<br /><br /> Aşağıdaki anahtar sözcükler belirli bir konuma işaret eden önceden tanımlanmış dağıtım hedef yolu değerler bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.<br /><br /> `SyndicationAuthorEmail:` `atom:email` Alt öğesi `atom:author` öğesi.<br /><br /> `SyndicationAuthorName:` `atom:name` Alt öğesi `atom:author` öğesi.<br /><br /> `SyndicationAuthorUri:` `atom:uri` Alt öğesi `atom:author` öğesi.<br /><br /> `SyndicationContributorEmail:` `atom:email` Alt öğesi `atom:contributor` öğesi.<br /><br /> `SyndicationContributorName:` `atom:name` Alt öğesi `atom:contributor` öğesi.<br /><br /> `SyndicationContributorUri:` `atom:uri` Alt öğesi `atom:contributor` öğesi.<br /><br /> `SyndicationCustomProperty:` Bir özel özellik öğesi. Özel bir öğeye eşlerken hedefi iç içe öğelerin bir ters eğik çizgi ile ayrılır bir yol ifadesi olmalıdır (`/`) ve öznitelikleri ampersan tarafından belirtilen (`@`). Aşağıdaki örnekte, dize `UnitsInStock/@ReorderLevel` adlı bir öznitelik için bir özellik değeri eşler `ReorderLevel` adlı bir alt öğesi üzerinde `UnitsInStock` kök giriş öğesinin.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Bir özel öğe adı hedeflendiğinde `FC_NsPrefix` ve `FC_NsUri` öznitelikleri de belirtilmelidir.<br /><br /> `SyndicationPublished:` `atom:published` Öğesi.<br /><br /> `SyndicationRights:` `atom:rights` Öğesi.<br /><br /> `SyndicationSummary:` `atom:summary` Öğesi.<br /><br /> `SyndicationTitle:` `atom:title` Öğesi.<br /><br /> `SyndicationUpdated:` `atom:updated` Öğesi.<br /><br /> Bu anahtar sözcükler değerleri eşdeğerdir <xref:System.Data.Services.Common.SyndicationItemProperty> yansıma sağlayıcısı ile kullanılan sabit listesi.|  
  
> [!NOTE]
>  Öznitelik adları ve değerleri büyük/küçük harf duyarlıdır. Öznitelikleri olabilir ya da uygulanan `EntityType` öğesi veya bir veya daha fazla `Property` öğeleri, ancak her ikisi de.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile akışları özelleştirme  
 Yansıma sağlayıcısı kullanılarak yapılıyordu bir veri modeli için akışları özelleştirmek için bir veya daha fazla örneğini ekleme <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> veri modelindeki varlık türleri temsil eden sınıfları özniteliği. Özelliklerini <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> sınıfı önceki bölümde açıklanan akış özelleştirme öznitelikleri karşılık gelir. Aşağıdaki bildirimi örnektir `Order` türüyle özel eşleme için her iki özellik tanımlanan akış.  
  
> [!NOTE]
>  Bu örnek için veri modeli konusunda tanımlanan [nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Aşağıdaki özelleştirilmiş veri akışı için bu özniteliği üretmek `Orders` varlık kümesi. Bu akış, özelleştirilmiş `OrderId` özellik değeri görüntüler yalnızca `title` öğesinin `entry` ve `Customer` özellik değeri görüntüler hem de `author` öğesi ve `Customer` özellik öğesi:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Daha fazla bilgi için [nasıl yapılır: Yansıma sağlayıcısı ile akışları özelleştirme](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Özel veri hizmeti sağlayıcısı ile akışları özelleştirme  
 Çağırarak bir kaynak türü için tanımlı bir özel veri hizmeti sağlayıcısı tarafından tanımlanan bir veri modeli için akış özelleştirme <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> üzerinde <xref:System.Data.Services.Providers.ResourceType> temsil eden bir veri modelindeki varlık türü. Daha fazla bilgi için [özel veri hizmeti sağlayıcılarını](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Özel tüketen akışları  
 Olduğunda, uygulamanızın doğrudan tüketen bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı, bunun tüm özelleştirilmiş öğeler ve öznitelikler döndürülen akıştaki işleyebilir olması gerekir. Veri hizmeti sağlayıcısı bakılmaksızın veri modelinizde özel akışları uygulamış `$metadata` uç noktasına özel akış bilgileri gibi özel akış öznitelikleri veri hizmeti tarafından döndürülen CSDL döndürür. Kullanırken **hizmet Başvurusu Ekle** iletişim veya [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracını istemci veri hizmeti sınıfları ve öznitelikleri isteklerine güvence altına almak için kullanılan özelleştirilmiş akış yanıtları oluşturmak için veri hizmeti doğru bir şekilde işlenir.  
  
## <a name="feed-customization-considerations"></a>Akış özelleştirme konuları  
 Özel akış eşlemeleri tanımlarken aşağıdakileri dikkate almanız gerekir.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci işler eşlenmiş öğeleri bir akışta boş olarak bunlar yalnızca boşluk içerdiğinde. Bu nedenle, yalnızca boşluk içeren eşlenen öğeler aynı boşluk ile istemcide gerçekleştirilmiş değil. Bu istemcideki bölünemez boşluğu koruyacak şekilde değerini ayarlamalısınız `KeepInContext` için `true` akış eşleme öznitelik.  
  
## <a name="versioning-requirements"></a>Sürüm gereksinimleri  
 Akış özelleştirmeye sahip aşağıdaki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokolü sürüm gereksinimleri:  
  
-   Akış özelleştirme gerektirir, hem istemci hem de veri hizmeti destek 2.0 sürümünü [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol ve sonraki sürümler.  
  
 Daha fazla bilgi için [veri hizmeti sürümü oluşturma](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
