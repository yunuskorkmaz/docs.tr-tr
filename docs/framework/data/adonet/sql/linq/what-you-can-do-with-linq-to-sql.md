---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: e84047843aff4044c75ba1b971a9e2f061e2e8d6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634007"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ to SQL ile Yapabilecekleriniz
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL geliştiricisi olarak bekleeceğiniz tüm önemli özellikleri destekler. Bilgileri sorgulayabilir ve tablolardan bilgi ekleyebilir, güncelleştirebilir ve silebilirsiniz.  
  
## <a name="selecting"></a>Seçme  
 (*Projeksiyon*) seçeneği, yalnızca kendi programlama DILINIZDE bir LINQ sorgusu yazarak ve ardından sonuçları almak için bu sorguyu yürüterek elde edilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendisi tüm gerekli işlemleri, bildiğiniz gerekli SQL işlemlerine çevirir. Daha fazla bilgi için bkz. [LINQ to SQL](index.md).  
  
 Aşağıdaki örnekte, Londra 'daki müşterilerin şirket adları, konsol penceresinde alınır ve görüntülenir.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Takma  
 Bir SQL `Insert`yürütmek için, yalnızca oluşturduğunuz nesne modeline nesne ekleyin ve <xref:System.Data.Linq.DataContext><xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırın.  
  
 Aşağıdaki örnekte, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>kullanılarak `Customers` tabloya yeni bir müşteri ve müşteri hakkındaki bilgiler eklenir.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Güncelleniyor  
 Bir veritabanı girişini `Update` için önce öğeyi alın ve doğrudan nesne modelinde düzenleyin. Nesne değiştirildikten sonra veritabanını güncelleştirmek için <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırın.  
  
 Aşağıdaki örnekte, Londra 'dan gelen tüm müşteriler alınır. Ardından, şehir adı "Londra" iken "Londra-Metro" olarak değiştirilir. Son olarak, değişiklikleri veritabanına göndermek için <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Siliniyor  
 Bir öğeyi `Delete` için, öğeyi ait olduğu koleksiyondan kaldırın ve ardından değişikliği uygulamak için <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırın.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] basamaklı silme işlemlerini tanımıyor. Kısıtlama içeren bir tablodaki bir satırı silmek isterseniz, bkz. [nasıl yapılır: satırları veritabanından silme](how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki örnekte, `98128` `CustomerID` olan müşteri veritabanından alınır. Ardından, müşteri satırının alındığını onayladıktan sonra, bu nesneyi koleksiyondan kaldırmak için <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> çağırılır. Son olarak, silme işlemini veritabanına iletmek için <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırılır.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [Başlarken](getting-started.md)
