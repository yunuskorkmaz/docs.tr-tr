---
title: 'Nasıl yapılır: Veritabanı İlişkilerini Eşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148380"
---
# <a name="how-to-map-database-relationships"></a>Nasıl yapılır: Veritabanı İlişkilerini Eşleme
Varlık sınıfınızda her zaman aynı olacak tüm veri ilişkilerini özellik başvuruları olarak kodlayabilirsiniz. Örneğin Northwind örnek veritabanında, müşteriler genellikle sipariş verdiğinden, modelde müşterilerle siparişleri arasında her zaman bir ilişki vardır.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bu tür <xref:System.Data.Linq.Mapping.AssociationAttribute> ilişkileri temsil yardımcı olmak için bir öznitelik tanımlar. Bu öznitelik, veritabanında <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntityRef%601> yabancı anahtar ilişkisi ne olacağını temsil etmek için ve türleri ile birlikte kullanılır. Daha fazla bilgi için, [Öznitelik Tabanlı Eşleme'nin](attribute-based-mapping.md)İlişki Özniteliği bölümüne bakın.  
  
> [!NOTE]
> İlişkilendirmeAttribute ve ColumnAttribute Depolama özellik değerleri büyük/küçük harf duyarlıdır. Örneğin, AssociationAttribute.Storage özelliği için öznitelikkullanılan değerlerin kodun başka bir yerinde kullanılan ilgili özellik adları için durum la eşleştirdiğinden emin olun. Bu, Visual Basic de dahil olmak üzere genellikle büyük/küçük harf duyarlı olmayan tüm .NET programlama dilleri için de geçerlidir. Depolama özelliği hakkında daha fazla <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>bilgi için bkz.  
  
 Çoğu ilişki, bu konunun sonraki örneğinde olduğu gibi bire bir dir. Ayrıca bire bir ve çok-çok ilişkileri aşağıdaki gibi temsil edebilirsiniz:  
  
- Bire bir: Her iki tarafı da <xref:System.Data.Linq.EntitySet%601> dahil ederek bu tür bir ilişkiyi temsil eder.  
  
     Örneğin, müşterinin `Customer` - `SecurityCode` güvenlik kodunun `Customer` tabloda bulunmaması ve yalnızca yetkili kişiler tarafından erişilebilmeleri için oluşturulmuş bir ilişkiyi düşünün.  
  
- Çok-çok: Çok-çok ilişkilerde, bağlantı tablosunun birincil anahtarı *(bağlantı* tablosu olarak da adlandırılır) genellikle diğer iki tablodaki yabancı anahtarların bir bileşiminden oluşur.  
  
     Örneğin, bağlantı `Employee` - `Project` tablosunu `EmployeeProject`kullanarak oluşan çok-çok ilişkisi düşünün. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]böyle bir ilişkinin üç sınıf kullanılarak `Employee`modellenmelerini gerektirir: , , `Project`ve `EmployeeProject`. Bu durumda, bir ve `Employee` a `Project` arasındaki ilişkiyi değiştirme birincil anahtarın `EmployeeProject`bir güncelleştirme gerektiren görünebilir. Ancak, bu durum en iyi varolan `EmployeeProject` bir silme ve `EmployeeProject`yeni bir oluşturma olarak modellenmiştir.  
  
    > [!NOTE]
    > İlişkisel veritabanlarındaki ilişkiler genellikle diğer tablolardaki birincil anahtarlara başvuran yabancı anahtar değerleri olarak modellenir. Aralarında gezinmek için, *ilişkisel* birleştirme işlemi kullanarak iki tabloyu açıkça ilişkilendirin.  
    >
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Diğer taraftan, nesneler, *nokta* gösterimi kullanarak yön ettiğiniz özellik başvurularını veya başvuru koleksiyonlarını kullanarak birbirlerine başvururlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki bire bir örnekte, `Customer` sınıfın müşteriler ve siparişleri arasındaki ilişkiyi bildiren bir özelliği vardır.  Özellik `Orders` türündedir. <xref:System.Data.Linq.EntitySet%601> Bu tür, bu ilişkinin bir-çok (birçok siparişiçin bir müşteri) olduğunu belirtir. Özellik, <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> bu ilişkilendirme nasıl gerçekleştirileceğini açıklamak için kullanılır, yani, bu ile karşılaştırıldığında ilgili sınıfta özelliğin adını belirterek. Bu örnekte, `CustomerID` bir veritabanı *birleştirme* bu sütun değerini karşılaştıracağı gibi özellik karşılaştırılır.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, sınıflar arasında bir ilişki oluşturmak için Nesne İlişkisel Tasarımcısı'nı kullanabilirsiniz.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Durumu tersine de çevirebilirsiniz. Müşteriler ve `Customer` siparişler arasındaki ilişkilendirme tanımlamak için sınıfı kullanmak `Order` yerine, sınıfı kullanabilirsiniz. Sınıf, `Order` aşağıdaki <xref:System.Data.Linq.EntityRef%601> kod örneğinde olduğu gibi, müşteriyle olan ilişkiyi açıklamak için türü kullanır.  
  
> [!NOTE]
> Sınıf <xref:System.Data.Linq.EntityRef%601> *ertelenmiş yüklemeyi*destekler. Daha fazla bilgi için [Ertelenmiş ve Hemen Yükleme](deferred-versus-immediate-loading.md) *bölümüne bakın.*  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
