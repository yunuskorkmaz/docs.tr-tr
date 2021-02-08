---
description: 'Hakkında daha fazla bilgi edinin: yansıma sağlayıcısı (WCF Veri Hizmetleri)'
title: Yansıma sağlayıcısı (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: e09c9a86bb940681d8de24f5082919aea897795d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794929"
---
# <a name="reflection-provider-wcf-data-services"></a>Yansıma sağlayıcısı (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Bir veri modelinden Entity Framework aracılığıyla veri sunmaya ek olarak, WCF Veri Hizmetleri varlık tabanlı bir modelde kesin olarak tanımlanmayan verileri ortaya çıkarabilirler. Yansıma sağlayıcısı, arabirimi uygulayan türleri döndüren sınıflarda verileri kullanıma sunar <xref:System.Linq.IQueryable%601> . WCF Veri Hizmetleri, bu sınıflar için bir veri modeli çıkarması için yansıma kullanır ve sunulan türlere karşı dil ile tümleşik sorgu (LINQ) tabanlı sorgulara kaynak ile adres tabanlı sorguları çevirebilir <xref:System.Linq.IQueryable%601> .

> [!NOTE]
> <xref:System.Linq.Queryable.AsQueryable%2A>Arabirimini uygulayan herhangi bir sınıftan bir arabirim döndürmek için yöntemini kullanabilirsiniz <xref:System.Linq.IQueryable%601> <xref:System.Collections.Generic.IEnumerable%601> . Bu, çoğu genel koleksiyon türünün veri hizmetiniz için bir veri kaynağı olarak kullanılmasını sağlar.

Yansıma sağlayıcısı tür hiyerarşilerini destekler. Daha fazla bilgi için bkz. [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Veri modelini erteleme

Veri hizmeti oluşturduğunuzda, sağlayıcı yansıma kullanarak veri modelini oluşturur. Aşağıdaki listede, yansıma sağlayıcısının veri modelini nasıl gösterdiği gösterilmektedir:

- Varlık kapsayıcısı-verileri bir örnek döndüren özellikler olarak kullanıma sunan sınıf <xref:System.Linq.IQueryable%601> . Yansıma tabanlı bir veri modeli adresleyebilirsiniz, varlık kapsayıcısı hizmetin kökünü temsil eder. Verilen bir ad alanı için yalnızca bir varlık kapsayıcı sınıfı desteklenir.

- Varlık kümeleri-örnek döndüren Özellikler <xref:System.Linq.IQueryable%601> varlık kümesi olarak değerlendirilir. Varlık kümeleri doğrudan sorgudaki kaynaklar olarak karşılanır. Varlık kapsayıcısındaki yalnızca bir özellik, <xref:System.Linq.IQueryable%601> belirli bir türün örneğini döndürebilir.

- Varlık türleri- `T` <xref:System.Linq.IQueryable%601> varlık kümesinin döndürdüğü öğesinin türü. Devralma hiyerarşisinin parçası olan sınıflar, yansıma sağlayıcısı tarafından eşdeğer bir varlık türü hiyerarşisine çevrilir.

- Varlık anahtarları-varlık türü olan her veri sınıfının bir anahtar özelliği olmalıdır. Bu özellik <xref:System.Data.Services.Common.DataServiceKeyAttribute> () özniteliğiyle nitelendirilen `[DataServiceKeyAttribute]` .

    > [!NOTE]
    > <xref:System.Data.Services.Common.DataServiceKeyAttribute>Özniteliği yalnızca varlık türünün bir örneğini benzersiz bir şekilde tanımlamak için kullanılabilecek bir özelliğe uygulamanız gerekir. Bu öznitelik, bir gezinti özelliğine uygulandığında yoksayılır.

- Varlık türü özellikleri-Varlık anahtarından farklı olarak, yansıma sağlayıcısı varlık türü olan bir sınıfın erişilebilir, Dizin Oluşturucu olmayan özelliklerini aşağıdaki gibi değerlendirir:

  - Özellik bir basit tür döndürürse, özelliğin bir varlık türünün özelliği olduğu varsayılır.

  - Özellik aynı zamanda bir varlık türü olan bir tür döndürürse, özelliğin, çoktan bire bir veya bire bir ilişkinin "bir" sonunu temsil eden bir gezinti özelliği olduğu varsayılır.

  - Özelliği <xref:System.Collections.Generic.IEnumerable%601> bir varlık türünden bir döndürürse, özelliğin bir-çok veya çoktan çoğa ilişkisinin "çok" sonunu temsil eden bir gezinti özelliği olduğu varsayılır.

  - Özelliğin dönüş türü bir değer türü ise, özelliği karmaşık bir türü temsil eder.

> [!NOTE]
> Varlık ilişkisel modelini temel alan bir veri modelinden farklı olarak, yansıma sağlayıcısını temel alan modeller ilişkisel verileri anlamayabilir. İlişkisel verileri WCF Veri Hizmetleri üzerinde göstermek için Entity Framework kullanmanız gerekir.

## <a name="data-type-mapping"></a>Veri türü eşleme

.NET Framework sınıflarından bir veri modeli çıkarsandığınızda, veri modelindeki temel türler aşağıdaki şekilde .NET Framework veri türlerine eşlenir:

|.NET Framework veri türü|Veri modeli türü|
|------------------------------|---------------------|
|<xref:System.Byte> `[]`|`Edm.Binary`|
|<xref:System.Boolean>|`Edm.Boolean`|
|<xref:System.Byte>|`Edm.Byte`|
|<xref:System.DateTime>|`Edm.DateTime`|
|<xref:System.Decimal>|`Edm.Decimal`|
|<xref:System.Double>|`Edm.Double`|
|<xref:System.Guid>|`Edm.Guid`|
|<xref:System.Int16>|`Edm.Int16`|
|<xref:System.Int32>|`Edm.Int32`|
|<xref:System.Int64>|`Edm.Int64`|
|<xref:System.SByte>|`Edm.SByte`|
|<xref:System.Single>|`Edm.Single`|
|<xref:System.String>|`Edm.String`|

> [!NOTE]
> .NET Framework Nullable değer türleri, null atanamayan karşılık gelen değer türleriyle aynı veri modeli türleriyle eşlenir.

## <a name="enabling-updates-in-the-data-model"></a>Veri modelinde güncelleştirmeleri etkinleştirme

Bu tür bir veri modeli üzerinden sunulan verilere yönelik güncelleştirmelere izin vermek için, yansıma sağlayıcısı bir <xref:System.Data.Services.IUpdatable> arabirimi tanımlar. Bu arabirim, veri hizmetine güncelleştirmeleri sunulma türlerine nasıl kalıcı hale getirebileceği konusunda yönlendirir. Veri modeli tarafından tanımlanan kaynakların güncelleştirmelerini etkinleştirmek için, varlık kapsayıcı sınıfı <xref:System.Data.Services.IUpdatable> arabirimini uygulamalıdır. Arabirimin bir uygulamasına bir örnek için <xref:System.Data.Services.IUpdatable> bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).

<xref:System.Data.Services.IUpdatable>Bu arabirim, güncelleştirmelerin yansıma sağlayıcısı kullanılarak veri kaynağına yayabilmesi için aşağıdaki üyelerin uygulanması gerekir:

|Üye|Description|
|------------|-----------------|
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|Bir gezinti özelliğinden erişilen ilgili nesneler koleksiyonuna nesne ekleme işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|Verilerde bekleyen değişiklikleri iptal eden işlevselliği sağlar.|
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|Belirtilen kapsayıcıda yeni bir kaynak oluşturmak için işlevsellik sağlar.|
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|Kaynak silme işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|Belirli bir sorgu ve tür adı tarafından tanımlanan bir kaynağı alma işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|, Bir kaynağın bir özelliğinin değerini döndürecek işlevselliği sağlar.|
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|Bir nesneyi bir gezinti özelliğinden erişilen ilgili nesneler koleksiyonuna kaldırma işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|Belirtilen bir kaynağı güncelleştirmek için işlevsellik sağlar.|
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|Belirli bir nesne örneği tarafından temsil edilen kaynağı döndürmek için işlevsellik sağlar.|
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|Bekleyen tüm değişiklikleri kaydetme işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|Bir gezinti özelliği kullanarak ilgili nesne başvurusunu ayarlama işlevlerini sağlar.|
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|, Bir kaynağın özelliğinin değerini ayarlama işlevlerini sağlar.|

## <a name="handling-concurrency"></a>Eşzamanlılığı İşleme

WCF Veri Hizmetleri bir varlık için eşzamanlılık belirteci tanımlamanızı sağlayarak iyimser eşzamanlılık modelini destekler. Varlığın bir veya daha fazla özelliği içeren bu eşzamanlılık belirteci, istenen, güncellenen veya silinen verilerde bir değişikliğin oluşup oluşmadığını anlamak için veri hizmeti tarafından kullanılır. İstekteki eTag öğesinden alınan belirteç değerleri varlığın geçerli değerlerinden farklıysa, veri hizmeti tarafından bir özel durum oluşturulur. , <xref:System.Data.Services.ETagAttribute> Yansıma sağlayıcısında bir eşzamanlılık belirteci tanımlamak için bir varlık türüne uygulanır. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Yansıma sağlayıcısıyla LINQ to SQL kullanma

Entity Framework varsayılan olarak yerel olarak desteklendiğinden, WCF Veri Hizmetleri ilişkisel verileri kullanmaya yönelik önerilen veri sağlayıcısıdır. Ancak, bir veri hizmetiyle LINQ to SQL sınıfları kullanmak için yansıma sağlayıcısını kullanabilirsiniz. <xref:System.Data.Linq.Table%601> <xref:System.Data.Linq.DataContext> LINQ to SQL nesne ilişkisel Tasarımcısı (O/R Designer) tarafından oluşturulan yöntemler tarafından döndürülen sonuç kümeleri, <xref:System.Linq.IQueryable%601> arabirimini uygular. Bu, yansıma sağlayıcısının bu yöntemlere erişmesini ve oluşturulan LINQ to SQL sınıflarını kullanarak SQL Server varlık verilerini döndürmesini sağlar. Ancak, LINQ to SQL <xref:System.Data.Services.IUpdatable> arabirimini uygulamadığından, <xref:System.Data.Linq.DataContext> uygulamayı eklemek için mevcut kısmi sınıfı genişleten kısmi bir sınıf eklemeniz gerekir <xref:System.Data.Services.IUpdatable> . Daha fazla bilgi için bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
