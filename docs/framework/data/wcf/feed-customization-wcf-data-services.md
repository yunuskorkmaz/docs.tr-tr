---
title: "Akış özelleştirme (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12820b6b2b864bfd00474abc118fe9b346b51bc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="feed-customization-wcf-data-services"></a>Akış özelleştirme (WCF Veri Hizmetleri)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]kullanan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] veriyi bir akış olarak kullanıma sunmak için. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]veri akışları için hem Atom hem de JavaScript nesne gösterimi (JSON) biçimini destekler. Atom akışı, kullandığınızda [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] varlıkları ve ilişkileri HTTP iletisinin gövdesinde bulunan bir XML biçimine gibi verileri seri hale getirmek için standart bir yöntemini sağlar. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]bir varsayılan varlık özellik eşlemesi varlıklarda bulunan verileri Atom öğeler arasındaki tanımlar. Daha fazla bilgi için bkz: [OData: Atom biçimi](http://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Veri Hizmeti tarafından döndürülen özelliği veri özelleştirilmiş bir şekilde yerine akış biçiminde standart seri hale gerektiren bir uygulama senaryosu olabilir. İle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], bir veri akışı serileştirmede kullanılmayan öğeleri ve özniteliklerinin girdinin veya akıştaki girdinin özel öğeleri için bir varlık özelliklerini eşlenebilir özelleştirebilirsiniz.  
  
> [!NOTE]
>  Atom akışları için akış özelleştirme yalnızca desteklenir. JSON biçimi döndürülen akış için istendiğinde özel akışları döndürülmez.  
  
 İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], veri modeli varlık türlerine el ile öznitelikleri uygulayarak bir Atom yükü için bir alternatif varlık özellik eşlemesi tanımlayabilirsiniz. Veri kaynağı sağlayıcı veri hizmetinin bu öznitelikler nasıl uygulamalıdır belirler.  
  
