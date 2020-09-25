---
title: 'Nasıl yapılır: Veritabanı İlişkilerini Eşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166462"
---
# <a name="how-to-map-database-relationships"></a>Nasıl yapılır: Veritabanı İlişkilerini Eşleme

Varlık sınıfınızda, her zaman aynı olacak herhangi bir veri ilişkisi olarak özellik başvuruları olarak kodlayabilirsiniz. Northwind örnek veritabanında, örneğin müşteriler genellikle sipariş yerleştirtiğinden, modelde müşteriler ve siparişleri arasında her zaman bir ilişki vardır.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.AssociationAttribute>Bu tür ilişkileri temsil etmenize yardımcı olmak için bir özniteliği tanımlar. Bu öznitelik, <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntityRef%601> bir veritabanında yabancı anahtar ilişkisi olduğunu göstermek için ve türleri ile birlikte kullanılır. Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)ilişkilendirme özniteliği bölümüne bakın.  
  
> [!NOTE]
> AssociationAttribute ve ColumnAttribute Storage Özellik değerleri büyük/küçük harfe duyarlıdır. Örneğin, AssociationAttribute. Storage özelliğinin özniteliğinde kullanılan değerlerin, kodun başka bir yerinde kullanılan ilgili özellik adları için büyük/küçük harf ile eşleştiğinden emin olun. Bu, genellikle büyük/küçük harf duyarlı olmayan, hatta Visual Basic dahil olmak üzere tüm .NET programlama dilleri için geçerlidir. Depolama özelliği hakkında daha fazla bilgi için bkz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType> ..  
  
 Çoğu ilişki, bu konunun ilerleyen kısımlarında olduğu gibi bire çok aynıdır. Ayrıca, bire bir ve çoktan çoğa ilişkilerini aşağıdaki şekilde de kullanabilirsiniz:  
  
- Bire bir: her iki tarafa de ekleyerek bu tür ilişkiyi temsil eder <xref:System.Data.Linq.EntitySet%601> .  
  
     Örneğin, `Customer` - `SecurityCode` müşterinin güvenlik kodu tabloda bulunamamayacak `Customer` ve yalnızca yetkili kişiler tarafından erişilebilecek şekilde oluşturulan bir ilişki düşünün.  
  
- Çoka çok: çoktan çoğa ilişkilerde, bağlantı tablosunun birincil anahtarı ( *birleşim* tablosu olarak da adlandırılır) genellikle diğer iki tablodaki yabancı anahtarların bir bileşimi tarafından oluşturulur.  
  
     Örneğin, `Employee` - `Project` bağlantı tablosu kullanılarak oluşturulmuş bir çoktan çoğa ilişki düşünün `EmployeeProject` . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu tür bir ilişkinin üç sınıf kullanılarak modellenmesi gerekir: `Employee` , `Project` ve `EmployeeProject` . Bu durumda, ve arasındaki ilişkiyi değiştirmek, `Employee` `Project` birincil anahtarın güncelleştirilmesini gerektirecek şekilde görünür `EmployeeProject` . Ancak, bu durum, mevcut bir `EmployeeProject` ve yeni oluşturma için en iyi modellenir `EmployeeProject` .  
  
    > [!NOTE]
    > İlişkisel veritabanlarındaki ilişkiler genellikle diğer tablolardaki birincil anahtarlara başvuran yabancı anahtar değerleri olarak modellenir. Bunlar arasında gezinmek için, ilişkisel bir *JOIN* işlemi kullanarak iki tabloyu açıkça ilişkilendirirsiniz.  
    >
    >  İçindeki nesneler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , diğer yandan, özellik başvurularını veya *nokta* gösterimini kullanarak gittiğiniz başvuruların koleksiyonlarını kullanarak birbirlerine başvurur.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki bire çok örnekte, `Customer` sınıfının müşteriler ve siparişleri arasındaki ilişkiyi bildiren bir özelliği vardır.  `Orders`Özelliği türündedir <xref:System.Data.Linq.EntitySet%601> . Bu tür, bu ilişkinin bire çok (bir müşterinin birden çok siparişe) olduğunu belirtir. Özelliği, bu <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> ilişkinin nasıl yapıldığını, yani ilgili sınıfta bununla Karşılaştırılacak özelliği belirterek belirtmek için kullanılır. Bu örnekte, `CustomerID` bir veritabanı *birleştirmesi* bu sütun değerini karşılaştıracağından, özelliği karşılaştırılır.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, sınıflar arasında bir ilişki oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Örnek  

 Ayrıca, durumu tersine çevirebilirsiniz. `Customer`Sınıfı, müşteriler ve siparişler arasındaki ilişkiyi betimleyen şekilde kullanmak yerine `Order` sınıfını kullanabilirsiniz. `Order`Sınıfı, <xref:System.Data.Linq.EntityRef%601> Aşağıdaki kod örneğinde olduğu gibi, ilişkiyi müşteriye geri açıklama için kullanır.  
  
> [!NOTE]
> <xref:System.Data.Linq.EntityRef%601>Sınıfı *ertelenmiş yüklemeyi*destekler. Daha fazla bilgi için *bkz* . [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
