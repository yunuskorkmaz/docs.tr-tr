---
title: 'Nasıl yapılır: Veritabanına Bağlanma'
description: LINQ to SQL ' de bir veritabanına bağlanmak için DataContext 'i kullanmayı öğrenin. Bir veritabanına bağlanmak ve satır almak için DataContext 'i kullanmak üzere bu örneklere bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: c3320a598cb8407ab584530c615c2e5ef0de53c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286410"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="eac33-104">Nasıl yapılır: Veritabanına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="eac33-104">How to: Connect to a Database</span></span>
<span data-ttu-id="eac33-105">, <xref:System.Data.Linq.DataContext> Bir veritabanına bağlandığınız, nesneleri buradan alacağınız ve değişiklikleri geri gönderen ana iletken.</span><span class="sxs-lookup"><span data-stu-id="eac33-105">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="eac33-106"><xref:System.Data.Linq.DataContext>Yalnızca bir ADO.net kullandığınız gibi kullanırsınız <xref:System.Data.SqlClient.SqlConnection> .</span><span class="sxs-lookup"><span data-stu-id="eac33-106">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="eac33-107">Aslında, <xref:System.Data.Linq.DataContext> sağladığınız bir bağlantı veya bağlantı dizesi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="eac33-107">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="eac33-108">Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="eac33-108">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="eac33-109">' Nin amacı, <xref:System.Data.Linq.DataContext> veritabanına karşı yapılacak ISTEKLERINIZI SQL sorgularına dönüştürmek ve ardından nesneleri sonuçlardan elde etmek üzere çevirsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="eac33-109">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="eac33-110">, <xref:System.Data.Linq.DataContext> Ve gibi standart sorgu işleçleri ile aynı işleç modelini uygulayarak dil Ile tümleşik sorgu (LINQ) etkinleştirilir `Where` `Select` .</span><span class="sxs-lookup"><span data-stu-id="eac33-110">The <xref:System.Data.Linq.DataContext> enables Language-Integrated Query (LINQ) by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eac33-111">Güvenli bir bağlantının sürdürülmesi en yüksek öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eac33-111">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="eac33-112">Daha fazla bilgi için bkz. [LINQ to SQL güvenlik](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="eac33-112">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac33-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="eac33-113">Example</span></span>  
 <span data-ttu-id="eac33-114">Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve şehri Londra olan müşterilerin satırlarını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eac33-114">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="eac33-115">Her veritabanı tablosu `Table` , yöntemi tarafından kullanılabilen bir koleksiyon olarak temsil edilir <xref:System.Data.Linq.DataContext.GetTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="eac33-115">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac33-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="eac33-116">Example</span></span>  
 <span data-ttu-id="eac33-117">En iyi yöntem, <xref:System.Data.Linq.DataContext> temel <xref:System.Data.Linq.DataContext> sınıfa ve yöntemine güvenmek yerine kesin bir tür bildirimi kullanmaktır <xref:System.Data.Linq.DataContext.GetTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="eac33-117">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="eac33-118">Türü kesin belirlenmiş, <xref:System.Data.Linq.DataContext> `Table` Aşağıdaki örnekte olduğu gibi tüm koleksiyonları bağlamın üyesi olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="eac33-118">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="eac33-119">Daha sonra Londra 'dan daha basit bir şekilde sorgu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eac33-119">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="eac33-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eac33-120">See also</span></span>

- [<span data-ttu-id="eac33-121">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="eac33-121">Communicating with the Database</span></span>](communicating-with-the-database.md)
