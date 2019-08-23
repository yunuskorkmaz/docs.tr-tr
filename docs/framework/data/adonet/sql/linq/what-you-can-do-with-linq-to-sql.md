---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 21ed620ab5b7a78fc4f396cc474e7c62b70f1ddd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946617"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ to SQL ile Yapabilecekleriniz
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bir SQL geliştiricisi olarak bekleeceğiniz tüm önemli özellikleri destekler. Bilgileri sorgulayabilir ve tablolardan bilgi ekleyebilir, güncelleştirebilir ve silebilirsiniz.  
  
## <a name="selecting"></a>Seçme  
 (*Projeksiyon*) seçeneği, yalnızca kendi programlama dilinizde bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgu yazarak ve ardından sonuçları almak için bu sorguyu yürüterek elde edilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], tüm gerekli işlemleri, bildiğiniz gerekli SQL işlemlerine dönüştürür. Daha fazla bilgi için bkz. [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Aşağıdaki örnekte, Londra 'daki müşterilerin şirket adları, konsol penceresinde alınır ve görüntülenir.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Takma  
 Bir SQL `Insert`yürütmek için, yalnızca oluşturduğunuz nesne modeline nesne ekleyin ve üzerinde <xref:System.Data.Linq.DataContext>öğesini çağırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .  
  
 Aşağıdaki örnekte, kullanarak `Customers` <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>tabloya yeni bir müşteri ve müşteri hakkındaki bilgiler eklenir.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Bilen  
 `Update` Bir veritabanı girişinde, önce öğeyi alın ve doğrudan nesne modelinde düzenleyin. Nesneyi değiştirdikten sonra, veritabanını güncelleştirmek <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> için üzerinde öğesini çağırın.  
  
 Aşağıdaki örnekte, Londra 'dan gelen tüm müşteriler alınır. Ardından, şehir adı "Londra" iken "Londra-Metro" olarak değiştirilir. Son olarak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> , değişiklikleri veritabanına göndermek için çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Silinmesinden  
 Bir `Delete` öğe için, öğeyi ait olduğu koleksiyondan kaldırın ve ardından değişikliği uygulamak <xref:System.Data.Linq.DataContext> için üzerinde öğesini çağırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]basamaklı silme işlemlerini tanımıyor. Kısıtlama içeren bir tablodaki bir satırı silmek istiyorsanız, bkz [. nasıl yapılır: Veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)satırları silin.  
  
 Aşağıdaki örnekte, çalıştıran müşteri `CustomerID` `98128` veritabanından alınır. Daha sonra, müşteri satırının alındığını onayladıktan sonra, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> bu nesneyi koleksiyondan kaldırmak için çağırılır. Son olarak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> , silme işlemini veritabanına iletmek için çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
