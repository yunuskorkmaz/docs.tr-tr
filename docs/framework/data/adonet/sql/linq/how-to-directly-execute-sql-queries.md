---
title: 'Nasıl yapılır: Doğrudan SQL sorguları yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 1caf81df5998e5aaef4ad011a399d70aff43ca9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634464"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="40495-102">Nasıl yapılır: Doğrudan SQL sorguları yürütme</span><span class="sxs-lookup"><span data-stu-id="40495-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="40495-103">parametrelenmiş SQL sorgularını (metin biçiminde) içine yazma sorguları çevirir ve bunları SQL server için işlem gönderir.</span><span class="sxs-lookup"><span data-stu-id="40495-103">translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="40495-104">Uygulamanızı yerel olarak kullanılabilir yöntemleri çeşitli SQL yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="40495-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="40495-105">Bu yerel yöntemlerin eşdeğer işlemlere ve SQL ortamı içinde kullanılabilen işlevleri dönüştürmeye çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="40495-105">tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="40495-106">Birçok yöntem ve işleçlerde [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] SQL komutları doğrudan çevirileri yerleşik türlerine sahip.</span><span class="sxs-lookup"><span data-stu-id="40495-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="40495-107">Bazı kullanılabilir olan işlevleri üretilebilir.</span><span class="sxs-lookup"><span data-stu-id="40495-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="40495-108">Üretilemeyebilir o çalışma zamanı özel durumlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40495-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="40495-109">Daha fazla bilgi için [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="40495-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="40495-110">Durumlarda burada bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu için özel bir görev yetersiz, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> bir SQL sorgusu Yürüt ve sonra sorgu sonucu doğrudan nesnelerine dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="40495-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40495-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="40495-111">Example</span></span>  
 <span data-ttu-id="40495-112">Aşağıdaki örnekte, varsayımında verilerini `Customer` sınıfı üzerinde iki tablo (customer1 ve customer2) yayılır.</span><span class="sxs-lookup"><span data-stu-id="40495-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="40495-113">Sorgu bir dizi döndürür `Customer` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="40495-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="40495-114">Sütun özellikleri varlık sınıfınızın tablo sonuçları sütun adlarının eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40495-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40495-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="40495-115">Example</span></span>  
 <span data-ttu-id="40495-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi için parametreler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="40495-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="40495-117">Parametreli bir sorgu yürütmek için kod aşağıdaki gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="40495-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="40495-118">Tarafından kullanılan aynı küme gösterimini kullanarak sorgu metni ifade parametreleri `Console.WriteLine()` ve `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="40495-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="40495-119">Aslında, `String.Format()` gerçekten sağlarsanız, Küme Küme ayracıyla belirtilen parametrelerle değiştirerek oluşturulan parametre adları gibi sorgu dizesine göre adlandırılır @p0, @p1 ... @p(n).</span><span class="sxs-lookup"><span data-stu-id="40495-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40495-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40495-120">See also</span></span>
- [<span data-ttu-id="40495-121">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="40495-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="40495-122">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="40495-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
