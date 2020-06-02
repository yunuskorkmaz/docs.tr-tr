---
title: 'Nasıl yapılır: Doğrudan SQL Sorguları Yürütme'
description: Bir sorgu çalıştırmak için ExecuteQuery kullanmayı ve sonra sonuçları bir LINQ to SQL sorgusunun yetersiz olduğu durumlarda doğrudan nesnelere dönüştürmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286371"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="0b371-103">Nasıl yapılır: Doğrudan SQL Sorguları Yürütme</span><span class="sxs-lookup"><span data-stu-id="0b371-103">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b371-104">yazdığınız sorguları parametreli SQL sorgularına çevirir (metin biçiminde) ve bunları işlenmek üzere SQL Server 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="0b371-104">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="0b371-105">SQL, uygulamanız için yerel olarak kullanılabilir olabilecek çeşitli yöntemler yürütemiyor.</span><span class="sxs-lookup"><span data-stu-id="0b371-105">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b371-106">Bu yerel yöntemleri SQL ortamında bulunan eşdeğer işlemlere ve işlevlere dönüştürmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="0b371-106">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="0b371-107">.NET Framework yerleşik türler üzerindeki yöntemlerin ve işleçlerin çoğu SQL komutlarına doğrudan Çeviriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b371-107">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="0b371-108">Bazıları kullanılabilir işlevlerden üretilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b371-108">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="0b371-109">Üretilemez çalışma zamanı özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b371-109">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="0b371-110">Daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b371-110">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="0b371-111">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgunun özelleşmiş bir görevde yetersiz olduğu durumlarda, <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> bir SQL sorgusunu yürütmek için yöntemini kullanabilir ve sonra sorgunuzun sonucunu doğrudan nesnelere dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b371-111">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b371-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b371-112">Example</span></span>  
 <span data-ttu-id="0b371-113">Aşağıdaki örnekte, `Customer` sınıfının verilerinin iki tabloya yayıldığını varsayın (customer1 ve customer2).</span><span class="sxs-lookup"><span data-stu-id="0b371-113">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="0b371-114">Sorgu bir nesne dizisi döndürür `Customer` .</span><span class="sxs-lookup"><span data-stu-id="0b371-114">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="0b371-115">Tablo sonuçlarındaki sütun adları, varlık sınıfınızın sütun özellikleriyle eşleştiği sürece, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi herhangi BIR SQL sorgusundan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b371-115">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b371-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b371-116">Example</span></span>  
 <span data-ttu-id="0b371-117"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Yöntemi ayrıca parametreler için de izin verir.</span><span class="sxs-lookup"><span data-stu-id="0b371-117">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="0b371-118">Parametreli bir sorgu yürütmek için aşağıdaki gibi bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b371-118">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="0b371-119">Parametreler, ve tarafından kullanılan aynı süslü gösterimi kullanılarak sorgu metninde ifade edilir `Console.WriteLine()` `String.Format()` .</span><span class="sxs-lookup"><span data-stu-id="0b371-119">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="0b371-120">Aslında, `String.Format()` sağladığınız sorgu dizesinde çağrılır, ancak küme dışı parametreleri,... @p0 @p1 , (n) gibi oluşturulmuş parametre adlarıyla değiştirerek @p .</span><span class="sxs-lookup"><span data-stu-id="0b371-120">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b371-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b371-121">See also</span></span>

- [<span data-ttu-id="0b371-122">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="0b371-122">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="0b371-123">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="0b371-123">Querying the Database</span></span>](querying-the-database.md)
