---
title: Sorgu projeksiyonları (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: d53892f9823474ea14640e352548b55432e7744b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526694"
---
# <a name="query-projections-wcf-data-services"></a>Sorgu projeksiyonları (WCF Data Services)
Projeksiyon mekanizması sağlar [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akıştaki yalnızca belirli özellikleri bir varlığın yanıtta döndürülen belirterek bir sorgu tarafından döndürülen veri miktarını azaltmak için. Daha fazla bilgi için [OData: Sistem sorgusu seçeneği seçin ($select)](https://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Bu konu nasıl varlık için gereksinimler nelerdir sorgu projeksiyon tanımlamak için ve varlık olmayan türleri, yapmadan öngörülen türleri oluşturma tahmini sonuçlarını güncelleştirir ve bazı projeksiyon konuları listeler açıklar.  
  
## <a name="defining-a-query-projection"></a>Bir sorgu projeksiyon tanımlama  
 Bir projeksiyon yan tümcesi bir sorgu kullanılarak ekleyebileceğiniz `$select` sorgu seçeneği bir URI veya kullanarak [seçin](~/docs/csharp/language-reference/keywords/select-clause.md) yan tümcesi ([seçin](~/docs/visual-basic/language-reference/queries/select-clause.md) Visual Basic'te) bir LINQ Sorgu. Varlık veri öngörülen varlık türleri veya varlığı olmayan türleri istemcide döndürdü. Bu konudaki örnekler nasıl kullanılacağını gösteren `select` bir LINQ sorgu yan tümcesi.  
  
> [!IMPORTANT]
>  Veri kaybı tahmini türlerine yapılan güncelleştirmeleri kaydetmek veri hizmetinde gerçekleşebilir. Daha fazla bilgi için [projeksiyon konuları](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Varlık veya varlık olmayan türleri için gereksinimleri  
 Varlık türleri Varlık anahtarı oluşturan bir veya daha fazla kimlik özellikleri olmalıdır. Varlık türleri istemcilerde aşağıdaki yollardan biriyle tanımlanır:  
  
-   Uygulayarak <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> türü.  
  
-   Türü adlı bir özellik bulunduğunda `ID`.  
  
-   Türü adlı bir özellik bulunduğunda *türü*`ID`burada *türü* türünün adı.  
  
 İstemcide, tanımlı bir tür içinde sorgu sonuçları projenizin varsayılan olarak, istemci türünde projeksiyon istenen özellikler mevcut olmalıdır. Ancak, değerini belirttiğinizde `true` için <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği <xref:System.Data.Services.Client.DataServiceContext>, özellikleri ortasının derece cinsinden belirtilen istemci türünde gerçekleşmesi için gerekli değildir.  
  
### <a name="making-updates-to-projected-results"></a>Gelecekteki sonuçları güncelleştirmeler yapma  
 İstemcide, varlık türlerine sorgu sonuçları projenizin <xref:System.Data.Services.Client.DataServiceContext> nesnelere verileri geri gönderilecek güncelleştirmeleri ile izleyebilirsiniz ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır. Ancak, veri hizmetine verilerle istemcide varlık olmayan tür olarak öngörülen yapılan güncelleştirmeler gönderilemez. Varlık örneğini tanımlamak için bir anahtar olmadan doğru varlık veri kaynağındaki veri hizmeti güncelleştirilemiyor olmasıdır. Varlık olmayan türleri bağlanan değil <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Bir varlık türünün tanımlanan veri hizmetinde bir veya daha fazla özellik varlığın üzerine gsyih istemci türünde gerçekleşmez, yeni varlık ekler bu eksik özellikleri içermez. Bu durumda, mevcut varlıklarda yapılan güncelleştirmeler olacak **ayrıca** bu eksik özellikler eklemeniz gerekmez. Böyle bir özellik için bir değer mevcut olduğunda, güncelleştirme, özellik için varsayılan değer veri kaynağında tanımlanan sıfırlar.  
  
### <a name="creating-projected-types"></a>Öngörülen türleri oluşturma  
 Aşağıdaki örnekte adresi ile ilgili özellikleri projelerin anonim bir LINQ Sorgu `Customers` yeni bir türe `CustomerAddress` istemcide tanımlanır ve bir varlık türü olarak öznitelikli türü:  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 Bu örnekte, nesne Başlatıcısı deseni yeni bir örneğini oluşturmak için kullanılan `CustmerAddress` bir oluşturucu çağırmak yerine türü. Varlık türleriyle yansıtılırken oluşturucuları desteklenmiyor ancak varlık olmayan ve anonim tür olarak yansıtılırken kullanılabilir. Çünkü `CustomerAddress` bir varlık türü olduğu değişiklikleri yapılan ve veri hizmetine geri gönderilir.  
  
 Ayrıca, verileri `Customer` türü örneği öngörülen `CustomerAddress` anonim bir tür yerine varlık türü. Anonim türlerini projeksiyon desteklenir, ancak anonim türler, varlık olmayan türleri olarak değerlendirildiğinden veri salt okunur.  
  
 <xref:System.Data.Services.Client.MergeOption> Ayarlarını <xref:System.Data.Services.Client.DataServiceContext> sorgu yansıtma sırasında kimlik çözümlemesi için kullanılır. Bu, eğer bir örneğini anlamına gelir `Customer` türü zaten <xref:System.Data.Services.Client.DataServiceContext>, örneği `CustomerAddress` aynı kimlikle kurallar tarafından kimlik çözümlemesi izler <xref:System.Data.Services.Client.MergeOption>  
  
Aşağıdaki sonuçları varlık ve varlık olmayan tür olarak yansıtılırken davranışları açıklanmaktadır:  

**Başlatıcılar kullanarak yeni bir tahmini örneği oluşturma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]

- Varlık türü: desteklenir

- Olmayan varlık türü: desteklenir

**Oluşturucuları kullanarak yeni bir tahmini örneği oluşturma**

- Örnek: 

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]

- Varlık türü: A <xref:System.NotSupportedException> tetiklenir.

- Olmayan varlık türü: desteklenir

**Bir özellik değerini dönüştürmek için yansıtma kullanma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]
   
- Varlık türü: karışıklık ve büyük olasılıkla başka bir varlığa ait veri kaynağındaki verileri üzerine neden olabileceği için varlık türleri için bu dönüştürme desteklenmiyor. A <xref:System.NotSupportedException> tetiklenir.

- Olmayan varlık türü: desteklenir  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Projeksiyon konuları  
 Aşağıdaki ek konulara ilişkin sorgu projeksiyon tanımlarken uygulayın.  
  
-   Atom biçimi için özel akışları tanımladığınızda, tanımlı özel eşlemelere sahip tüm varlık özellikleri projeksiyonda içerdiği emin olmanız gerekir. Projeksiyon eşlenen varlık özelliği bulunmayan, veri kaybı oluşabilir. Daha fazla bilgi için [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Tüm veri hizmetinin veri modelinde entity öğesinin özellikleri içermiyor öngörülen bir türe yapılan eklemeleri, istemcide projeksiyon bulunmayan özellikleri varsayılan değerlerine ayarlanır.  
  
-   Güncelleştirmeleri, tüm veri hizmetinin veri modelinde entity öğesinin özellikleri içermiyor öngörülen bir türe yapıldığında, istemci projeksiyonda bulunmayan mevcut değerleri başlatılmamış varsayılan değerlerle üzerine yazılır.  
  
-   Bir projeksiyon karmaşık bir özellik varsa, tüm karmaşık nesne iade edilmesi gerekir.  
  
-   Bir projeksiyon bir gezinti özelliği içerir, ilişkili nesneleri örtük olarak aramak zorunda kalmadan yüklenir <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Öngörülen sorguda kullanmak için yöntemi desteklenmiyor.  
  
-   Sorgu projeksiyonları sorgular istemcide çevrilmiş kullanılacak `$select` seçeneği istek URI'SİNDE sorgu. Ne zaman bir projeksiyon sorgu yürütüldüğünde önceki bir sürümünü karşı [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] desteklemeyen `$select` sorgu seçeneği bir hata döndürülür. De gerçekleşebilir, <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> , <xref:System.Data.Services.DataServiceBehavior> için veri hizmeti için bir değer ayarlanır <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Daha fazla bilgi için [veri hizmeti sürümü oluşturma](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Daha fazla bilgi için [nasıl yapılır: Proje sorgu sonuçları](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
