---
title: LINQ to SQL Nesne Modeli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 7ce759de004d479f5162d2ce3a965f5c40afa450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917608"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL Nesne Modeli
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], geliştiricinin programlama dilinde ifade nesne modeli, ilişkisel veritabanı ve veri modelini eşlendi. Veriler üzerinde işlemler sonra nesne modeline göre yürütülür.  
  
 Bu senaryoda, veritabanı komutlarını dağıttığınız değil (örneğin, `INSERT`) veritabanı. Bunun yerine, değerleri değiştirin ve, nesne modeli içinde bir yöntem yürütülemez. Değiştirirse, gönderme ve veritabanını sorgulamak istediğiniz zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] isteklerinizi doğru SQL komutlara çevirir ve söz konusu komutları veritabanına gönderir.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 En temel öğeleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli ve bunların ilişkisel veri modelindeki öğeler aşağıdaki tabloda özetlenmiştir:  
  
|LINQ to SQL nesne modeli|İlişkisel veri modeli|  
|------------------------------|---------------------------|  
|Varlık sınıfı|Tablo|  
|Sınıf üyesi|Sütun|  
|İlişkilendirme|Yabancı anahtar ilişkisi|  
|Yöntem|Saklı yordamı veya işlevi|  
  
> [!NOTE]
>  Aşağıdaki açıklamaları kuralları ve ilişkisel veri modeli temel bilgiye sahip olduğunuzu varsaymaktadır.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL varlık sınıfları ve veritabanı tabloları  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bir veritabanı tablosu tarafından temsil edilen bir *varlık sınıfı*. Bir varlık sınıfı sınıfı bir veritabanı tablosu ile ilişkilendiren özel bilgileri kullanarak sınıf ek açıklama dışında oluşturacağınız başka bir sınıf gibidir. Özel bir öznitelik ekleyerek bu ek açıklama yapın (<xref:System.Data.Linq.Mapping.TableAttribute>) aşağıdaki örnekte olduğu gibi sınıf bildirimi için:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Veritabanı tabloları (diğer bir deyişle, varlık sınıfları) kaydedilebilir olarak yalnızca sınıfların örneklerini bildirilmiş.  
  
 Daha fazla bilgi için tablo özniteliği bölümüne bakın. [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL sınıf üyeleri ve veritabanı sütunları  
 Sınıflar içeren tablolar ilişkilendirme ek olarak, alanlar ve Özellikler veritabanı sütunları temsil etmek için belirleyin. Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tanımlar <xref:System.Data.Linq.Mapping.ColumnAttribute> öznitelik, aşağıdaki örnekte olduğu gibi:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Yalnızca alanlar ve Özellikler sütunlarıyla eşlenen kalıcı veya veritabanından alınır. Bu sütunlar geçici uygulama mantığınızın parçaları olarak kabul edilir olarak bildirilmedi.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliğine sahip çeşitli sütunları (örneğin, bir birincil anahtar sütunu temsil eden olarak bir üye tanımlayarak) temsil eden bu üyeleri özelleştirmek için kullanabileceğiniz özellikler. Daha fazla bilgi için sütun özniteliği bölümüne bakın. [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL ilişkilendirmeleri ve veritabanı yabancı anahtar ilişkileri  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uygulayarak veritabanı ilişkileri (örneğin, yabancı anahtar ilişkileri birincil anahtar) temsil eden <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği. Kod, aşağıdaki Segmentte `Order` sınıfı içeren bir `Customer` olan özellik bir <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği. Bu özellik ve onun özniteliğini `Order` ilişkisi olan sınıf `Customer` sınıfı.  
  
 Aşağıdaki örnekte gösterildiği kod `Customer` özelliğinden `Order` sınıfı.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Daha fazla bilgi için ilişkilendirme özniteliği bölümüne bakın. [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL yöntemleri ve veritabanı saklı yordamları  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler saklı yordamlar ve kullanıcı tanımlı işlevler. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], böylece istemci kodundan kesin bir şekilde erişebilir istemci nesneleri için bu veritabanında tanımlı soyutlama eşleyin. Yöntem imzaları mümkün olduğunca yakın yordamları ve işlevleri veritabanında tanımlanan imzalarını benzer. Bu yöntemleri bulmak için IntelliSense'i kullanabilirsiniz.  
  
 Bir sonuç kümesi diğer bir deyişle eşlenmiş bir yordam çağrısı tarafından döndürülen bir türü kesin belirlenmiş koleksiyonudur.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] saklı yordamları ve işlevleri kullanarak yöntemlere eşler <xref:System.Data.Linq.Mapping.FunctionAttribute> ve <xref:System.Data.Linq.Mapping.ParameterAttribute> öznitelikleri. Saklı yordamlar temsil eden yöntemleri temsil eden kullanıcı tanımlı işlevleri tarafından kullanılanlardan ayırt edici <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> özelliği. Bu özellik ayarlanırsa `false` (varsayılan), bir saklı yordam yöntemi temsil eder. Bu ayarlanırsa `true`, bir veritabanı işlevi yöntemi temsil eder.  
  
> [!NOTE]
>  Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamları ve kullanıcı tanımlı işlevleri için eşlenmiş yöntemleri oluşturma.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Daha fazla bilgi için işlev özniteliği ve depolanan yordam öznitelik parametre özniteliği bölümlerine bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) ve [saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
