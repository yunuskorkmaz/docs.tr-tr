---
title: 'Nasıl yapılır: Veritabanına Bağlanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: ebf630c08714a2e5162ba072f88b7fbdef7ca0f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964055"
---
# <a name="how-to-connect-to-a-database"></a>Nasıl yapılır: Veritabanına Bağlanma
, <xref:System.Data.Linq.DataContext> Bir veritabanına bağlandığınız, nesneleri buradan alacağınız ve değişiklikleri geri gönderen ana iletken. <xref:System.Data.Linq.DataContext> Yalnızca bir ADO.net <xref:System.Data.SqlClient.SqlConnection>kullandığınız gibi kullanırsınız. Aslında <xref:System.Data.Linq.DataContext> , sağladığınız bir bağlantı veya bağlantı dizesi ile başlatılır. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 ' Nin <xref:System.Data.Linq.DataContext> amacı, veritabanına karşı yapılacak isteklerinizi SQL sorgularına dönüştürmek ve ardından nesneleri sonuçlardan elde etmek üzere çevirsağlamaktır. <xref:System.Data.Linq.DataContext> [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] , `Where` Ve gibistandartsorguişleçleriileaynıoperatördeseninin`Select`uygulanması ile etkinleştirilir.  
  
> [!IMPORTANT]
> Güvenli bir bağlantının sürdürülmesi en yüksek öneme sahiptir. Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Data.Linq.DataContext> , Northwind örnek veritabanına bağlanmak ve şehri Londra olan müşterilerin satırlarını almak için kullanılır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Her veritabanı tablosu, `Table` <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi tarafından kullanılabilen bir koleksiyon olarak temsil edilir.  
  
## <a name="example"></a>Örnek  
 En iyi yöntem, temel <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext> sınıfa ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemine güvenmek yerine kesin bir tür bildirimi kullanmaktır. Türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> , aşağıdaki `Table` örnekte olduğu gibi tüm koleksiyonları bağlamın üyesi olarak bildirir.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Daha sonra Londra 'dan daha basit bir şekilde sorgu yapabilirsiniz:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı ile İletişim Kurma](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
