---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: efb7b86c3add99e596e6798c8267c09689899d56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231584"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>LINQ to SQL ile Yapabilecekleriniz
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir SQL geliştirici olarak beklediğiniz tüm anahtar özelliklerini destekler. Bilgiler için Sorgulayabileceğiniz ve ekleme, güncelleştirme ve tablolarından bilgi Sil.  
  
## <a name="selecting"></a>Seçme  
 Seçme (*projeksiyon*) yalnızca yazarak elde edilen bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] kendi programlama diliyle sorgulayın ve ardından sonuçları almak için bu sorguyu yürütme. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kendisini bilginiz gerekli SQL işlemleri gerekli tüm işlemlere çevirir. Daha fazla bilgi için [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Aşağıdaki örnekte, şirket adlarını londralı müşteriler alınır ve konsol penceresinde görüntülenir.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Ekleme  
 Bir SQL yürütme `Insert`, nesneleri oluşturduğunuz nesne modeli ve çağrı eklemeniz yeterlidir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.  
  
 Aşağıdaki örnekte, yeni müşteri ve müşteri hakkındaki bilgiler eklenen `Customers` kullanarak tablo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Güncelleştirme  
 İçin `Update` bir veritabanı girişi, ilk öğeyi almak ve doğrudan nesne modelinde düzenleyin. Nesne değiştirdikten sonra çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> veritabanını güncellemek için.  
  
 Aşağıdaki örnekte, Londra'dan tüm müşterileri alınır. Ardından şehir adı "London" "London – Metro için" değiştirilir. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanına değişiklikleri göndermek için çağrılır.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Silme  
 İçin `Delete` , öğenin ait olduğu koleksiyon ve sonra çağrı öğesini kaldırmak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> değişikliği kaydetmek için.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Art arda silme işlemleri algılamaz. Bunlara karşı kısıtlamaları olan bir tablosunda bir satıra silmek istiyorsanız, bkz: [nasıl yapılır: Veritabanından satır silme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki örnekte, olan müşteri `CustomerID` , `98128` veritabanından alınır. Ardından, müşteri satır alındığını onayladıktan sonra <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> o nesneyi koleksiyondan kaldırmak için çağrılır. Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanına silme iletmek için çağrılır.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
