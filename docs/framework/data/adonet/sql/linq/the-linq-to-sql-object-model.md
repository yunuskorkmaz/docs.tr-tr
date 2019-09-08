---
title: LINQ to SQL Nesne Modeli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: b73904e2347c501b21b2c5933d0b43c7abafeb7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792320"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL Nesne Modeli
' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, geliştiricinin programlama dilinde ifade edilen bir nesne modeli, ilişkisel bir veritabanının veri modeliyle eşlenir. Daha sonra, veriler üzerindeki işlemler nesne modeline göre yürütülür.  
  
 Bu senaryoda veritabanına veritabanı komutları (örneğin, `INSERT`) yayınlamayın. Bunun yerine, değerleri değiştirirsiniz ve nesne modelinizdeki yöntemleri yürütün. Veritabanını sorgulamak veya değişiklikleri göndermek istediğinizde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] isteklerinizi doğru SQL komutlarına çevirir ve bu komutları veritabanına gönderir.  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nesne modelindeki en temel öğeler ve ilişkisel veri modelindeki öğelerle ilişkisi aşağıdaki tabloda özetlenmiştir:  
  
|LINQ to SQL nesne modeli|İlişkisel veri modeli|  
|------------------------------|---------------------------|  
|Varlık sınıfı|Tablo|  
|Sınıf üyesi|Sütun|  
|Kaldırma|Yabancı anahtar ilişkisi|  
|Yöntem|Saklı yordam veya Işlev|  
  
> [!NOTE]
> Aşağıdaki açıklamalarda, ilişkisel veri modeli ve kurallarıyla ilgili temel bilgilere sahip olduğunuz varsayılır.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL varlık sınıfları ve veritabanı tabloları  
 ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, bir veritabanı tablosu bir *varlık sınıfı*tarafından temsil edilir. Bir varlık sınıfı, sınıfının bir veritabanı tablosuyla ilişkilenme özel bilgilerini kullanarak açıklama ekleyerek, oluşturabileceğiniz diğer herhangi bir sınıf gibidir. Aşağıdaki örnekte olduğu gibi, sınıf bildirimidir özel bir<xref:System.Data.Linq.Mapping.TableAttribute>öznitelik () ekleyerek bu ek açıklamayı yaparsınız:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Yalnızca tablo (yani varlık sınıfları) olarak tanımlanan sınıfların örnekleri veritabanına kaydedilebilir.  
  
 Daha fazla bilgi için [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)tablo özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Sınıf üyeleri ve veritabanı sütunları LINQ to SQL  
 Sınıfları tablolarla ilişkilendirmenin yanı sıra, alanları veya özellikleri veritabanı sütunlarını temsil edecek şekilde belirlersiniz. Bu amaçla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , aşağıdaki örnekte olduğu <xref:System.Data.Linq.Mapping.ColumnAttribute> gibi özniteliğini tanımlar:  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Yalnızca sütunlara eşlenen alanlar ve Özellikler veritabanına kalıcı olarak kaydedilir veya veritabanından alınır. Sütun olarak bildirilmeyen uygulamalar, uygulama mantığınızın geçici bölümleri olarak değerlendirilir.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliği sütunları temsil eden bu üyeleri özelleştirmek için kullanabileceğiniz çeşitli özelliklere sahiptir (örneğin, bir üyeyi birincil anahtar sütununu temsil edecek şekilde belirleme). Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)sütun özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL Ilişkilendirmeleri ve veritabanı yabancı anahtar Ilişkileri  
 ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini uygulayarak veritabanı ilişkilendirmelerini (birincil anahtar için yabancı anahtar ilişkileri gibi) temsil edersiniz. Aşağıdaki kod segmentinde, `Order` sınıfı <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği olan bir `Customer` özelliği içerir. Bu özellik ve özniteliği sınıfı ile bir `Order` ilişki `Customer` sağlar.  
  
 Aşağıdaki kod örneği `Customer` `Order` sınıfından özelliğini gösterir.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)ilişkilendirme özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL yöntemleri ve veritabanı saklı yordamları  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]saklı yordamları ve Kullanıcı tanımlı işlevleri destekler. ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, bu veritabanı tanımlı soyutlamaları istemci nesnelerinde kesin olarak belirlenmiş bir şekilde erişebileceğiniz şekilde, istemci nesneleriyle eşlersiniz. Yöntem imzaları, veritabanında tanımlanan yordamlar ve işlevler için olası imzalara benzer. Bu yöntemleri saptamak için IntelliSense 'i kullanabilirsiniz.  
  
 Eşlenmiş yordama yapılan bir çağrı tarafından döndürülen bir sonuç kümesi, türü kesin belirlenmiş bir koleksiyondur.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.FunctionAttribute> ve<xref:System.Data.Linq.Mapping.ParameterAttribute> özniteliklerini kullanarak saklı yordamları ve işlevleri yöntemlere eşler. Saklı yordamları temsil eden yöntemler, <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> özelliği tarafından Kullanıcı tanımlı işlevlerden temsil eden uygulamalardan ayırt edilir. Bu Özellik (varsayılan) olarak `false` ayarlandıysa, yöntemi saklı prosedürü temsil eder. Olarak `true`ayarlanırsa, yöntemi bir veritabanı işlevini temsil eder.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, saklı yordamlara ve Kullanıcı tanımlı işlevlere eşlenmiş Yöntemler oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
### <a name="example"></a>Örnek  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md) ve [saklı yordamların](stored-procedures.md)Işlev özniteliği, saklı yordam özniteliği ve parametre özniteliği bölümlerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [Arka Plan Bilgileri](background-information.md)
