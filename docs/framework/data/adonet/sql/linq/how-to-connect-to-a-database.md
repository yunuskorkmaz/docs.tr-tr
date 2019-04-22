---
title: 'Nasıl yapılır: Veritabanına Bağlanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: f04726bc12fdfbca530ee5533d5b8969addf962e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208143"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="3ddb7-102">Nasıl yapılır: Veritabanına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="3ddb7-102">How to: Connect to a Database</span></span>
<span data-ttu-id="3ddb7-103"><xref:System.Data.Linq.DataContext> Olduğu ana conduit, bir veritabanına bağlanmak, nesneleri alabilirsiniz ve yapılan değişikliklerin geri gönderin.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="3ddb7-104">Kullandığınız <xref:System.Data.Linq.DataContext> kullanacağınız gibi bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="3ddb7-105">Aslında, <xref:System.Data.Linq.DataContext> bir bağlantı veya sağladığınız bağlantı dizesi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="3ddb7-106">Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="3ddb7-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="3ddb7-107">Amacı <xref:System.Data.Linq.DataContext> SQL sorguları veritabanına karşı yapılacak nesneler için isteklerinizi küçültmesini olduğu ve sonra sonuçları nesneleri birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="3ddb7-108"><xref:System.Data.Linq.DataContext> Sağlayan [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] gibi standart sorgu işleçleri, aynı işleci desenle uygulayarak `Where` ve `Select`.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ddb7-109">Güvenli bağlantıyı sürdürme en yüksek önem derecesi olur.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="3ddb7-110">Daha fazla bilgi için [LINQ to SQL'de güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3ddb7-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ddb7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ddb7-111">Example</span></span>  
 <span data-ttu-id="3ddb7-112">Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanma ve, şehir, Londra olan müşterilerin satırlarını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="3ddb7-113">Her veritabanı tablosu olarak temsil edilen bir `Table` koleksiyonu sunar kullanılabilir <xref:System.Data.Linq.DataContext.GetTable%2A> tanımlamak için varlık sınıfı kullanarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ddb7-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ddb7-114">Example</span></span>  
 <span data-ttu-id="3ddb7-115">En iyi uygulamadır türü kesin belirlenmiş bildirmek için <xref:System.Data.Linq.DataContext> basic kalmak yerine <xref:System.Data.Linq.DataContext> sınıfı ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="3ddb7-116">Türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> tüm bildirir `Table` koleksiyonları bağlamı, aşağıdaki örnekte olduğu gibi bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="3ddb7-117">Londralı müşteriler için sorgu ifade ardından edebilirsiniz daha basit olarak:</span><span class="sxs-lookup"><span data-stu-id="3ddb7-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3ddb7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ddb7-118">See also</span></span>

- [<span data-ttu-id="3ddb7-119">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="3ddb7-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
