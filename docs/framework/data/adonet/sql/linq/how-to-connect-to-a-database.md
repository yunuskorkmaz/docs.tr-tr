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
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="eb8c7-102">Nasıl yapılır: bir veritabanına bağlanma</span><span class="sxs-lookup"><span data-stu-id="eb8c7-102">How to: Connect to a Database</span></span>
<span data-ttu-id="eb8c7-103"><xref:System.Data.Linq.DataContext>, bir veritabanına bağlandığınız, nesneleri buradan alacağınız ve değişiklikleri geri gönderen ana iletken.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="eb8c7-104"><xref:System.Data.Linq.DataContext>, tıpkı bir ADO.NET <xref:System.Data.SqlClient.SqlConnection>kullandığınız gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="eb8c7-105">Aslında <xref:System.Data.Linq.DataContext>, sağladığınız bir bağlantı veya bağlantı dizesi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="eb8c7-106">Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="eb8c7-107"><xref:System.Data.Linq.DataContext> amacı, nesne isteklerinizi veritabanına yönelik olarak SQL sorgularına dönüştürmek ve ardından nesneleri sonuçlardan elde etmek için çevirsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="eb8c7-108"><xref:System.Data.Linq.DataContext>, `Where` ve `Select`gibi standart sorgu Işleçleriyle aynı operatör modelini uygulayarak dil ile tümleşik sorgu (LINQ) imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-108">The <xref:System.Data.Linq.DataContext> enables Language-Integrated Query (LINQ) by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb8c7-109">Güvenli bir bağlantının sürdürülmesi en yüksek öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="eb8c7-110">Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eb8c7-110">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb8c7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb8c7-111">Example</span></span>  
 <span data-ttu-id="eb8c7-112">Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve şehri Londra olan müşterilerin satırlarını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="eb8c7-113">Her veritabanı tablosu, <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi tarafından kullanılabilen `Table` bir koleksiyon olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb8c7-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb8c7-114">Example</span></span>  
 <span data-ttu-id="eb8c7-115">En iyi yöntem, temel <xref:System.Data.Linq.DataContext> sınıfına ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemine güvenmek yerine, türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> bildirmenin bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="eb8c7-116">Türü kesin belirlenmiş <xref:System.Data.Linq.DataContext>, aşağıdaki örnekte olduğu gibi tüm `Table` koleksiyonları bağlamın üyesi olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="eb8c7-117">Daha sonra Londra 'dan daha basit bir şekilde sorgu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb8c7-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="eb8c7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb8c7-118">See also</span></span>

- [<span data-ttu-id="eb8c7-119">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="eb8c7-119">Communicating with the Database</span></span>](communicating-with-the-database.md)
