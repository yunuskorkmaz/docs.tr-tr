---
title: Sorgu projeksiyonlar (WCF Veri Hizmetleri)
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
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cd775ed31d0457308f86b3d5b6f40092bfa9690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="query-projections-wcf-data-services"></a>Sorgu projeksiyonlar (WCF Veri Hizmetleri)
Projeksiyon bir mekanizma sağlar [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] yalnızca belirli özellikleri bir varlığın yanıtta döndürülen belirterek bir sorgu tarafından döndürülen akıştaki veri miktarını azaltmak için. Daha fazla bilgi için bkz: [OData: Sistem sorgusu seçeneği ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Bu konuda nasıl varlık için gereksinimler nelerdir sorgu projeksiyon tanımlamak için ve varlık olmayan türleri, yapmadan güncelleştirmeleri tahmini sonuçları için tahmini türleri oluşturma ve bazı projeksiyon konular listelenmiştir açıklanmaktadır.  
  
## <a name="defining-a-query-projection"></a>Bir sorgu projeksiyon tanımlama  
 Projeksiyon yan tümcesi bir sorgu kullanarak ya da ekleyebilirsiniz `$select` sorgu seçeneği bir URI veya kullanarak [seçin](~/docs/csharp/language-reference/keywords/select-clause.md) yan tümcesi ([seçin](~/docs/visual-basic/language-reference/queries/select-clause.md) Visual Basic'te) LINQ Sorgu. Varlık veri öngörülen varlık türleri veya varlık olmayan türler istemcide döndürdü. Bu konudaki örnekler nasıl kullanılacağını göstermektedir `select` yan tümcesinde bir LINQ Sorgu.  
  
> [!IMPORTANT]
>  Tahmini türleri için yapılan güncelleştirmeler kaydettiğinizde, veri hizmeti veri kaybı oluşabilir. Daha fazla bilgi için bkz: [projeksiyon konuları](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Varlık ve varlık olmayan türleri için gereksinimleri  
 Varlık türleri Varlık anahtarı oluşturan bir veya daha fazla kimlik özellikleri olması gerekir. Varlık türleri istemcilerde aşağıdaki yollardan biriyle tanımlanmıştır:  
  
-   Uygulayarak <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> türü.  
  
-   Adlı bir özellik türüne sahip olduğunda `ID`.  
  
-   Adlı bir özellik türüne sahip olduğunda *türü*`ID`, burada *türü* türünün adı.  
  
 İstemcide tanımlanan bir türü içine sorgu sonuçları projenizin varsayılan olarak, istemci türünde projeksiyon istenen özellikler mevcut olması gerekir. Ancak, değerini belirttiğinizde `true` için <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>, projeksiyon belirtilen özellikler istemci türü gerçekleşmesi için gerekli değildir.  
  
### <a name="making-updates-to-projected-results"></a>Tahmini sonuçları güncelleştirmeleri yapma  
 Sorgu sonuçları istemci üzerinde varlık türlerine projenizin <xref:System.Data.Services.Client.DataServiceContext> verileri yedekleyin gönderilmek üzere güncelleştirmeleri bu nesnelerle izleyebilirsiniz ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır. Bununla birlikte, varlık olmayan türlerine istemcide öngörülen verilere yapılan güncelleştirmeler veri hizmetine gönderilemiyor. Varlık örneği tanımlamak için bir anahtar olmadan, veri hizmeti veri kaynağının doğru varlık güncelleştirilemez olmasıdır. Olmayan varlık türleri değil bağlanan <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Veri Hizmeti tanımlanan bir varlık türünün bir veya daha fazla özelliklerini içine varlık yansıtılır istemci türünde değil gerçekleştiğinde, yeni varlık ekler bu eksik özellikleri içermez. Bu durumda, var olan varlıkları için yapılan güncelleştirmeler olacak **de** bu eksik özellikler eklemeniz gerekmez. Böyle bir özellik için bir değer mevcut olduğunda, güncelleştirme, bir özellik için varsayılan değer veri kaynağında tanımlanan sıfırlar.  
  
### <a name="creating-projected-types"></a>Tahmini türleri oluşturma  
 Aşağıdaki örnek, adresi ilgili özelliklerini projeleri anonim bir LINQ sorgusu kullanır `Customers` yeni bir türe `CustomerAddress` istemcide tanımlanır ve varlık türü olarak öznitelikli türü:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 Bu örnekte, nesne Başlatıcı düzeni yeni bir örneğini oluşturmak için kullanılan `CustmerAddress` bir oluşturucu çağırarak yerine türü. Varlık türleriyle yansıtılırken oluşturucuları desteklenmiyor ancak varlık olmayan ve anonim türler yansıtılırken kullanılabilir. Çünkü `CustomerAddress` bir varlık türü olduğu değişiklikleri yapılan ve veri hizmetine gönderilir.  
  
 Ayrıca, verileri `Customer` türü örneğini öngörülen `CustomerAddress` anonim bir tür yerine varlık türü. Anonim türler içine projeksiyon desteklenir, ancak anonim türler, varlık olmayan türleri olarak değerlendirildiğinden veriler salt okunur.  
  
 <xref:System.Data.Services.Client.MergeOption> Ayarlarını <xref:System.Data.Services.Client.DataServiceContext> kimlik çözümlemesi için sorgu projeksiyon sırasında kullanılır. Bu örneği olması durumunda gelir `Customer` türü zaten <xref:System.Data.Services.Client.DataServiceContext>, örneği `CustomerAddress` aynı kimlikle tarafından belirlenen kuralları kimlik çözümleme izler<xref:System.Data.Services.Client.MergeOption>  
  
 Aşağıdaki tabloda, varlık ve varlık olmayan türlerine sonuçları yansıtılırken davranışları açıklanmaktadır:  
  
|Eylem|Varlık türü|Varlık dışı türü|  
|------------|-----------------|----------------------|  
|Aşağıdaki örnekte olduğu gibi başlatıcıları kullanarak yeni bir tahmini örneği oluşturma:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|Desteklenir|Desteklenir|  
|Aşağıdaki örnekte olduğu gibi oluşturucuları kullanarak yeni bir tahmini örneği oluşturma:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|A <xref:System.NotSupportedException> tetiklenir.|Desteklenir|  
|Projeksiyon kullanarak aşağıdaki örnekteki gibi bir özellik değeri dönüştürmek için:<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> Karışıklığı önlemek için ve büyük olasılıkla başka bir varlığa ait veri kaynağındaki verileri üzerine neden olabilir çünkü bu dönüşüm varlık türleri için desteklenmiyor.|A <xref:System.NotSupportedException> tetiklenir.|Desteklenir|  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Projeksiyon konuları  
 Bir sorgu projeksiyon tanımlarken aşağıdaki hususlar geçerlidir.  
  
-   Atom biçimi için özel akışları tanımladığınızda, tanımlı özel eşlemeleri sahip tüm varlık özellikleri projeksiyon içerdiği emin olmanız gerekir. Eşlenen varlık özelliği cinsinden izdüşümünü bulunmaz, veri kaybı oluşabilir. Daha fazla bilgi için bkz: [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Ekler, varlık veri hizmetinin veri modelindeki özelliklerin tümünü içermiyor tahmini bir türe yapıldığında, istemcide projeksiyon bulunmayan özellikler varsayılan değerlerine ayarlanır.  
  
-   Varlık veri hizmetinin veri modelindeki özelliklerin tümünü içermiyor tahmini bir türe güncelleştirmeleri yapıldığında istemcide projeksiyon bulunmayan mevcut değerleri başlatılmamış varsayılan değerlerle üzerine yazılır.  
  
-   Bir yansıtma karmaşık bir özellik varsa, tüm karmaşık nesne iade edilmesi gerekir.  
  
-   Bir yansıtma bir gezinti özelliği içerdiğinde, ilgili nesneleri örtük olarak çağrı yapmak zorunda kalmadan yüklenen <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Yöntemi tahmini sorguda kullanım için desteklenmez.  
  
-   Sorgu tahminleri sorgular istemcide kullanmak üzere çevrilen `$select` seçeneği URI isteğinde sorgu. Ne zaman bir sorgu projeksiyon yürütüldüğünde önceki bir sürümünü karşı [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , desteklemiyor `$select` sorgu seçeneği bir hata döndürülür. Bu da gerçekleşebilir, <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> , <xref:System.Data.Services.DataServiceBehavior> için veri hizmeti değerine ayarlanır <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Daha fazla bilgi için bkz: [veri hizmeti sürüm](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: Proje sorgu sonuçları](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
