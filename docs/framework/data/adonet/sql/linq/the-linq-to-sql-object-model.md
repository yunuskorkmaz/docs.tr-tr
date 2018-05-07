---
title: LINQ to SQL nesne modeli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: c716847c60611a6e8a2911d4b9ae2f1683d2cdd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL nesne modeli
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], geliştirici programlama dilinde ifade nesne modeli ilişkisel veritabanı veri modeline eşlendi. Veriler üzerinde işlemler nesne modeline göre daha sonra yürütülür.  
  
 Bu senaryoda, veritabanı komutları sorun değildir (örneğin, `INSERT`) veritabanı. Bunun yerine, değerleri değiştirin ve nesne modeli içindeki bir yöntem yürütülemez. Veritabanı veya değiştiğinde, gönderme sorgulamak istediğiniz zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] isteklerinizi doğru SQL komutlara çevirir ve bu komutları veritabanına gönderir.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 En temel öğeleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli ve ilişkilerini ilişkisel veri modeli öğeleri için aşağıdaki tabloda özetlenmiştir:  
  
|LINQ to SQL nesne modeli|İlişkisel veri modeli|  
|------------------------------|---------------------------|  
|Varlık sınıfı|Tablo|  
|Sınıf üyesi|Sütun|  
|İlişkilendirme|Yabancı anahtar ilişkisi|  
|Yöntem|Saklı yordam veya işlev|  
  
> [!NOTE]
>  Aşağıdaki açıklamaları, kuralları ve ilişkisel veri modelini temel bilgiye sahip olduğunuzu varsayar.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ-SQL sınıflar ve veritabanı tabloları  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bir veritabanı tablosu tarafından temsil edilen bir *varlık sınıfı*. Bir varlık sınıfı sınıfı bir veritabanı tablosu ile ilişkilendirir özel bilgileri kullanarak sınıfı açıklama dışında oluşturacağınız başka bir sınıf gibidir. Özel bir öznitelik ekleyerek bu ek açıklama yapın (<xref:System.Data.Linq.Mapping.TableAttribute>) aşağıdaki örnekteki gibi sınıf bildirimi için:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Tabloları (diğer bir deyişle, varlık sınıflar) veritabanına kaydedilebilir gibi sınıfların yalnızca örneklerini bildirildi.  
  
 Daha fazla bilgi için tablo özniteliği bölümüne bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ-SQL sınıf üyeleri ve veritabanı sütunları  
 Sınıfları tablolarla ilişkilendirme yanı sıra, alanlar veya veritabanı sütunlarını göstermek için özellikleri belirtin. Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tanımlar <xref:System.Data.Linq.Mapping.ColumnAttribute> aşağıdaki örnekteki gibi öznitelik:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Yalnızca alanlar ve sütunlarla eşlenen özellikler için kalıcı veya veritabanından alınır. Bu sütunları geçici uygulama mantığınızın parçaları olarak kabul edilen olarak bildirilmedi.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliğine sahip çeşitli sütunlar (örneğin, birincil anahtar sütunu temsil eden olarak bir üye belirleme) temsil eder Bu üyeleri özelleştirmek için kullanabileceğiniz özellikler. Daha fazla bilgi için sütun özniteliği bölümüne bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ-SQL ilişkileri ve veritabanı yabancı anahtar ilişkileri  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uygulayarak veritabanı ilişkilendirmeleri (örneğin, yabancı anahtar birincil anahtar ilişkileri) temsil eden <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği. Kod, aşağıdaki kesimdeki `Order` sınıfı içeren bir `Customer` sahip özellik bir <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği. Bu özellik ve onun özniteliğini sağlayın `Order` sınıfı bir ilişkisi olan `Customer` sınıfı.  
  
 Aşağıdaki örnekte gösterildiği kod `Customer` özelliğinden `Order` sınıfı.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Daha fazla bilgi için ilişki özniteliğini bölümüne bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ-SQL yöntemleri ve veritabanı saklı yordamları  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] saklı yordamlar ve kullanıcı tanımlı işlevler destekler. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], böylece istemci kodundan kesin türü belirtilmiş bir şekilde erişebilir istemci nesnelere bu veritabanı tanımlanan soyutlamalar eşleyin. Yöntem imzaları mümkün olduğunca yakın yordamları ve işlevleri veritabanı içinde tanımlanan imzalarını benzer. Bu yöntemler bulmak için IntelliSense kullanabilirsiniz.  
  
 Bir sonuç kümesi olan eşlenen bir yordam için bir çağrı tarafından döndürülen bir türü kesin belirlenmiş koleksiyonudur.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] saklı yordamları ve işlevleri kullanarak yöntemlere eşlemeleri <xref:System.Data.Linq.Mapping.FunctionAttribute> ve <xref:System.Data.Linq.Mapping.ParameterAttribute> öznitelikleri. Saklı yordamlar temsil eden yöntemleri temsil eden kullanıcı tanımlı işlevler tarafından kullanılanlardan ayırt <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> özelliği. Bu özellik ayarlanmışsa `false` (varsayılan), bir saklı yordam yöntemi temsil eder. Bu ayarlanırsa `true`, yöntemi bir veritabanı işlevi temsil eder.  
  
> [!NOTE]
>  Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] saklı yordamları ve kullanıcı tanımlı işlevler eşlenen yöntemleri oluşturmak için.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Daha fazla bilgi için işlevi özniteliği, saklı yordam özniteliği ve parametre özniteliği bölümlerine bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) ve [saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
