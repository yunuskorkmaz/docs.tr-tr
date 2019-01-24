---
title: 'Nasıl yapılır: Veritabanı ilişkileri eşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 907ed58e9828921585135f2319d0db9559b606d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556395"
---
# <a name="how-to-map-database-relationships"></a>Nasıl yapılır: Veritabanı ilişkileri eşleme
Her zaman aynı olacak herhangi bir veri ilişkileri varlık sınıfınızda özelliğine başvuruyor şifreleyebilirsiniz. Northwind örnek veritabanındaki gibi müşteriler genellikle, sipariş olduğundan her zaman bir ilişki yoktur modelinde müşterilerin ve siparişlerinin arasında.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tanımlayan bir <xref:System.Data.Linq.Mapping.AssociationAttribute> tür ilişkilerini temsil eden yardımcı olması için öznitelik. Bu öznitelik ile birlikte kullanılan <xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601> türleri temsil eden bir veritabanındaki yabancı anahtar ilişkisi olması. Daha fazla bilgi için ilişkilendirme özniteliği bölümüne bakın. [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük/küçük harfe duyarlıdır. Örneğin, öznitelik AssociationAttribute.Storage özelliği için kullanılan değerleri başka bir yerde kod içinde kullanılan karşılık gelen özellik adları durum eşleştiğinden emin olun. Bu, tüm .NET programlama dillerinde, olanlar genellikle büyük Visual Basic dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir. Depolama özelliği hakkında daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Çoğu ilişki tek-çok, bu konunun ilerleyen bölümlerinde örnekte olduğu gibi ' dir. Bire bir veya çoktan çoğa ilişkilerini şu şekilde gösterebilir.  
  
-   Bire bir: Bu tür bir ilişkiyi temsil eden dahil ederek <xref:System.Data.Linq.EntitySet%601> her iki tarafında.  
  
     Örneğin, bir `Customer` - `SecurityCode` ilişki, Müşteri'nin güvenlik kodu içinde bulunmaz oluşturulan `Customer` tablo ve yalnızca yetkili kişiler tarafından erişilebilecek.  
  
-   Çoktan çoğa: Çoktan çoğa ilişkilerin, bağlantı tablonun birincil anahtarı (olarak da adlandırılan *birleşim* tablo) bir bileşik diğer iki tablodan yabancı anahtarları tarafından oluşturulmuş.  
  
     Örneğin, bir `Employee` - `Project` oluşturulmuş çoktan çoğa ilişki bağlantı tablosunu kullanarak `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tür bir ilişkiye üç sınıflarını kullanarak modellenebilir gerektirir: `Employee`, `Project`, ve `EmployeeProject`. Bu durumda, arasındaki ilişkiyi değiştirme bir `Employee` ve `Project` birincil anahtarın bir güncelleştirme gerektiren görünebilir `EmployeeProject`. Ancak, varolan silinmesi iyi bu durum modellenmiştir `EmployeeProject` ve yeni bir oluşturma `EmployeeProject`.  
  
    > [!NOTE]
    >  İlişkisel veritabanları ilişkiler genellikle diğer tablolardaki birincil anahtarları başvuran yabancı anahtar değerler olarak modellenir. Bunlar arasında gezinmek için açıkça iki tablo bir ilişkisel kullanılarak ilişkilendirmek *birleştirme* işlemi.  
    >   
    >  Nesneler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], diğer el, birbirlerine başvuran bir özelliğe veya koleksiyonlar kullanarak Git başvuru kullanarak başvuru *nokta* gösterimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir-çok, `Customer` sınıfı, müşterilerin ve siparişlerinin arasındaki ilişkiyi bildiren bir özelliğe sahiptir.  `Orders` Özelliği türüdür <xref:System.Data.Linq.EntitySet%601>. Bu tür, bu ilişki tek-çok olduğunu belirten (bir müşteri için çok sayıda sipariş). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Özelliği nasıl Bu ilişkilendirme, yani bu biriyle Karşılaştırılacak ilgili sınıfında özelliğin adını belirterek gerçekleştirilir tanımlamak için kullanılır. Bu örnekte, `CustomerID` özelliği karşılaştırılır, yalnızca bir veritabanı *birleştirme* bu sütun değeri ile karşılaştırmak.  
  
> [!NOTE]
>  Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] sınıfları arasında bir ilişki oluşturmak için.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Ayrıca, durum tersine çevirebilirsiniz. Yerine `Customer` müşteriler ve siparişler arasındaki ilişkiyi tanımlamak için sınıf, kullanabileceğiniz `Order` sınıfı. `Order` Sınıfının kullandığı <xref:System.Data.Linq.EntityRef%601> ilişkisi aşağıdaki kod örneğinde olduğu gibi müşteri açıklayan tür.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Sınıfı destekler *Ertelenen yükleme*. Daha fazla bilgi için *bkz* [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
