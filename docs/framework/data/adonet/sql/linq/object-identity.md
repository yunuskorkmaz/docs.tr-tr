---
title: Nesne Kimliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: dff5642b2490cd3935dba3b3d04cd62082249c32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915721"
---
# <a name="object-identity"></a>Nesne Kimliği
Çalışma zamanındaki nesnelerin benzersiz kimlikleri vardır. Aynı nesneye başvuran iki değişken gerçekten nesnenin aynı örneğine başvurur. Bu olgu nedeniyle, bir değişken aracılığıyla bir yol yoluyla yaptığınız değişiklikler, hemen başka bir şekilde görünür.  
  
 İlişkisel bir veritabanı tablosundaki satırların benzersiz kimlikleri yok. Her satır benzersiz bir birincil anahtara sahip olduğundan, iki satır aynı anahtar değerini paylaşmaz. Ancak, bu olgu yalnızca veritabanı tablosunun içeriğini kısıtlar.  
  
 Gerçekte, veriler genellikle veritabanından ve uygulamanın onunla birlikte çalıştığı farklı bir katmana getirilir. Bu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklediği modeldir. Veriler veritabanından satır olarak başlatıldığında, aynı verileri temsil eden iki satırın gerçekten aynı satır örneklerine karşılık geldiğini gösteren bir beklenmez. Belirli bir müşteriyi iki kez sorgulayıp iki satırlık veri alırsınız. Her satır aynı bilgileri içerir.  
  
 Nesneler sayesinde çok farklı bir şey beklemeniz gerekir. Aynı bilgileri sürekli olarak sormanız <xref:System.Data.Linq.DataContext> durumunda, size aynı nesne örneğini sunacaktır. Bu davranışı, nesnelerin uygulamanız için özel anlamı olduğundan ve nesneler gibi davranmalarını beklemeniz için beklemeniz gerekir. Bunları hiyerarşi veya grafik olarak tasarlamış olursunuz. Aynı şeyi birden çok kez isteyip istemediğiniz için, bunları, çoğaltılan örnek sayısını almak zorunda değilsiniz.  
  
 ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] De<xref:System.Data.Linq.DataContext> , nesne kimliğini yönetir. Veritabanından yeni bir satır aldığınızda, satır bir kimlik tablosuna birincil anahtar tarafından kaydedilir ve yeni bir nesne oluşturulur. Aynı satırı her aldığınızda, özgün nesne örneği uygulamaya geri gönderilir. Bu şekilde, <xref:System.Data.Linq.DataContext> kimlik kavramını veritabanı (yani, birincil anahtarlar) tarafından görülen kimlik kavramına (yani, örnekler) çevirir. Uygulama yalnızca ilk alındığı durumda nesneyi görür. Yeni veriler, farklıysa, atılır. Daha fazla bilgi için bkz. [kimlik önbelleğinden nesneleri alma](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], iyimser güncelleştirmeleri desteklemek için yerel nesnelerin bütünlüğünü yönetmek üzere bu yaklaşımı kullanır. Nesne ilk oluşturulduktan sonra gerçekleşen tek değişiklikler uygulama tarafından yapılan değişikliklerdir, uygulamanın amacı net olur. Bir dış tarafa ait değişiklikler ara içinde gerçekleştiyse, bu, zaman `SubmitChanges()` olarak tanımlanır.  
  
> [!NOTE]
> Sorgu tarafından istenen nesne zaten alınmış bir biçimde kolayca tanındıysa, hiçbir sorgu yürütülmez. Kimlik tablosu, daha önce alınan tüm nesneler için bir önbellek işlevi görür.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="object-caching-example-1"></a>Nesne önbelleği örneği 1  
 Bu örnekte, aynı sorguyu iki kez çalıştırırsanız, bellekte her seferinde aynı nesneye bir başvuru alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Nesne önbelleği örneği 2  
 Bu örnekte, veritabanından aynı satırı döndüren farklı sorgular çalıştırırsanız, bellekte her seferinde aynı nesneye bir başvuru alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
