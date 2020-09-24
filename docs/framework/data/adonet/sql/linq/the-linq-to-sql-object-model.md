---
title: LINQ to SQL Nesne Modeli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: b17e1b6f4a6f849e3b42d69e9b9c2d5f906218e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155516"
---
# <a name="the-linq-to-sql-object-model"></a>LINQ to SQL Nesne Modeli

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, geliştiricinin programlama dilinde ifade edilen bir nesne modeli, ilişkisel bir veritabanının veri modeliyle eşlenir. Daha sonra, veriler üzerindeki işlemler nesne modeline göre yürütülür.  
  
 Bu senaryoda veritabanına veritabanı komutları (örneğin,) yayınlamayın `INSERT` . Bunun yerine, değerleri değiştirirsiniz ve nesne modelinizdeki yöntemleri yürütün. Veritabanını sorgulamak veya değişiklikleri göndermek istediğinizde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] isteklerinizi doğru SQL komutlarına çevirir ve bu komutları veritabanına gönderir.  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Nesne modelindeki en temel öğeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve ilişkisel veri modelindeki öğelerle ilişkisi aşağıdaki tabloda özetlenmiştir:  
  
|LINQ to SQL nesne modeli|İlişkisel veri modeli|  
|------------------------------|---------------------------|  
|Varlık sınıfı|Tablo|  
|Sınıf üyesi|Sütun|  
|Kaldırma|Yabancı anahtar ilişkisi|  
|Yöntem|Saklı yordam veya Işlev|  
  
> [!NOTE]
> Aşağıdaki açıklamalarda, ilişkisel veri modeli ve kurallarıyla ilgili temel bilgilere sahip olduğunuz varsayılır.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL varlık sınıfları ve veritabanı tabloları  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, bir veritabanı tablosu bir *varlık sınıfı*tarafından temsil edilir. Bir varlık sınıfı, sınıfının bir veritabanı tablosuyla ilişkilenme özel bilgilerini kullanarak açıklama ekleyerek, oluşturabileceğiniz diğer herhangi bir sınıf gibidir. <xref:System.Data.Linq.Mapping.TableAttribute>Aşağıdaki örnekte olduğu gibi, sınıf bildirimidir özel bir öznitelik () ekleyerek bu ek açıklamayı yaparsınız:  
  
### <a name="example"></a>Örnek  

 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Yalnızca tablo (yani varlık sınıfları) olarak tanımlanan sınıfların örnekleri veritabanına kaydedilebilir.  
  
 Daha fazla bilgi için [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)tablo özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Sınıf üyeleri ve veritabanı sütunları LINQ to SQL  

 Sınıfları tablolarla ilişkilendirmenin yanı sıra, alanları veya özellikleri veritabanı sütunlarını temsil edecek şekilde belirlersiniz. Bu amaçla, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> Aşağıdaki örnekte olduğu gibi özniteliğini tanımlar:  
  
### <a name="example"></a>Örnek  

 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Yalnızca sütunlara eşlenen alanlar ve Özellikler veritabanına kalıcı olarak kaydedilir veya veritabanından alınır. Sütun olarak bildirilmeyen uygulamalar, uygulama mantığınızın geçici bölümleri olarak değerlendirilir.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği sütunları temsil eden bu üyeleri özelleştirmek için kullanabileceğiniz çeşitli özelliklere sahiptir (örneğin, bir üyeyi birincil anahtar sütununu temsil edecek şekilde belirleme). Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)sütun özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL Ilişkilendirmeleri ve veritabanı yabancı anahtar Ilişkileri  

 ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , özniteliğini uygulayarak veritabanı ilişkilendirmelerini (birincil anahtar için yabancı anahtar ilişkileri gibi) temsil edersiniz <xref:System.Data.Linq.Mapping.AssociationAttribute> . Aşağıdaki kod segmentinde, `Order` sınıfı özniteliği olan bir özelliği içerir `Customer` <xref:System.Data.Linq.Mapping.AssociationAttribute> . Bu özellik ve özniteliği sınıfı `Order` ile bir ilişki sağlar `Customer` .  
  
 Aşağıdaki kod örneği `Customer` sınıfından özelliğini gösterir `Order` .  
  
### <a name="example"></a>Örnek  

 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)ilişkilendirme özniteliği bölümüne bakın.  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>LINQ to SQL yöntemleri ve veritabanı saklı yordamları  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] saklı yordamları ve Kullanıcı tanımlı işlevleri destekler. ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bu veritabanı tanımlı soyutlamaları istemci nesnelerinde kesin olarak belirlenmiş bir şekilde erişebileceğiniz şekilde, istemci nesneleriyle eşlersiniz. Yöntem imzaları, veritabanında tanımlanan yordamlar ve işlevler için olası imzalara benzer. Bu yöntemleri saptamak için IntelliSense 'i kullanabilirsiniz.  
  
 Eşlenmiş yordama yapılan bir çağrı tarafından döndürülen bir sonuç kümesi, türü kesin belirlenmiş bir koleksiyondur.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve özniteliklerini kullanarak saklı yordamları ve işlevleri yöntemlere eşler <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> . Saklı yordamları temsil eden yöntemler, özelliği tarafından Kullanıcı tanımlı işlevlerden temsil eden uygulamalardan ayırt edilir <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> . Bu özellik `false` (varsayılan) olarak ayarlandıysa, yöntemi saklı prosedürü temsil eder. Olarak ayarlanırsa `true` , yöntemi bir veritabanı işlevini temsil eder.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, saklı yordamlara ve Kullanıcı tanımlı işlevlere eşlenmiş Yöntemler oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
### <a name="example"></a>Örnek  

 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md) ve [saklı yordamların](stored-procedures.md)Işlev özniteliği, saklı yordam özniteliği ve parametre özniteliği bölümlerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [Arka Plan Bilgileri](background-information.md)
