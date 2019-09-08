---
title: 'Nasıl yapılır: Doğrudan SQL Sorguları Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793789"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="8a626-102">Nasıl yapılır: Doğrudan SQL Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="8a626-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8a626-103">yazdığınız sorguları parametreli SQL sorgularına çevirir (metin biçiminde) ve bunları işlenmek üzere SQL Server 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="8a626-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="8a626-104">SQL, uygulamanız için yerel olarak kullanılabilir olabilecek çeşitli yöntemler yürütemiyor.</span><span class="sxs-lookup"><span data-stu-id="8a626-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8a626-105">Bu yerel yöntemleri SQL ortamında bulunan eşdeğer işlemlere ve işlevlere dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="8a626-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="8a626-106">.NET Framework yerleşik türler üzerindeki yöntemlerin ve işleçlerin çoğu SQL komutlarına doğrudan Çeviriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a626-106">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="8a626-107">Bazıları kullanılabilir işlevlerden üretilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a626-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="8a626-108">Üretilemez çalışma zamanı özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a626-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="8a626-109">Daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="8a626-109">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="8a626-110">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgunun özelleşmiş bir görevde yetersiz olduğu durumlarda, bir SQL sorgusunu yürütmek için <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> yöntemini kullanabilir ve sonra sorgunuzun sonucunu doğrudan nesnelere dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a626-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a626-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a626-111">Example</span></span>  
 <span data-ttu-id="8a626-112">Aşağıdaki örnekte, `Customer` sınıfının verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2).</span><span class="sxs-lookup"><span data-stu-id="8a626-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="8a626-113">Sorgu bir `Customer` nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a626-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="8a626-114">Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi bir SQL sorgusundan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a626-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a626-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a626-115">Example</span></span>  
 <span data-ttu-id="8a626-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi Ayrıca parametreler için de izin verir.</span><span class="sxs-lookup"><span data-stu-id="8a626-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="8a626-117">Parametreli bir sorgu yürütmek için aşağıdaki gibi bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a626-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="8a626-118">Parametreler, ve `Console.WriteLine()` `String.Format()`tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="8a626-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="8a626-119">Aslında, sağladığınız sorgu dizesinde çağrılır, @p0 @p1 @pancakkümedışı parametreleri,..., (n) gibi oluşturulmuş parametre adlarıyla değiştirerek. `String.Format()`</span><span class="sxs-lookup"><span data-stu-id="8a626-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a626-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a626-120">See also</span></span>

- [<span data-ttu-id="8a626-121">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="8a626-121">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="8a626-122">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="8a626-122">Querying the Database</span></span>](querying-the-database.md)