> [!IMPORTANT]
>  Özel akışları tanımladığınızda, tanımlı özel eşlemeleri sahip tüm varlık özellikleri projeksiyon içerdiği güvence altına almalıdır. Eşlenen varlık özelliği cinsinden izdüşümünü bulunmaz, veri kaybı oluşabilir. Daha fazla bilgi için bkz: [sorgu tahminleri](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Entity Framework sağlayıcısı akışlarıyla özelleştirme  
 İle kullanılan veri modelini [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcı .edmx dosyasının XML olarak temsil edilir. Bu durumda, özel akışları tanımlama öznitelikleri eklenir `EntityType` ve `Property` varlık türleri ve veri modelindeki özellikleri temsil eden öğeleri. Bu akış özelleştirme öznitelikler tanımlı değil [ \[MC CSDL\]: kavramsal şema tanım dosyası biçimi](http://go.microsoft.com/fwlink/?LinkId=159072), biçimi olduğu, [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] sağlayıcısı veri modeli tanımlamak için kullanır. Bu nedenle, akış özelleştirme öznitelikleri olarak tanımlanmış bir özel Şema ad alanındaki bildirmelidir `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Aşağıdaki XML parçası uygulanan akış özelleştirme öznitelikleri gösterir `Property` öğeleri `Products` tanımlayan varlık türü `ProductName`, `ReorderLevel`, ve `UnitsInStock` özellikleri.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Bu öznitelikler için akış aşağıdaki özelleştirilmiş veri üretmek `Products` varlık kümesi. Akış, özelleştirilmiş veri `ProductName` özellik değerini hem de görüntülenir `author` öğesi de `ProductName` özellik öğesi ve `UnitsInStock` özelliği, kendi benzersiz ad alanına sahip özel bir öğe ve ile görüntülenir `ReorderLevel` öznitelik olarak özellik:  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: özelleştirme akışları Entity Framework sağlayıcısı ile](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Veri modeli için Uzantılar Entity Designer tarafından desteklenmediği için veri modeli içeren XML dosyasını el ile değiştirmeniz gerekir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tarafından oluşturulan .edmx dosyasının [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] araçları, bkz: [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Özel öznitelikler akışı  
 Aşağıdaki tabloda veri modeli tanımlayan kavramsal şema tanım dili için (CSDL) ekleyebileceğiniz akışları özelleştirme XML öznitelikleri gösterir. Bu öznitelikler özelliklerine eşdeğer <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> yansıma sağlayıcı ile kullanılır.  
  
|Öznitelik adı|Açıklama|  
|--------------------|-----------------|  
|`FC_ContentKind`|İçerik türünü belirtir. Aşağıdaki anahtar sözcükler dağıtım içerik türünü tanımlar.<br /><br /> `text:`Özellik değeri akışta metin olarak görüntülenir.<br /><br /> `html:`Özellik değeri akışta HTML olarak görüntülenir.<br /><br /> `xhtml:`Özellik değeri akışta XML biçimli HTML olarak görüntülenir.<br /><br /> Bu anahtar sözcükler değerleri eşdeğer <xref:System.Data.Services.Common.SyndicationTextContentKind> yansıma sağlayıcı ile kullanılan numaralandırması.<br /><br /> Bu öznitelik ne zaman desteklenen `FC_NsPrefix` ve `FC_NsUri` öznitelikler kullanılır.<br /><br /> Değerini belirttiğinizde `xhtml` için `FC_ContentKind` özniteliği sağlamanız özellik değeri düzgün şekilde biçimlendirilmemiş XML içeriyor. Veri Hizmeti, herhangi bir dönüştürme yapmadan değeri döndürür. Ayrıca tüm XML öğesi öneklerini döndürülen XML ad alanı URI'si ve eşlenen akışta tanımlanan önek sahip olduğundan emin olmalısınız.|  
|`FC_KeepInContent`|Başvurulan özellik değeri akışın içerik bölümü hem eşleşen konumda eklenmesi gerektiğini gösterir. Geçerli değerler `true` ve `false`. Sonuçta elde edilen akış önceki sürümleriyle geriye dönük uyumlu olmak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], değerini belirtin `true` değeri akış içeriği bölümünde bulunduğundan emin olmak için.|  
|`FC_NsPrefix`|XML öğesi olmayan dağıtım eşlemeye ad alanı öneki. Bu öznitelik ile birlikte kullanılmalıdır `FC_NsUri` özniteliği ve kullanılamaz `FC_ContentKind` özniteliği.|  
|`FC_NsUri`|Ad alanı URI'si dağıtım olmayan eşlemeye XML öğesi. Bu öznitelik ile birlikte kullanılmalıdır `FC_NsPrefix` özniteliği ve kullanılamaz `FC_ContentKind` özniteliği.|  
|`FC_SourcePath`|Bu eşleme kuralı akış varlık özelliğinin yolu geçerlidir. İçinde kullanıldığında bu öznitelik yalnızca desteklenen bir `EntityType` öğesi.<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Özelliği bir karmaşık tür doğrudan başvuruda bulunamaz. Karmaşık türler için bir yol ifadesi özellik adları bir ters eğik çizgi ile ayrıldığı kullanmanız gerekir (`/`) karakter. Örneğin, aşağıdaki değerleri bir varlık türü için izin `Person` bir tamsayı özelliği ile `Age` ve karmaşık bir özellik<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> Özelliği, bir boşluk veya bir özellik adı geçerli değil herhangi bir karakter içeren bir değere ayarlanamaz.|  
|`FC_TargetPath`|Sonuçta elde edilen akışın özelliği eşlemek istediğiniz hedef öğesinin adı. Bu öğe Atom belirtim tarafından tanımlanan bir öğe veya özel bir öğe olabilir.<br /><br /> Belirli bir konuma işaret önceden tanımlanmış dağıtım hedef yolu değerleri aşağıdaki sözcükler bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.<br /><br /> `SyndicationAuthorEmail:``atom:email` Alt öğesi olan `atom:author` öğesi.<br /><br /> `SyndicationAuthorName:``atom:name` Alt öğesi olan `atom:author` öğesi.<br /><br /> `SyndicationAuthorUri:``atom:uri` Alt öğesi olan `atom:author` öğesi.<br /><br /> `SyndicationContributorEmail:``atom:email` Alt öğesi olan `atom:contributor` öğesi.<br /><br /> `SyndicationContributorName:``atom:name` Alt öğesi olan `atom:contributor` öğesi.<br /><br /> `SyndicationContributorUri:``atom:uri` Alt öğesi olan `atom:contributor` öğesi.<br /><br /> `SyndicationCustomProperty:`Bir özel özellik öğesi. Özel bir öğeye eşlerken hedef iç içe öğelerin bir ters eğik çizgi ile ayrılır yol ifadesi olmalıdır (`/`) ve öznitelikleri ampersan tarafından belirtilen (`@`). Aşağıdaki örnekte, dize `UnitsInStock/@ReorderLevel` adlı bir özniteliği için bir özellik değeri eşler `ReorderLevel` adlı bir alt öğesi üzerinde `UnitsInStock` kök giriş öğesinin.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Hedef bir özel öğe adı olduğunda `FC_NsPrefix` ve `FC_NsUri` öznitelikler de belirtilmesi gerekir.<br /><br /> `SyndicationPublished:``atom:published` Öğesi.<br /><br /> `SyndicationRights:``atom:rights` Öğesi.<br /><br /> `SyndicationSummary:``atom:summary` Öğesi.<br /><br /> `SyndicationTitle:``atom:title` Öğesi.<br /><br /> `SyndicationUpdated:``atom:updated` Öğesi.<br /><br /> Bu anahtar sözcükler değerleri eşdeğer <xref:System.Data.Services.Common.SyndicationItemProperty> yansıma sağlayıcı ile kullanılan numaralandırması.|  
  
> [!NOTE]
>  Öznitelik adları ve değerleri büyük/küçük harf duyarlıdır. Öznitelikleri olabilir ya da uygulanan `EntityType` öğesi ya da bir veya daha fazla `Property` öğeleri, ancak her ikisi de.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Yansıma sağlayıcısı ile akışları özelleştirme  
 Yansıma kullanarak uygulanan bir veri modeli akışları özelleştirmek için bir veya daha fazla örneğini ekleyin <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> özniteliği için veri modelindeki varlık türleri temsil eden sınıflar için. Özelliklerini <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> sınıfı önceki bölümde açıklanan akış özelleştirme öznitelikleri karşılık gelir. Aşağıdaki bildirimi örneğidir `Order` türüyle özel eşleme için her iki özellik tanımlanan akış.  
  
> [!NOTE]
>  Bu örnek için veri modeli konusundaki tanımlanan [nasıl yapılır: yansıma sağlayıcı veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Bu öznitelikler için akış aşağıdaki özelleştirilmiş veri üretmek `Orders` varlık kümesi. Bu akış, özelleştirilmiş `OrderId` özellik değeri görüntüler yalnızca `title` öğesinin `entry` ve `Customer` özellik değeri görüntüler hem de `author` öğesi de `Customer` özellik öğesi:  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: özelleştirme akışları yansıma sağlayıcısı ile](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Bir özel veri hizmeti sağlayıcısına akışları özelleştirme  
 Özelleştirme çağırarak bir kaynak türü için tanımlı bir özel veri hizmeti sağlayıcısı kullanılarak tanımlanmış bir veri modeli için akış <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> üzerinde <xref:System.Data.Services.Providers.ResourceType> , bir varlık türü için veri modelindeki temsil eder. Daha fazla bilgi için bkz: [özel veri hizmeti sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Özel tüketen akışları  
 Olduğunda, uygulamanızın doğrudan tüketir bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, bunun herhangi bir özelleştirilmiş öğeleri ve özniteliklerinin döndürülen akıştaki işleyebilmesi olması gerekir. Veri hizmeti sağlayıcısı bağımsız olarak, veri modelinde özel akışları uygulamış `$metadata` uç nokta döndüren özel veri hizmet tarafından döndürülen csdl'deki olarak özel akış öznitelikleri bilgi akışı. Kullandığınızda **hizmet Başvurusu Ekle** iletişim veya [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) istemci veri hizmeti sınıfları, özelleştirilmiş akış öznitelikleri isteklerine güvence altına almak için kullanılır ve yanıtları oluşturmak için aracı veri hizmeti doğru şekilde işlenir.  
  
## <a name="feed-customization-considerations"></a>Akış özelleştirme konuları  
 Aşağıdaki özel akış eşlemeleri tanımlarken düşünmelisiniz.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci değerlendirir eşlenmiş öğeleri akış boş olarak yalnızca boşluk içeriyorsa. Bu nedenle, yalnızca boşluk içeren eşlenmiş öğeleri aynı boşluk ile istemcide gerçekleştirilip değil. Bu istemcideki korumak için değerini ayarlamalısınız `KeepInContext` için `true` akış eşleme öznitelik.  
  
## <a name="versioning-requirements"></a>Sürüm oluşturma gereksinimleri  
 Akış özelleştirme olan aşağıdaki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] iletişim kuralı sürüm gereksinimleri:  
  
-   Akış özelleştirme gerektiren bu hem istemci hem de veri hizmeti destek 2.0 sürümünü [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü ve sonraki sürümler.  
  
 Daha fazla bilgi için bkz: [veri hizmeti sürüm](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansıma sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Entity Framework sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
