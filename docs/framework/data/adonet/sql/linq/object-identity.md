---
title: Nesne Kimliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 0f1b6cf27101c2a7f55757b72b56b2291198404d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767552"
---
# <a name="object-identity"></a>Nesne Kimliği
Çalışma zamanı nesneleri benzersiz kimlikler var. Aynı nesneye başvuran iki değişken aslında aynı nesne örneğine bakın. Bu olgu nedeniyle bir değişken bir yol ile yaptığınız değişiklikler diğer hemen görünür.  
  
 İlişkisel veritabanı tablosundaki satırlara benzersiz kimlikleri yok. Her satırda benzersiz bir birincil anahtar olduğundan, hiçbir iki satır aynı anahtar değeri paylaşın. Ancak, bu durum yalnızca veritabanı tablosunun içeriği kısıtlar.  
  
 Gerçekte uygulamanın nerede ile çalışır, farklı bir katmanı ve veritabanı dışına veri çoğunlukla getirilir. Bu model, bu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler. Verileri veritabanından satırlar olarak yapıldığında, aynı verileri temsil eden iki satır aynı satır örnekleri gerçekten karşılık gelen hiçbir beklentisi içindedirler. Belirli bir müşteri için iki kez sorgu, iki satır veri alın. Her satır aynı bilgileri içerir.  
  
 Nesneleriyle çok farklı bir şey bekler. Siz istenirse, beklediğiniz <xref:System.Data.Linq.DataContext> aynı bilgilerin tekrar tekrar, aslında size aynı nesne örneği sunar. Bu davranış, çünkü nesneleri uygulamanız için özel bir anlamı yoktur ve nesneleri gibi davranırlar beklediğiniz bekler. Bunları hiyerarşileri veya grafikleri tasarlanmıştır. Bu nedenle almak için ve yalnızca birden fazla kez aynı şeyi sorulan nedeniyle çoğaltılmış örneklerinin verilere almamayı beklediğiniz.  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> nesne kimliğini yönetir. Yeni bir satır veritabanından her satırın birincil anahtara göre bir kimlik tablosuna kaydedilir ve yeni bir nesne oluşturulur. Aynı satır almak zaman, özgün nesne örneğini geri uygulamaya devredildiği. Bu şekilde <xref:System.Data.Linq.DataContext> kimlik kavramını (diğer bir deyişle, birincil anahtarlar) veritabanı tarafından görülen dil (örnekler) tarafından görülen kimlik kavramını dönüştürecektir. Uygulama, yalnızca ilk alındıktan durumda nesne görür. Yeni veri farklı olması durumunda, göz ardı edilir. Daha fazla bilgi için [kimlik önbelleğinden nesne alma](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İyimser güncelleştirmeleri desteklemek için yerel nesneleri bütünlüğünü yönetmek için bu yaklaşımı kullanır. Uygulama tarafından yapılan ilk başta nesne oluşturulduktan sonra gerçekleşen yalnızca değişiklikler olduğu için uygulama amacı işaretlenmemiştir. Bu arada değişiklikleri dışında bir taraf tarafından oluştuysa zamanında tanımlanır `SubmitChanges()` çağrılır.  
  
> [!NOTE]
>  Sorgu tarafından istenen nesne zaten alınan bir kolayca tanımlanabilen ise, hiçbir sorgu yürütülür. Bir önbellek tüm nesneler daha önce listelene kimlik tablo işlevi görür.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="object-caching-example-1"></a>Önbelleğe alma örnek 1 nesne  
 İki kez, aynı sorgu yürütün, bu örnekte, bellekte aynı nesneye bir başvuru her seferinde alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Önbelleğe alma örnek 2 nesnesi  
 Aynı satırda veritabanından döndüren farklı sorgular yürütün, bu örnekte, bellekte aynı nesneye bir başvuru her seferinde alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
