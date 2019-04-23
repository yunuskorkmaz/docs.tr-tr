---
title: 'Nasıl yapılır: Veritabanına Bağlanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: f04726bc12fdfbca530ee5533d5b8969addf962e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208143"
---
# <a name="how-to-connect-to-a-database"></a>Nasıl yapılır: Veritabanına Bağlanma
<xref:System.Data.Linq.DataContext> Olduğu ana conduit, bir veritabanına bağlanmak, nesneleri alabilirsiniz ve yapılan değişikliklerin geri gönderin. Kullandığınız <xref:System.Data.Linq.DataContext> kullanacağınız gibi bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>. Aslında, <xref:System.Data.Linq.DataContext> bir bağlantı veya sağladığınız bağlantı dizesi ile başlatılır. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Amacı <xref:System.Data.Linq.DataContext> SQL sorguları veritabanına karşı yapılacak nesneler için isteklerinizi küçültmesini olduğu ve sonra sonuçları nesneleri birleştirmek için. <xref:System.Data.Linq.DataContext> Sağlayan [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] gibi standart sorgu işleçleri, aynı işleci desenle uygulayarak `Where` ve `Select`.  
  
> [!IMPORTANT]
>  Güvenli bağlantıyı sürdürme en yüksek önem derecesi olur. Daha fazla bilgi için [LINQ to SQL'de güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanma ve, şehir, Londra olan müşterilerin satırlarını almak için kullanılır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Her veritabanı tablosu olarak temsil edilen bir `Table` koleksiyonu sunar kullanılabilir <xref:System.Data.Linq.DataContext.GetTable%2A> tanımlamak için varlık sınıfı kullanarak yöntemi.  
  
## <a name="example"></a>Örnek  
 En iyi uygulamadır türü kesin belirlenmiş bildirmek için <xref:System.Data.Linq.DataContext> basic kalmak yerine <xref:System.Data.Linq.DataContext> sınıfı ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi. Türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> tüm bildirir `Table` koleksiyonları bağlamı, aşağıdaki örnekte olduğu gibi bir üyesi olarak.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Londralı müşteriler için sorgu ifade ardından edebilirsiniz daha basit olarak:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı ile İletişim Kurma](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
