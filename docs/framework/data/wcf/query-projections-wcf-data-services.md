---
title: Sorgu tahminleri (WCF Veri Hizmetleri)
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
ms.openlocfilehash: 17475cccf461371a909660bfe3f8db29bf1fa2fe
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975181"
---
# <a name="query-projections-wcf-data-services"></a>Sorgu tahminleri (WCF Veri Hizmetleri)

Projeksiyon, yanıtta bir varlığın yalnızca belirli özelliklerinin döndürülüp döndürülmeyeceğini belirterek, bir sorgu tarafından döndürülen akıştaki veri miktarını azaltmak için açık veri Protokolü (OData) içinde bir mekanizma sağlar. Daha fazla bilgi için bkz. [OData: sistem sorgu seçeneğini seçin ($Select)](https://go.microsoft.com/fwlink/?LinkId=186076).

Bu konu, bir sorgu projeksiyonu, varlık ve varlık olmayan türler için gereksinimlerin ne olduğunu, öngörülen sonuçlara yönelik güncelleştirmeler yapmayı, tasarlanan türleri oluşturmayı ve bazı projeksiyon konularını listeler.

## <a name="defining-a-query-projection"></a>Sorgu projeksiyonu tanımlama

Bir URI içinde `$select` sorgu seçeneğini kullanarak veya bir LINQ sorgusunda [Select](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesini (Visual Basic içinde[seçin](../../../visual-basic/language-reference/queries/select-clause.md) ) kullanarak bir sorguya projeksiyon yan tümcesi ekleyebilirsiniz. Döndürülen varlık verileri, istemci üzerindeki varlık türlerine veya varlık olmayan türlere yansıtılmalıdır. Bu konudaki örneklerde, bir LINQ sorgusunda `select` yan tümcesinin nasıl kullanılacağı gösterilmektedir.

> [!IMPORTANT]
> Tasarlanan türlerde yapılan güncelleştirmeleri kaydettiğinizde veri hizmetinde veri kaybı oluşabilir. Daha fazla bilgi için bkz. [projeksiyon konuları](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Varlık ve varlık olmayan türler için gereksinimler

Varlık türlerinin, varlık anahtarını oluşturan bir veya daha fazla kimlik özelliği olmalıdır. Varlık türleri, istemcilerde aşağıdaki yollarla tanımlanmıştır:

- <xref:System.Data.Services.Common.DataServiceKeyAttribute> veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> türe uygulayarak.

- Türün `ID`adında bir özelliği varsa.

- *Türün type`ID`adında* bir özelliği varsa *, burada tür adıdır.*

Varsayılan olarak, sorgu sonuçlarını istemcide tanımlı bir türe proje yaparken, projeksiyde istenen özellikler istemci türünde bulunmalıdır. Ancak, <xref:System.Data.Services.Client.DataServiceContext><xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği için bir `true` değeri belirttiğinizde, projeksiyde belirtilen özelliklerin istemci türünde gerçekleşmesi gerekmez.

### <a name="making-updates-to-projected-results"></a>Yansıtılan sonuçlara güncelleştirmeler yapılıyor

Sorgu sonuçlarını istemcideki varlık türlerine proje yaparken, <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrıldığında veri hizmetine geri gönderilmek üzere güncelleştirmeler içeren nesneleri izleyebilir. Ancak, istemcideki varlık olmayan türlere yapılan veriler veri hizmetine geri gönderilemez. Bunun nedeni, varlık örneğini tanımlamak için bir anahtar olmadığı için veri hizmeti veri kaynağındaki doğru varlığı güncelleştiremez. Varlık dışı türler <xref:System.Data.Services.Client.DataServiceContext>eklenmez.

Veri hizmetinde tanımlanan bir veya daha fazla varlık türünün bir veya daha fazla özelliği, varlığın yansıtıldıkları istemci türünde gerçekleşmezse, yeni varlıkların ekleme işlemi bu eksik özellikleri içermez. Bu durumda, mevcut varlıklarda yapılan güncelleştirmeler bu eksik özellikleri **de** içermez. Bu tür bir özellik için bir değer varsa, güncelleştirme onu veri kaynağında tanımlandığı şekilde özellik için varsayılan değere sıfırlar.

### <a name="creating-projected-types"></a>Öngörülen türler oluşturuluyor

Aşağıdaki örnek, `Customers` türünün adresle ilgili özelliklerini, istemcide tanımlanan ve bir varlık türü olarak öznitelikli yeni bir `CustomerAddress` türüne depolayan bir anonim LINQ sorgusu kullanır:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

Bu örnekte, nesne Başlatıcısı, Oluşturucu çağırmak yerine `CustomerAddress` türünün yeni bir örneğini oluşturmak için kullanılır. Oluşturucular varlık türlerine yansıtılamayan desteklenmez, ancak varlık dışı ve anonim türler halinde yansıtılarınızda kullanılabilirler. `CustomerAddress` bir varlık türü olduğundan, değişiklikler yapılabilir ve veri hizmetine geri gönderilebilir.

Ayrıca, `Customer` türündeki veriler, anonim bir tür yerine `CustomerAddress` varlık türünün bir örneğine yansıtıldır. Anonim türlere yansıtma desteklenir, ancak anonim türler varlık dışı türler olarak değerlendirildiğinden veriler salt okunurdur.

<xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.MergeOption> ayarları, sorgu projeksiyonu sırasında kimlik çözümlemesi için kullanılır. Bu, `Customer` türünün bir örneği <xref:System.Data.Services.Client.DataServiceContext>zaten mevcutsa, aynı kimliğe sahip bir `CustomerAddress` örneğinin, <xref:System.Data.Services.Client.MergeOption> tarafından ayarlanan kimlik çözümleme kurallarını izlediği anlamına gelir.

Aşağıda, sonuçlar varlık ve varlık olmayan türlere yansıtılanmakta olan davranışlar açıklanmaktadır:

**Başlatıcıları kullanarak yeni bir öngörülen örnek oluşturma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Varlık türü: destekleniyor

- Varlık olmayan tür: destekleniyor

**Oluşturucular kullanarak yeni bir öngörülen örnek oluşturma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Varlık türü: bir <xref:System.NotSupportedException> tetiklenir.

- Varlık olmayan tür: destekleniyor

**Bir özellik değerini dönüştürmek için projeksiyonu kullanma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Varlık türü: Bu dönüşüm, varlık türleri için desteklenmez çünkü bu, başka bir varlığa ait veri kaynağındaki verilerin üzerine yazılmasına neden olabilir. <xref:System.NotSupportedException> tetiklenir.

- Varlık olmayan tür: destekleniyor

<a name="considerations"></a>

## <a name="projection-considerations"></a>Projeksiyon konuları

Bir sorgu projeksiyonu tanımlarken aşağıdaki ek konular geçerlidir.

- Atom biçimi için özel akışlar tanımladığınızda, tanımlanmış özel eşlemelere sahip tüm varlık özelliklerinin projeksiyonda eklendiğinden emin olmanız gerekir. Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir. Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).

- Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen türe ekleme yapıldığında, istemcideki projeksiyonde bulunmayan özellikler varsayılan değerlerine ayarlanır...

- Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen tür için güncelleştirmeler yapıldığında, istemcideki projeksiyonde bulunmayan mevcut değerlerin üzerine başlatılmamış varsayılan değerler eklenir.

- Projeksiyon karmaşık bir özellik içerdiğinde, tüm karmaşık nesne döndürülmelidir.

- Projeksiyon bir gezinti özelliği içerdiğinde, ilgili nesneler <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemini çağırmak zorunda kalmadan örtük olarak yüklenir. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi, tasarlanan bir sorguda kullanım için desteklenmiyor.

- İstemci üzerindeki sorgu tahminleri sorguları, istek URI 'sindeki `$select` sorgu seçeneğini kullanacak şekilde çevrilir. Projeksiyon içeren bir sorgu, `$select` sorgu seçeneğini desteklemeyen [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] önceki bir sürümüne karşı yürütüldüğünde bir hata döndürülür. Bu durum, veri hizmeti için <xref:System.Data.Services.DataServiceBehavior> <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>değere ayarlandığında de oluşabilir. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).

Daha fazla bilgi için bkz. [nasıl yapılır: Proje sorgu sonuçları](how-to-project-query-results-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
