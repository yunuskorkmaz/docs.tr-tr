---
title: Yansıma sağlayıcısı (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
ms.openlocfilehash: 0eeb223093d709cfe2722c2ad7cf622164eab32f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568870"
---
# <a name="reflection-provider-wcf-data-services"></a>Yansıma sağlayıcısı (WCF Veri Hizmetleri)

Bir veri modelinden Entity Framework aracılığıyla veri sunmaya ek olarak, WCF Veri Hizmetleri varlık tabanlı bir modelde kesin olarak tanımlanmayan verileri ortaya çıkarabilirler. Yansıma sağlayıcısı, <xref:System.Linq.IQueryable%601> arabirimini uygulayan türleri döndüren sınıflardaki verileri kullanıma sunar. WCF Veri Hizmetleri, bu sınıflar için bir veri modeli çıkarması için yansıma kullanır ve sunulan <xref:System.Linq.IQueryable%601> türlerine karşı dil ile tümleşik sorgu (LINQ) tabanlı sorgulara kaynak için adres tabanlı sorguları çevirebilir.

> [!NOTE]
> <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan herhangi bir sınıftan <xref:System.Linq.IQueryable%601> arabirimini döndürmek için <xref:System.Linq.Queryable.AsQueryable%2A> yöntemini kullanabilirsiniz. Bu, çoğu genel koleksiyon türünün veri hizmetiniz için bir veri kaynağı olarak kullanılmasını sağlar.

Yansıma sağlayıcısı tür hiyerarşilerini destekler. Daha fazla bilgi için bkz. [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md).

## <a name="inferring-the-data-model"></a>Veri modelini erteleme

Veri hizmeti oluşturduğunuzda, sağlayıcı yansıma kullanarak veri modelini oluşturur. Aşağıdaki listede, yansıma sağlayıcısının veri modelini nasıl gösterdiği gösterilmektedir:

- Varlık kapsayıcısı-verileri bir <xref:System.Linq.IQueryable%601> örneği döndüren özellikler olarak kullanıma sunan sınıf. Yansıma tabanlı bir veri modeli adresleyebilirsiniz, varlık kapsayıcısı hizmetin kökünü temsil eder. Verilen bir ad alanı için yalnızca bir varlık kapsayıcı sınıfı desteklenir.

- Varlık kümeleri-<xref:System.Linq.IQueryable%601> örnekleri döndüren Özellikler varlık kümesi olarak değerlendirilir. Varlık kümeleri doğrudan sorgudaki kaynaklar olarak karşılanır. Varlık kapsayıcısındaki yalnızca bir özellik, belirli bir türün <xref:System.Linq.IQueryable%601> örneğini döndürebilir.

- Varlık türleri-varlık kümesinin döndürdüğü <xref:System.Linq.IQueryable%601> türü `T`. Devralma hiyerarşisinin parçası olan sınıflar, yansıma sağlayıcısı tarafından eşdeğer bir varlık türü hiyerarşisine çevrilir.

- Varlık anahtarları-varlık türü olan her veri sınıfının bir anahtar özelliği olmalıdır. Bu özellik <xref:System.Data.Services.Common.DataServiceKeyAttribute> özniteliğiyle nitelendirilen (`[DataServiceKeyAttribute]`).

    > [!NOTE]
    > <xref:System.Data.Services.Common.DataServiceKeyAttribute> özniteliğini yalnızca varlık türünün bir örneğini benzersiz bir şekilde tanımlamak için kullanılabilecek bir özelliğe uygulamanız gerekir. Bu öznitelik, bir gezinti özelliğine uygulandığında yoksayılır.

- Varlık türü özellikleri-Varlık anahtarından farklı olarak, yansıma sağlayıcısı varlık türü olan bir sınıfın erişilebilir, Dizin Oluşturucu olmayan özelliklerini aşağıdaki gibi değerlendirir:

  - Özellik bir basit tür döndürürse, özelliğin bir varlık türünün özelliği olduğu varsayılır.

  - Özellik aynı zamanda bir varlık türü olan bir tür döndürürse, özelliğin, çoktan bire bir veya bire bir ilişkinin "bir" sonunu temsil eden bir gezinti özelliği olduğu varsayılır.

  - Özellik bir varlık türünün <xref:System.Collections.Generic.IEnumerable%601> döndürürse, özelliğin bir-çok veya çoktan çoğa ilişkisinin "çok" sonunu temsil eden bir gezinti özelliği olduğu varsayılır.

  - Özelliğin dönüş türü bir değer türü ise, özelliği karmaşık bir türü temsil eder.

> [!NOTE]
> Varlık ilişkisel modelini temel alan bir veri modelinden farklı olarak, yansıma sağlayıcısını temel alan modeller ilişkisel verileri anlamayabilir. İlişkisel verileri WCF Veri Hizmetleri üzerinde göstermek için Entity Framework kullanmanız gerekir.

## <a name="data-type-mapping"></a>Veri türü eşleme

.NET Framework sınıflarından bir veri modeli çıkarsandığınızda, veri modelindeki temel türler aşağıdaki şekilde .NET Framework veri türlerine eşlenir:

|.NET Framework veri türü|Veri modeli türü|
|------------------------------|---------------------|
|<xref:System.Byte>`[]`|`Edm.Binary`|
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

Bu tür bir veri modeli aracılığıyla kullanıma sunulan veri güncelleştirmelerine izin vermek için, yansıma sağlayıcısı bir <xref:System.Data.Services.IUpdatable> arabirimini tanımlar. Bu arabirim, veri hizmetine güncelleştirmeleri sunulma türlerine nasıl kalıcı hale getirebileceği konusunda yönlendirir. Veri modeli tarafından tanımlanan kaynaklara yönelik güncelleştirmeleri etkinleştirmek için, varlık kapsayıcı sınıfı <xref:System.Data.Services.IUpdatable> arabirimini gerçekleştirmelidir. <xref:System.Data.Services.IUpdatable> arabirimi uygulamasına bir örnek için bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).

