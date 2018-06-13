---
title: LINQ-SQL ile yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 719c2e5c97d3f8c64de53831ac50b2e7156a38fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356424"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ-SQL ile yapabilecekleriniz
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL geliştirici olarak beklediğiniz tüm anahtar özelliklerini destekler. Bilgi için sorgu ve Ekle, Güncelleştir ve bilgileri tablodan silin.  
  
## <a name="selecting"></a>Seçme  
 Seçme (*projeksiyon*) yalnızca yazarak elde edilen bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgu kendi programlama dilinde ve sonuçları almak için sorgu yürütme. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendisini bilginiz gerekli SQL işlemleri gerekli tüm işlemlere çevirir. Daha fazla bilgi için bkz: [LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Aşağıdaki örnekte, Londra müşterilerden şirket adlarını alınır ve konsol penceresinde görüntülenir.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Ekleme  
 Bir SQL yürütmek için `Insert`, yalnızca nesneler oluşturdunuz nesne modeli ve arama Ekle <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.  
  
 Aşağıdaki örnekte, yeni müşteri ve müşteri hakkındaki bilgiler eklenen `Customers` kullanarak tablo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Güncelleştirme  
 İçin `Update` bir veritabanı girişi ilk öğe almak ve doğrudan nesne modelinde düzenleyin. Nesne değiştirdikten sonra arama <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> veritabanını güncelleştirmek için.  
  
 Aşağıdaki örnekte, Londra'dan olan tüm müşterilerin alınır. Ardından şehrin adı "İçin Londra – Metro" "Londra'dan" değiştirilir. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> değişiklikleri veritabanına göndermek için çağrılır.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Silme  
 İçin `Delete` bir öğe öğenin ait olduğu koleksiyonu ve ardından arama kaldırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> değişikliği kaydetmek için.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Art arda silme işlemleri tanımıyor. Tablodaki satır silmek istiyorsanız, bunu karşı kısıtlamalarına sahip, bkz: [nasıl yapılır: Sil satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki örnekte, olan müşteri `CustomerID` , `98128` veritabanından alınır. Ardından, müşteri satır alındığını onaylayan sonra <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> söz konusu nesne koleksiyondan kaldırmak için çağrılır. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanı silme iletmek için çağrılır.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
