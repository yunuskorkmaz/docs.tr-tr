---
title: 'Nasıl yapılır: bir veritabanına bağlanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 837919b1cfcdf46026ccfb37cbbec951c0ae41b8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634683"
---
# <a name="how-to-connect-to-a-database"></a>Nasıl yapılır: bir veritabanına bağlanma
<xref:System.Data.Linq.DataContext>, bir veritabanına bağlandığınız, nesneleri buradan alacağınız ve değişiklikleri geri gönderen ana iletken. <xref:System.Data.Linq.DataContext>, tıpkı bir ADO.NET <xref:System.Data.SqlClient.SqlConnection>kullandığınız gibi kullanırsınız. Aslında <xref:System.Data.Linq.DataContext>, sağladığınız bir bağlantı veya bağlantı dizesi ile başlatılır. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 <xref:System.Data.Linq.DataContext> amacı, nesne isteklerinizi veritabanına yönelik olarak SQL sorgularına dönüştürmek ve ardından nesneleri sonuçlardan elde etmek için çevirsağlamaktır. <xref:System.Data.Linq.DataContext>, `Where` ve `Select`gibi standart sorgu Işleçleriyle aynı operatör modelini uygulayarak dil ile tümleşik sorgu (LINQ) imkanı sunar.  
  
> [!IMPORTANT]
> Güvenli bir bağlantının sürdürülmesi en yüksek öneme sahiptir. Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve şehri Londra olan müşterilerin satırlarını almak için kullanılır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Her veritabanı tablosu, <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi tarafından kullanılabilen `Table` bir koleksiyon olarak temsil edilir.  
  
## <a name="example"></a>Örnek  
 En iyi yöntem, temel <xref:System.Data.Linq.DataContext> sınıfına ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemine güvenmek yerine, türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> bildirmenin bir yöntemidir. Türü kesin belirlenmiş <xref:System.Data.Linq.DataContext>, aşağıdaki örnekte olduğu gibi tüm `Table` koleksiyonları bağlamın üyesi olarak bildirir.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Daha sonra Londra 'dan daha basit bir şekilde sorgu yapabilirsiniz:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