<xref:System.Data.Services.IUpdatable> arabirimi, güncelleştirmelerin yansıma sağlayıcısı kullanılarak veri kaynağına yayabilmesi için aşağıdaki üyelerin uygulanması gerekir:

|Üye|Açıklama|
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

WCF Veri Hizmetleri bir varlık için eşzamanlılık belirteci tanımlamanızı sağlayarak iyimser eşzamanlılık modelini destekler. Varlığın bir veya daha fazla özelliği içeren bu eşzamanlılık belirteci, istenen, güncellenen veya silinen verilerde bir değişikliğin oluşup oluşmadığını anlamak için veri hizmeti tarafından kullanılır. İstekteki eTag öğesinden alınan belirteç değerleri varlığın geçerli değerlerinden farklıysa, veri hizmeti tarafından bir özel durum oluşturulur. <xref:System.Data.Services.ETagAttribute>, yansıma sağlayıcısında bir eşzamanlılık belirteci tanımlamak için bir varlık türüne uygulanır. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).

## <a name="using-linq-to-sql-with-the-reflection-provider"></a>Yansıma sağlayıcısıyla LINQ to SQL kullanma

Entity Framework varsayılan olarak yerel olarak desteklendiğinden, WCF Veri Hizmetleri ilişkisel verileri kullanmaya yönelik önerilen veri sağlayıcısıdır. Ancak, bir veri hizmetiyle LINQ to SQL sınıfları kullanmak için yansıma sağlayıcısını kullanabilirsiniz. LINQ to SQL Nesne İlişkisel Tasarımcısı (O/R Designer) tarafından oluşturulan <xref:System.Data.Linq.DataContext> yöntemler tarafından döndürülen <xref:System.Data.Linq.Table%601> sonuç kümeleri <xref:System.Linq.IQueryable%601> arabirimini uygular. Bu, yansıma sağlayıcısının bu yöntemlere erişmesini ve oluşturulan LINQ to SQL sınıflarını kullanarak SQL Server varlık verilerini döndürmesini sağlar. Ancak, LINQ to SQL <xref:System.Data.Services.IUpdatable> arabirimini uygulamadığından, <xref:System.Data.Services.IUpdatable> uygulamasını eklemek için var olan <xref:System.Data.Linq.DataContext> parçalı sınıfı genişleten kısmi bir sınıf eklemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
