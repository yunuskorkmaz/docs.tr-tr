---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: a2e65cb558eec3cec21ea0efbcc66bb8c56ec7b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163927"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ to SQL ile Yapabilecekleriniz

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir SQL geliştiricisi olarak bekleeceğiniz tüm önemli özellikleri destekler. Bilgileri sorgulayabilir ve tablolardan bilgi ekleyebilir, güncelleştirebilir ve silebilirsiniz.  
  
## <a name="selecting"></a>Seçiminde  

 (*Projeksiyon*) seçeneği, yalnızca kendi programlama DILINIZDE bir LINQ sorgusu yazarak ve ardından sonuçları almak için bu sorguyu yürüterek elde edilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , tüm gerekli işlemleri, bildiğiniz gerekli SQL işlemlerine dönüştürür. Daha fazla bilgi için bkz. [LINQ to SQL](index.md).  
  
 Aşağıdaki örnekte, Londra 'daki müşterilerin şirket adları, konsol penceresinde alınır ve görüntülenir.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Takma  

 Bir SQL yürütmek için `Insert` , yalnızca oluşturduğunuz nesne modeline nesne ekleyin ve üzerinde öğesini çağırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> .  
  
 Aşağıdaki örnekte, kullanarak tabloya yeni bir müşteri ve müşteri hakkındaki bilgiler eklenir `Customers` <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> .  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Bilen  

 `Update`Bir veritabanı girişinde, önce öğeyi alın ve doğrudan nesne modelinde düzenleyin. Nesneyi değiştirdikten sonra, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanını güncelleştirmek için üzerinde öğesini çağırın <xref:System.Data.Linq.DataContext> .  
  
 Aşağıdaki örnekte, Londra 'dan gelen tüm müşteriler alınır. Ardından, şehir adı "Londra" iken "Londra-Metro" olarak değiştirilir. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> değişiklikleri veritabanına göndermek için çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Siliniyor  

 `Delete`Bir öğe için, öğeyi ait olduğu koleksiyondan kaldırın ve ardından <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> değişikliği uygulamak için üzerinde öğesini çağırın.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] basamaklı silme işlemlerini tanımıyor. Kısıtlama içeren bir tablodaki bir satırı silmek isterseniz, bkz. [nasıl yapılır: satırları veritabanından silme](how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki örnekte, çalıştıran müşteri `CustomerID` `98128` veritabanından alınır. Daha sonra, müşteri satırının alındığını onayladıktan sonra, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> Bu nesneyi koleksiyondan kaldırmak için çağırılır. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> silme işlemini veritabanına iletmek için çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Başlarken](getting-started.md)
