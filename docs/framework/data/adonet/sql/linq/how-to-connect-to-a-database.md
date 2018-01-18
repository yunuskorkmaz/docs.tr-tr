---
title: "Nasıl yapılır: bir veritabanına bağlan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a5447ce64803405668a2d486c7b3071b5ff923cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="6216d-102">Nasıl yapılır: bir veritabanına bağlan</span><span class="sxs-lookup"><span data-stu-id="6216d-102">How to: Connect to a Database</span></span>
<span data-ttu-id="6216d-103"><xref:System.Data.Linq.DataContext> , Bir veritabanına bağlanmak, nesneleri ondan almak ve yapılan değişikliklerin geri göndermek ana conduit değil.</span><span class="sxs-lookup"><span data-stu-id="6216d-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="6216d-104">Kullandığınız <xref:System.Data.Linq.DataContext> kullanacağınız gibi bir [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="6216d-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="6216d-105">Aslında, <xref:System.Data.Linq.DataContext> bir bağlantı veya sağladığınız bağlantı dizesi ile başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="6216d-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="6216d-106">Daha fazla bilgi için bkz: [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="6216d-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="6216d-107">Amacı <xref:System.Data.Linq.DataContext> halinde veritabanıyla yapılması SQL sorguları isteklerinizi nesneler için geçersizdir ve ardından sonuçları dışında nesnelerin araya getirmek için.</span><span class="sxs-lookup"><span data-stu-id="6216d-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="6216d-108"><xref:System.Data.Linq.DataContext> Sağlayan [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] standart sorgu işleçleri olarak aynı işleci düzeni gibi uygulama tarafından `Where` ve `Select`.</span><span class="sxs-lookup"><span data-stu-id="6216d-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6216d-109">Güvenli bir bağlantı koruma yüksek çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6216d-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="6216d-110">Daha fazla bilgi için bkz: [LINQ-SQL güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6216d-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6216d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6216d-111">Example</span></span>  
 <span data-ttu-id="6216d-112">Aşağıdaki örnekte, <xref:System.Data.Linq.DataContext> Northwind örnek veritabanına bağlanmak ve, şehir Londra olan müşterilerin satırlarını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6216d-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="6216d-113">Her veritabanı tablosu olarak temsil edilen bir `Table` koleksiyon tarafından yolu, kullanılabilir <xref:System.Data.Linq.DataContext.GetTable%2A> tanımlamak için varlık sınıfı kullanarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6216d-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6216d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6216d-114">Example</span></span>  
 <span data-ttu-id="6216d-115">En iyi uygulamadır kesin türü belirtilmiş bildirmek için <xref:System.Data.Linq.DataContext> basic kalmak yerine <xref:System.Data.Linq.DataContext> sınıfı ve <xref:System.Data.Linq.DataContext.GetTable%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6216d-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="6216d-116">Kesin türü belirtilmiş <xref:System.Data.Linq.DataContext> tüm bildirir `Table` koleksiyon üyeleri aşağıdaki örnekteki gibi bağlamının olarak.</span><span class="sxs-lookup"><span data-stu-id="6216d-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="6216d-117">Londra müşteriler için sorgu ifade sonra edebilirsiniz daha basit bir şekilde olarak:</span><span class="sxs-lookup"><span data-stu-id="6216d-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6216d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6216d-118">See Also</span></span>  
 [<span data-ttu-id="6216d-119">Veritabanı ile İletişim Kurma</span><span class="sxs-lookup"><span data-stu-id="6216d-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
