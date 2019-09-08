---
title: 'Nasıl yapılır: Veritabanı İlişkilerini Eşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: b6b1eba063c9ec72ae14c12028dd0950b2ad95f5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793526"
---
# <a name="how-to-map-database-relationships"></a>Nasıl yapılır: Veritabanı İlişkilerini Eşleme
Varlık sınıfınızda, her zaman aynı olacak herhangi bir veri ilişkisi olarak özellik başvuruları olarak kodlayabilirsiniz. Northwind örnek veritabanında, örneğin müşteriler genellikle sipariş yerleştirtiğinden, modelde müşteriler ve siparişleri arasında her zaman bir ilişki vardır.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu tür <xref:System.Data.Linq.Mapping.AssociationAttribute> ilişkileri temsil etmenize yardımcı olmak için bir özniteliği tanımlar. Bu öznitelik, <xref:System.Data.Linq.EntitySet%601> bir veritabanında yabancı anahtar ilişkisi <xref:System.Data.Linq.EntityRef%601> olduğunu göstermek için ve türleri ile birlikte kullanılır. Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)ilişkilendirme özniteliği bölümüne bakın.  
  
> [!NOTE]
> AssociationAttribute ve ColumnAttribute Storage Özellik değerleri büyük/küçük harfe duyarlıdır. Örneğin, AssociationAttribute. Storage özelliğinin özniteliğinde kullanılan değerlerin, kodun başka bir yerinde kullanılan ilgili özellik adları için büyük/küçük harf ile eşleştiğinden emin olun. Bu, genellikle büyük/küçük harf duyarlı olmayan, hatta Visual Basic dahil olmak üzere tüm .NET programlama dilleri için geçerlidir. Depolama özelliği hakkında daha fazla bilgi için bkz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Çoğu ilişki, bu konunun ilerleyen kısımlarında olduğu gibi bire çok aynıdır. Ayrıca, bire bir ve çoktan çoğa ilişkilerini aşağıdaki şekilde de kullanabilirsiniz:  
  
- Bire bir: Her iki tarafa de <xref:System.Data.Linq.EntitySet%601> ekleyerek bu tür ilişkiyi temsil edin.  
  
     Örneğin `Customer` , müşterinin - `SecurityCode` güvenlikkodutablodabulunamamayacakveyalnızcayetkilikişilertarafındanerişilebilecekşekildeoluşturulan`Customer` bir ilişki düşünün.  
  
- Çoka çok: Çoktan çoğa ilişkilerde, bağlantı tablosunun birincil anahtarı ( *birleşim* tablosu olarak da adlandırılır) genellikle diğer iki tablodaki yabancı anahtarların bir bileşimi tarafından oluşturulur.  
  
     Örneğin, `Employee` bağlantı tablosu `Project` - kullanılarakoluşturulmuşbirçoktançoğailişkidüşünün`EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu tür bir ilişkinin üç sınıf kullanılarak modellenmesi gerekir: `Employee`, `Project`ve `EmployeeProject`. Bu durumda, `Employee` `Project` ve arasındaki ilişkiyi değiştirmek, birincil anahtarın `EmployeeProject`güncelleştirilmesini gerektirecek şekilde görünür. Ancak, bu durum, mevcut `EmployeeProject` bir ve yeni `EmployeeProject`oluşturma için en iyi modellenir.  
  
    > [!NOTE]
    > İlişkisel veritabanlarındaki ilişkiler genellikle diğer tablolardaki birincil anahtarlara başvuran yabancı anahtar değerleri olarak modellenir. Bunlar arasında gezinmek için, ilişkisel bir *JOIN* işlemi kullanarak iki tabloyu açıkça ilişkilendirirsiniz.  
    >   
    >  İçindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nesneler, diğer yandan, özellik başvurularını veya *nokta* gösterimini kullanarak gittiğiniz başvuruların koleksiyonlarını kullanarak birbirlerine başvurur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki bire çok örnekte, `Customer` sınıfının müşteriler ve siparişleri arasındaki ilişkiyi bildiren bir özelliği vardır.  `Orders` Özelliği türündedir<xref:System.Data.Linq.EntitySet%601>. Bu tür, bu ilişkinin bire çok (bir müşterinin birden çok siparişe) olduğunu belirtir. <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Özelliği, bu ilişkinin nasıl yapıldığını, yani ilgili sınıfta bununla Karşılaştırılacak özelliği belirterek belirtmek için kullanılır. Bu örnekte, `CustomerID` bir veritabanı *birleştirmesi* bu sütun değerini karşılaştıracağından, özelliği karşılaştırılır.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, sınıflar arasında bir ilişki oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Ayrıca, durumu tersine çevirebilirsiniz. Sınıfı, müşteriler ve siparişler arasındaki ilişkiyi betimleyen şekilde `Order` kullanmak yerine sınıfını kullanabilirsiniz. `Customer` Sınıfı, aşağıdaki kod <xref:System.Data.Linq.EntityRef%601> örneğinde olduğu gibi, ilişkiyi müşteriye geri açıklama için kullanır. `Order`  
  
> [!NOTE]
> Sınıfı ertelenmiş yüklemeyi destekler. <xref:System.Data.Linq.EntityRef%601> Daha fazla bilgi için *bkz* . [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
