---
title: "Nesne Kimliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cb4e25c2c2a1832b662a23caa7d5f3d7090228ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="object-identity"></a>Nesne Kimliği
Çalışma zamanında nesneleri benzersiz kimlikler sahiptir. Aynı nesneye başvurmak iki değişken aslında aynı nesne örneğine bakın. Bu olgu nedeniyle bir değişken yolundan yapmamanız yaptığınız değişiklikler diğer hemen görünür değildir.  
  
 İlişkisel veritabanı tablosundaki satırları benzersiz kimlikler gerekmez. Her satırda benzersiz bir birincil anahtara sahip olduğundan, hiçbir iki satır aynı anahtar değeri paylaşır. Ancak, bu olgu yalnızca veritabanı tablosunun içeriğini kısıtlar.  
  
 Gerçekte, veri çoğunlukla veritabanı dışında ve bir uygulama ile çalıştığı farklı bir katmana halinde duruma getirilir. Bu modelin olup, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler. Verileri veritabanından satırlar olarak duruma getirildiğinde aynı verilerini temsil eden iki satır aynı satır örneklerine gerçekte karşılık gelen hiçbir Beklenti sahip. Belirli bir müşteri için iki kez sorgu, iki veri satırını alır. Her satır aynı bilgileri içerir.  
  
 Nesnelerle çok farklı bir şey bekler. Sorun varsa, beklediğiniz <xref:System.Data.Linq.DataContext> aynı bilgilerin tekrar tekrar, aslında size aynı nesne örneğini sağlar. Bu davranış, çünkü nesneleri, uygulamanız için özel bir anlamı olan ve nesneleri gibi davranırlar beklediğiniz bekler. Bunları hiyerarşileri veya grafikleri tasarlanmıştır. Bu nedenle almaya ve yalnızca aynı şeyi birden fazla kez sorulan çünkü gerek çoğaltılmış örneklerinin almamayı beklediğiniz.  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> nesne kimliğini yönetir. Veritabanından yeni bir satır her satırın birincil anahtarı tarafından bir kimlik tablosunda kaydedilir ve yeni bir nesne oluşturulur. Aynı satır almak olduğunda, orijinal nesne örneğini geri uygulamaya karmalayan. Bu şekilde <xref:System.Data.Linq.DataContext> kimlik kavramını (diğer bir deyişle, birincil anahtarlar) veritabanı tarafından görülen (örnekler) dil tarafından görülen kimlik kavramını çevirir. Uygulama, yalnızca ilk alınmış durumdaki nesne görür. Yeni veriler farklı olması durumunda, göz ardı edilir. Daha fazla bilgi için bkz: [kimlik önbelleğe alma nesnelerden](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]İyimser güncelleştirmeleri desteklemek için yerel nesneleri bütünlüğünü yönetmek için bu yaklaşımı kullanır. İlk bakışta nesne oluşturulduktan sonra oluşan yalnızca değişiklikler uygulama tarafından yapılan olduğundan, uygulama amacı işaretlenmemiştir. Bir dış taraf değişikliklerden arada oluşmuş olursa zamanında tanımlanır `SubmitChanges()` olarak adlandırılır.  
  
> [!NOTE]
>  Sorgu tarafından istenen nesne zaten alınan biri kolayca tanımlanabilen ise, hiçbir sorgu yürütülür. Bir önbellek tüm nesneleri daha önce listelene gibi kimlik tablo yapar.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="object-caching-example-1"></a>Önbelleğe alma örnek 1 nesne  
 İki kez aynı sorgu yürütme, bu örnekte, bellekte aynı nesneye bir başvurusu her zaman alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Önbelleğe alma örnek 2 nesnesi  
 Aynı satır veritabanından döndüren farklı sorgular yürütün, bu örnekte, bellekte aynı nesneye bir başvurusu her zaman alırsınız.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
