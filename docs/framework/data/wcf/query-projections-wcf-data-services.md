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
ms.openlocfilehash: 44e99db2d75fcd8e84f91f0afc8da54ff6c3f707
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931164"
---
# <a name="query-projections-wcf-data-services"></a>Sorgu tahminleri (WCF Veri Hizmetleri)

Projeksiyon, yanıtta bir varlığın yalnızca [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] belirli özelliklerinin döndürülüp döndürülmeyeceğini belirterek, bir sorgu tarafından döndürülen akıştaki veri miktarını azaltmak için içinde bir mekanizma sağlar. Daha fazla bilgi için bkz [. OData: Sistem sorgu seçeneğini belirleyin ($select)](https://go.microsoft.com/fwlink/?LinkId=186076).

Bu konu, bir sorgu projeksiyonu, varlık ve varlık olmayan türler için gereksinimlerin ne olduğunu, öngörülen sonuçlara yönelik güncelleştirmeler yapmayı, tasarlanan türleri oluşturmayı ve bazı projeksiyon konularını listeler.

## <a name="defining-a-query-projection"></a>Sorgu projeksiyonu tanımlama

Bir URI 'de `$select` sorgu seçeneğini kullanarak veya bir LINQ sorgusunda [Select](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesini (Visual Basic içinde[seçin](../../../visual-basic/language-reference/queries/select-clause.md) ) kullanarak bir sorguya projeksiyon yan tümcesi ekleyebilirsiniz. Döndürülen varlık verileri, istemci üzerindeki varlık türlerine veya varlık olmayan türlere yansıtılmalıdır. Bu konudaki örneklerde bir LINQ sorgusunda `select` yan tümcesinin nasıl kullanılacağı gösterilmektedir.

> [!IMPORTANT]
> Tasarlanan türlerde yapılan güncelleştirmeleri kaydettiğinizde veri hizmetinde veri kaybı oluşabilir. Daha fazla bilgi için bkz. [projeksiyon konuları](#considerations).

## <a name="requirements-for-entity-and-non-entity-types"></a>Varlık ve varlık olmayan türler için gereksinimler

Varlık türlerinin, varlık anahtarını oluşturan bir veya daha fazla kimlik özelliği olmalıdır. Varlık türleri, istemcilerde aşağıdaki yollarla tanımlanmıştır:

- <xref:System.Data.Services.Common.DataServiceKeyAttribute> Ya<xref:System.Data.Services.Common.DataServiceEntityAttribute> da türünü uygulayarak.

- Türün adında `ID`bir özelliği olduğunda.

- Türün Type adlı`ID`bir özelliği varsa, burada tür adıdır .

Varsayılan olarak, sorgu sonuçlarını istemcide tanımlı bir türe proje yaparken, projeksiyde istenen özellikler istemci türünde bulunmalıdır. Ancak, `true` <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> özelliği içinbirdeğeribelirttiğinizde,projeksiyondabelirtilenözelliklerinistemcitüründegerçekleşmesigerekmez.<xref:System.Data.Services.Client.DataServiceContext>

### <a name="making-updates-to-projected-results"></a>Yansıtılan sonuçlara güncelleştirmeler yapılıyor

Sorgu sonuçlarını istemcideki <xref:System.Data.Services.Client.DataServiceContext> varlık türlerine proje yaparken, bu nesneleri, <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntem çağrıldığında veri hizmetine geri gönderilmek üzere güncelleştirmeler ile izleyebilir. Ancak, istemcideki varlık olmayan türlere yapılan veriler veri hizmetine geri gönderilemez. Bunun nedeni, varlık örneğini tanımlamak için bir anahtar olmadığı için veri hizmeti veri kaynağındaki doğru varlığı güncelleştiremez. Varlık dışı türler öğesine <xref:System.Data.Services.Client.DataServiceContext>eklenmez.

Veri hizmetinde tanımlanan bir veya daha fazla varlık türünün bir veya daha fazla özelliği, varlığın yansıtıldıkları istemci türünde gerçekleşmezse, yeni varlıkların ekleme işlemi bu eksik özellikleri içermez. Bu durumda, mevcut varlıklarda yapılan güncelleştirmeler bu eksik özellikleri **de** içermez. Bu tür bir özellik için bir değer varsa, güncelleştirme onu veri kaynağında tanımlandığı şekilde özellik için varsayılan değere sıfırlar.

### <a name="creating-projected-types"></a>Öngörülen türler oluşturuluyor

Aşağıdaki örnek, `Customers` türün adresle ilgili özelliklerini, istemcisinde tanımlanmış olan ve bir varlık türü olarak öznitelikli yeni `CustomerAddress` bir türe uygulayan anonim bir LINQ sorgusu kullanır:

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

Bu örnekte, nesne Başlatıcısı, bir oluşturucuyu çağırmak yerine `CustomerAddress` türün yeni bir örneğini oluşturmak için kullanılır. Oluşturucular varlık türlerine yansıtılamayan desteklenmez, ancak varlık dışı ve anonim türler halinde yansıtılarınızda kullanılabilirler. Bir `CustomerAddress` varlık türü olduğundan, değişiklikler yapılabilir ve veri hizmetine geri gönderilebilir.

Ayrıca, `Customer` türdeki veriler anonim bir tür yerine `CustomerAddress` varlık türünün bir örneğine yansıtıldır. Anonim türlere yansıtma desteklenir, ancak anonim türler varlık dışı türler olarak değerlendirildiğinden veriler salt okunurdur.

<xref:System.Data.Services.Client.MergeOption> Ayarları ,<xref:System.Data.Services.Client.DataServiceContext> sorgu projeksiyonu sırasında kimlik çözümlemesi için kullanılır. Bu, `Customer` türünün bir örneği <xref:System.Data.Services.Client.DataServiceContext>içinde zaten mevcutsa, aynı kimliğe `CustomerAddress` sahip bir örneği, tarafından ayarlanan kimlik çözümleme kurallarını takip eder.<xref:System.Data.Services.Client.MergeOption>

Aşağıda, sonuçlar varlık ve varlık olmayan türlere yansıtılanmakta olan davranışlar açıklanmaktadır:

**Başlatıcıları kullanarak yeni bir öngörülen örnek oluşturma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- Varlık türü: Desteklenir

- Varlık olmayan tür: Desteklenir

**Oluşturucular kullanarak yeni bir öngörülen örnek oluşturma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- Varlık türü: Bir <xref:System.NotSupportedException> oluşturulur.

- Varlık olmayan tür: Desteklenir

**Bir özellik değerini dönüştürmek için projeksiyonu kullanma**

- Örnek:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- Varlık türü: Bu dönüşüm, varlık türleri için desteklenmez çünkü bu, başka bir varlığa ait veri kaynağındaki verilerin üzerine yazılmasına neden olabilir. Bir <xref:System.NotSupportedException> oluşturulur.

- Varlık olmayan tür: Desteklenir

<a name="considerations"></a>

## <a name="projection-considerations"></a>Projeksiyon konuları

Bir sorgu projeksiyonu tanımlarken aşağıdaki ek konular geçerlidir.

- Atom biçimi için özel akışlar tanımladığınızda, tanımlanmış özel eşlemelere sahip tüm varlık özelliklerinin projeksiyonda eklendiğinden emin olmanız gerekir. Eşlenen bir varlık özelliği projeksiyonde yer olmadığında veri kaybı oluşabilir. Daha fazla bilgi için bkz. [akış özelleştirmesi](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).

- Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen türe ekleme yapıldığında, istemcideki projeksiyonde bulunmayan özellikler varsayılan değerlerine ayarlanır...

- Veri hizmetinin veri modelindeki varlık özelliklerinin tümünü içermeyen bir öngörülen tür için güncelleştirmeler yapıldığında, istemcideki projeksiyonde bulunmayan mevcut değerlerin üzerine başlatılmamış varsayılan değerler eklenir.

- Projeksiyon karmaşık bir özellik içerdiğinde, tüm karmaşık nesne döndürülmelidir.

- Projeksiyon bir gezinti özelliği içerdiğinde, ilgili nesneler <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi çağırmak zorunda kalmadan örtük olarak yüklenir. Yöntem <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> , tasarlanan bir sorguda kullanım için desteklenmiyor.

- İstemcideki sorgu tahminleri sorguları, istek URI 'sindeki `$select` sorgu seçeneğini kullanacak şekilde çevrilir. Yansıtma içeren bir sorgu, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] `$select` sorgu seçeneğini desteklemeyen önceki bir sürümüne karşı yürütüldüğünde bir hata döndürülür. Bu durum, veri hizmeti <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> <xref:System.Data.Services.DataServiceBehavior> için öğesinin bir değerine <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>ayarlandığı durumlarda da gerçekleşebilir. Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).

Daha fazla bilgi için [nasıl yapılır: Proje sorgu sonuçları](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
