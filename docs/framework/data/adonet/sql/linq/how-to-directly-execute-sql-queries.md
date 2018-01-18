---
title: "Nasıl yapılır: doğrudan SQL sorgularını Yürüt"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 000a7c50edacbae09675a9f9069f56aa6cd211f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="eff68-102">Nasıl yapılır: doğrudan SQL sorgularını Yürüt</span><span class="sxs-lookup"><span data-stu-id="eff68-102">How to: Directly Execute SQL Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eff68-103">(metin biçiminde) parametreli SQL sorguları içine yazma sorguları çevirir ve bunları SQL server için işlem gönderir.</span><span class="sxs-lookup"><span data-stu-id="eff68-103"> translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="eff68-104">Uygulamanızı yerel olarak kullanılabilir yöntemleri çeşitli SQL yürütülemiyor.</span><span class="sxs-lookup"><span data-stu-id="eff68-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eff68-105">Bu yerel yöntemleri eşdeğer işlemler ve SQL ortamın içinde kullanılabilen işlevlerin dönüştürmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="eff68-105"> tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="eff68-106">Birçok yöntem ve işleçlerini [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yerleşik türleri SQL komutlarını doğrudan çevirileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eff68-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="eff68-107">Bazı kullanılabilir işlevlerden üretilebilir.</span><span class="sxs-lookup"><span data-stu-id="eff68-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="eff68-108">Üretilemez o çalışma zamanı özel durumları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eff68-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="eff68-109">Daha fazla bilgi için bkz: [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="eff68-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="eff68-110">Durumlarda burada bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu özel bir görev için yeterli değil, kullanabileceğiniz <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> bir SQL sorgusu yürütme ve sorgunuzu sonuç nesnelerini doğrudan dönüştürmeniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eff68-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff68-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eff68-111">Example</span></span>  
 <span data-ttu-id="eff68-112">Aşağıdaki örnekte, varsayımında verilerini `Customer` sınıfı (customer1 ve customer2) üzerinde iki tablo yayılır.</span><span class="sxs-lookup"><span data-stu-id="eff68-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="eff68-113">Sorgu bir dizi döndürür `Customer` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="eff68-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="eff68-114">Tablo sonuçları sütun adlarının sütun özellikleri varlık sınıfınızın eşleştiği sürece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerinizi dışında herhangi bir SQL sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eff68-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff68-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="eff68-115">Example</span></span>  
 <span data-ttu-id="eff68-116"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Yöntemi için parametreler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="eff68-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="eff68-117">Parametreli bir sorgu yürütmek için kodu aşağıdaki gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="eff68-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="eff68-118">Tarafından kullanılan aynı süslü gösterimini kullanarak sorgu metni ifade parametreleri `Console.WriteLine()` ve `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="eff68-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="eff68-119">Aslında, `String.Format()` gerçekten sağlarsanız, süslü küme ayracı içine alınan parametrelerle değiştirerek oluşturulan parametre adları gibi sorgu dizesi olarak da adlandırılır @p0, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="eff68-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff68-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eff68-120">See Also</span></span>  
 [<span data-ttu-id="eff68-121">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="eff68-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="eff68-122">Veritabanını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="eff68-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
