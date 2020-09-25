---
title: 'Nasıl yapılır: Veritabanına Bağlanma'
description: LINQ to SQL ' de bir veritabanına bağlanmak için DataContext 'i kullanmayı öğrenin. Bir veritabanına bağlanmak ve satır almak için DataContext 'i kullanmak üzere bu örneklere bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: ebd45b92abf3bf300fa5fa06dbb4e92354fac3c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173503"
---
# <a name="how-to-connect-to-a-database"></a>Nasıl yapılır: Veritabanına Bağlanma

, <xref:System.Data.Linq.DataContext> Bir veritabanına bağlandığınız, nesneleri buradan alacağınız ve değişiklikleri geri gönderen ana iletken. <xref:System.Data.Linq.DataContext>Yalnızca bir ADO.net kullandığınız gibi kullanırsınız <xref:System.Data.SqlClient.SqlConnection> . Aslında, <xref:System.Data.Linq.DataContext> sağladığınız bir bağlantı veya bağlantı dizesi ile başlatılır. Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 ' Nin amacı, <xref:System.Data.Linq.DataContext> veritabanına karşı yapılacak ISTEKLERINIZI SQL sorgularına dönüştürmek ve ardından nesneleri sonuçlardan elde etmek üzere çevirsağlamaktır. , <xref:System.Data.Linq.DataContext> Ve gibi standart sorgu işleçleri ile aynı işleç modelini uygulayarak dil Ile tümleşik sorgu (LINQ) etkinleştirilir `Where` `Select` .  
  
> [!IMPORTANT]
> Güvenli bir bağlantının sürdürülmesi en yüksek öneme sahiptir. Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve şehri Londra olan müşterilerin satırlarını almak için kullanılır.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Her veritabanı tablosu `Table` , yöntemi tarafından kullanılabilen bir koleksiyon olarak temsil edilir <xref:System.Data.Linq.DataContext.GetTable%2A> .  
  
## <a name="example"></a>Örnek  

 En iyi yöntem, <xref:System.Data.Linq.DataContext> temel <xref:System.Data.Linq.DataContext> sınıfa ve yöntemine güvenmek yerine kesin bir tür bildirimi kullanmaktır <xref:System.Data.Linq.DataContext.GetTable%2A> . Türü kesin belirlenmiş, <xref:System.Data.Linq.DataContext> `Table` Aşağıdaki örnekte olduğu gibi tüm koleksiyonları bağlamın üyesi olarak bildirir.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Daha sonra Londra 'dan daha basit bir şekilde sorgu yapabilirsiniz:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı ile İletişim Kurma](communicating-with-the-database.md)
