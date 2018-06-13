---
title: Şema kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357263"
---
# <a name="schema-restrictions"></a><span data-ttu-id="c6f36-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="c6f36-102">Schema Restrictions</span></span>
<span data-ttu-id="c6f36-103">İkinci isteğe bağlı parametresi, **GetSchema** yöntemdir şema bilgi tutarını sınırlamak için kullanılan kısıtlamaları döndürülür ve için geçirilen **GetSchema** bir dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="c6f36-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="c6f36-104">Dizideki konumu geçirebilirsiniz değerleri belirler ve bu kısıtlama sayıya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="c6f36-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6f36-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="c6f36-106">SQL Server şeması koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="c6f36-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-107">Restriction Name</span></span>|<span data-ttu-id="c6f36-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-108">Parameter Name</span></span>|<span data-ttu-id="c6f36-109">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-109">Restriction Default</span></span>|<span data-ttu-id="c6f36-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-111">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-112">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-113">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-113">1</span></span>|  
|<span data-ttu-id="c6f36-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-114">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-116">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-116">2</span></span>|  
|<span data-ttu-id="c6f36-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-117">Table</span></span>|@Name|<span data-ttu-id="c6f36-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-118">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-119">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-119">3</span></span>|  
|<span data-ttu-id="c6f36-120">TableType</span><span class="sxs-lookup"><span data-stu-id="c6f36-120">TableType</span></span>|@TableType|<span data-ttu-id="c6f36-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6f36-121">TABLE_TYPE</span></span>|<span data-ttu-id="c6f36-122">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="c6f36-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="c6f36-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="c6f36-124">"Tablo" şema koleksiyonu kısıtlamalarını birini kullanmak için yalnızca bir dizeler dizisi ile dört öğeleri oluşturun, sonra bir değer kısıtlama numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c6f36-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="c6f36-125">Örneğin, tablolar kısıtlamak için tarafından geri döndürülen **GetSchema** geçirmeden önce "Satış" diziye ikinci öğesini set yöntemi yalnızca "Satış" şemasında tablolara **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6f36-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6f36-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="c6f36-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="c6f36-127">Kısıtlama varsayılan sütunu yine için geriye dönük uyumluluk yoktur, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="c6f36-128">Dize değiştirme yerine parametreli sorgular kısıtlama değerleri belirtirken SQL ekleme saldırı riskini en aza indirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6f36-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6f36-129">Dizideki öğelerin sayısı başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6f36-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="c6f36-130">Olabilir kısıtlamaları maksimum sayısından az.</span><span class="sxs-lookup"><span data-stu-id="c6f36-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="c6f36-131">Eksik kısıtlamaları (sınırsız) null olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c6f36-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="c6f36-132">Çağıran desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="c6f36-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="c6f36-133">Bu döndürülecek bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="c6f36-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c6f36-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6f36-134">Example</span></span>  
 <span data-ttu-id="c6f36-135">Aşağıdaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> şema tüm içinde yer alan tabloları hakkında bilgi almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için yalnızca "Satış" şemasında tablolar için:</span><span class="sxs-lookup"><span data-stu-id="c6f36-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="c6f36-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="c6f36-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="c6f36-137">SQL Server şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="c6f36-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="c6f36-138">Users</span></span>  
  
|<span data-ttu-id="c6f36-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-139">Restriction Name</span></span>|<span data-ttu-id="c6f36-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-140">Parameter Name</span></span>|<span data-ttu-id="c6f36-141">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-141">Restriction Default</span></span>|<span data-ttu-id="c6f36-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-143">User_name</span><span class="sxs-lookup"><span data-stu-id="c6f36-143">User_Name</span></span>|@Name|<span data-ttu-id="c6f36-144">name</span><span class="sxs-lookup"><span data-stu-id="c6f36-144">name</span></span>|<span data-ttu-id="c6f36-145">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="c6f36-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="c6f36-146">Databases</span></span>  
  
|<span data-ttu-id="c6f36-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-147">Restriction Name</span></span>|<span data-ttu-id="c6f36-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-148">Parameter Name</span></span>|<span data-ttu-id="c6f36-149">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-149">Restriction Default</span></span>|<span data-ttu-id="c6f36-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-151">Ad</span><span class="sxs-lookup"><span data-stu-id="c6f36-151">Name</span></span>|@Name|<span data-ttu-id="c6f36-152">Ad</span><span class="sxs-lookup"><span data-stu-id="c6f36-152">Name</span></span>|<span data-ttu-id="c6f36-153">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="c6f36-154">tabloları</span><span class="sxs-lookup"><span data-stu-id="c6f36-154">Tables</span></span>  
  
|<span data-ttu-id="c6f36-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-155">Restriction Name</span></span>|<span data-ttu-id="c6f36-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-156">Parameter Name</span></span>|<span data-ttu-id="c6f36-157">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-157">Restriction Default</span></span>|<span data-ttu-id="c6f36-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-159">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-160">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-161">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-161">1</span></span>|  
|<span data-ttu-id="c6f36-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-162">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-164">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-164">2</span></span>|  
|<span data-ttu-id="c6f36-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-165">Table</span></span>|@Name|<span data-ttu-id="c6f36-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-166">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-167">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-167">3</span></span>|  
|<span data-ttu-id="c6f36-168">TableType</span><span class="sxs-lookup"><span data-stu-id="c6f36-168">TableType</span></span>|@TableType|<span data-ttu-id="c6f36-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6f36-169">TABLE_TYPE</span></span>|<span data-ttu-id="c6f36-170">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6f36-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="c6f36-171">Columns</span></span>  
  
|<span data-ttu-id="c6f36-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-172">Restriction Name</span></span>|<span data-ttu-id="c6f36-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-173">Parameter Name</span></span>|<span data-ttu-id="c6f36-174">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-174">Restriction Default</span></span>|<span data-ttu-id="c6f36-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-176">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-177">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-178">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-178">1</span></span>|  
|<span data-ttu-id="c6f36-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-179">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-181">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-181">2</span></span>|  
|<span data-ttu-id="c6f36-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-182">Table</span></span>|@Table|<span data-ttu-id="c6f36-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-183">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-184">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-184">3</span></span>|  
|<span data-ttu-id="c6f36-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="c6f36-185">Column</span></span>|@Column|<span data-ttu-id="c6f36-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-186">COLUMN_NAME</span></span>|<span data-ttu-id="c6f36-187">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="c6f36-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="c6f36-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="c6f36-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-189">Restriction Name</span></span>|<span data-ttu-id="c6f36-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-190">Parameter Name</span></span>|<span data-ttu-id="c6f36-191">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-191">Restriction Default</span></span>|<span data-ttu-id="c6f36-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-193">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-194">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-195">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-195">1</span></span>|  
|<span data-ttu-id="c6f36-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-196">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-198">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-198">2</span></span>|  
|<span data-ttu-id="c6f36-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-199">Table</span></span>|@Table|<span data-ttu-id="c6f36-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-200">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-201">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-201">3</span></span>|  
|<span data-ttu-id="c6f36-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="c6f36-202">Column</span></span>|@Column|<span data-ttu-id="c6f36-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-203">COLUMN_NAME</span></span>|<span data-ttu-id="c6f36-204">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="c6f36-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="c6f36-205">Views</span></span>  
  
|<span data-ttu-id="c6f36-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-206">Restriction Name</span></span>|<span data-ttu-id="c6f36-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-207">Parameter Name</span></span>|<span data-ttu-id="c6f36-208">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-208">Restriction Default</span></span>|<span data-ttu-id="c6f36-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-210">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-211">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-212">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-212">1</span></span>|  
|<span data-ttu-id="c6f36-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-213">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-215">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-215">2</span></span>|  
|<span data-ttu-id="c6f36-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-216">Table</span></span>|@Table|<span data-ttu-id="c6f36-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-217">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-218">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="c6f36-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="c6f36-219">ViewColumns</span></span>  
  
|<span data-ttu-id="c6f36-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-220">Restriction Name</span></span>|<span data-ttu-id="c6f36-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-221">Parameter Name</span></span>|<span data-ttu-id="c6f36-222">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-222">Restriction Default</span></span>|<span data-ttu-id="c6f36-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-224">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-225">VIEW_CATALOG</span></span>|<span data-ttu-id="c6f36-226">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-226">1</span></span>|  
|<span data-ttu-id="c6f36-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-227">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="c6f36-229">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-229">2</span></span>|  
|<span data-ttu-id="c6f36-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-230">Table</span></span>|@Table|<span data-ttu-id="c6f36-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-231">VIEW_NAME</span></span>|<span data-ttu-id="c6f36-232">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-232">3</span></span>|  
|<span data-ttu-id="c6f36-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="c6f36-233">Column</span></span>|@Column|<span data-ttu-id="c6f36-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-234">COLUMN_NAME</span></span>|<span data-ttu-id="c6f36-235">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c6f36-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6f36-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c6f36-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-237">Restriction Name</span></span>|<span data-ttu-id="c6f36-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-238">Parameter Name</span></span>|<span data-ttu-id="c6f36-239">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-239">Restriction Default</span></span>|<span data-ttu-id="c6f36-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-241">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c6f36-243">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-243">1</span></span>|  
|<span data-ttu-id="c6f36-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-244">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c6f36-246">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-246">2</span></span>|  
|<span data-ttu-id="c6f36-247">Ad</span><span class="sxs-lookup"><span data-stu-id="c6f36-247">Name</span></span>|@Name|<span data-ttu-id="c6f36-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="c6f36-249">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-249">3</span></span>|  
|<span data-ttu-id="c6f36-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="c6f36-250">Parameter</span></span>|@Parameter|<span data-ttu-id="c6f36-251">PARAMETRE_ADÝ</span><span class="sxs-lookup"><span data-stu-id="c6f36-251">PARAMETER_NAME</span></span>|<span data-ttu-id="c6f36-252">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6f36-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c6f36-253">Procedures</span></span>  
  
|<span data-ttu-id="c6f36-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-254">Restriction Name</span></span>|<span data-ttu-id="c6f36-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-255">Parameter Name</span></span>|<span data-ttu-id="c6f36-256">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-256">Restriction Default</span></span>|<span data-ttu-id="c6f36-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-258">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c6f36-260">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-260">1</span></span>|  
|<span data-ttu-id="c6f36-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-261">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c6f36-263">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-263">2</span></span>|  
|<span data-ttu-id="c6f36-264">Ad</span><span class="sxs-lookup"><span data-stu-id="c6f36-264">Name</span></span>|@Name|<span data-ttu-id="c6f36-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="c6f36-266">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-266">3</span></span>|  
|<span data-ttu-id="c6f36-267">Tür</span><span class="sxs-lookup"><span data-stu-id="c6f36-267">Type</span></span>|@Type|<span data-ttu-id="c6f36-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6f36-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="c6f36-269">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="c6f36-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="c6f36-270">IndexColumns</span></span>  
  
|<span data-ttu-id="c6f36-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-271">Restriction Name</span></span>|<span data-ttu-id="c6f36-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-272">Parameter Name</span></span>|<span data-ttu-id="c6f36-273">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-273">Restriction Default</span></span>|<span data-ttu-id="c6f36-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-275">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="c6f36-276">db_name()</span></span>|<span data-ttu-id="c6f36-277">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-277">1</span></span>|  
|<span data-ttu-id="c6f36-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-278">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-279">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="c6f36-279">user_name()</span></span>|<span data-ttu-id="c6f36-280">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-280">2</span></span>|  
|<span data-ttu-id="c6f36-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-281">Table</span></span>|@Table|<span data-ttu-id="c6f36-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="c6f36-282">o.name</span></span>|<span data-ttu-id="c6f36-283">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-283">3</span></span>|  
|<span data-ttu-id="c6f36-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="c6f36-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="c6f36-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="c6f36-285">x.name</span></span>|<span data-ttu-id="c6f36-286">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-286">4</span></span>|  
|<span data-ttu-id="c6f36-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="c6f36-287">Column</span></span>|@Column|<span data-ttu-id="c6f36-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="c6f36-288">c.name</span></span>|<span data-ttu-id="c6f36-289">5</span><span class="sxs-lookup"><span data-stu-id="c6f36-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c6f36-290">Dizinler</span><span class="sxs-lookup"><span data-stu-id="c6f36-290">Indexes</span></span>  
  
|<span data-ttu-id="c6f36-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-291">Restriction Name</span></span>|<span data-ttu-id="c6f36-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-292">Parameter Name</span></span>|<span data-ttu-id="c6f36-293">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-293">Restriction Default</span></span>|<span data-ttu-id="c6f36-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-295">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="c6f36-296">db_name()</span></span>|<span data-ttu-id="c6f36-297">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-297">1</span></span>|  
|<span data-ttu-id="c6f36-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-298">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-299">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="c6f36-299">user_name()</span></span>|<span data-ttu-id="c6f36-300">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-300">2</span></span>|  
|<span data-ttu-id="c6f36-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-301">Table</span></span>|@Table|<span data-ttu-id="c6f36-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="c6f36-302">o.name</span></span>|<span data-ttu-id="c6f36-303">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="c6f36-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="c6f36-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="c6f36-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-305">Restriction Name</span></span>|<span data-ttu-id="c6f36-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-306">Parameter Name</span></span>|<span data-ttu-id="c6f36-307">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-307">Restriction Default</span></span>|<span data-ttu-id="c6f36-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="c6f36-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="c6f36-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="c6f36-310">assemblies.name</span></span>|<span data-ttu-id="c6f36-311">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-311">1</span></span>|  
|<span data-ttu-id="c6f36-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="c6f36-312">udt_name</span></span>|@UDTName|<span data-ttu-id="c6f36-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="c6f36-313">types.assembly_class</span></span>|<span data-ttu-id="c6f36-314">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="c6f36-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="c6f36-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="c6f36-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-316">Restriction Name</span></span>|<span data-ttu-id="c6f36-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-317">Parameter Name</span></span>|<span data-ttu-id="c6f36-318">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-318">Restriction Default</span></span>|<span data-ttu-id="c6f36-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-320">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="c6f36-322">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-322">1</span></span>|  
|<span data-ttu-id="c6f36-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-323">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="c6f36-325">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-325">2</span></span>|  
|<span data-ttu-id="c6f36-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-326">Table</span></span>|@Table|<span data-ttu-id="c6f36-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-327">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-328">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-328">3</span></span>|  
|<span data-ttu-id="c6f36-329">Ad</span><span class="sxs-lookup"><span data-stu-id="c6f36-329">Name</span></span>|@Name|<span data-ttu-id="c6f36-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="c6f36-331">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="c6f36-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="c6f36-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="c6f36-333">SQL Server 2008 şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="c6f36-334">Bu kısıtlamalar sürüm SQL Server 2008 ve .NET Framework 3.5 SP1 ile başlayan geçerli ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6f36-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="c6f36-335">Önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c6f36-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="c6f36-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="c6f36-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="c6f36-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-337">Restriction Name</span></span>|<span data-ttu-id="c6f36-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-338">Parameter Name</span></span>|<span data-ttu-id="c6f36-339">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-339">Restriction Default</span></span>|<span data-ttu-id="c6f36-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-341">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-342">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-343">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-343">1</span></span>|  
|<span data-ttu-id="c6f36-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-344">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-346">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-346">2</span></span>|  
|<span data-ttu-id="c6f36-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-347">Table</span></span>|@Table|<span data-ttu-id="c6f36-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-348">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-349">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="c6f36-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="c6f36-350">AllColumns</span></span>  
  
|<span data-ttu-id="c6f36-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-351">Restriction Name</span></span>|<span data-ttu-id="c6f36-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="c6f36-352">Parameter Name</span></span>|<span data-ttu-id="c6f36-353">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="c6f36-353">Restriction Default</span></span>|<span data-ttu-id="c6f36-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="c6f36-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c6f36-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="c6f36-355">Catalog</span></span>|@Catalog|<span data-ttu-id="c6f36-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6f36-356">TABLE_CATALOG</span></span>|<span data-ttu-id="c6f36-357">1.</span><span class="sxs-lookup"><span data-stu-id="c6f36-357">1</span></span>|  
|<span data-ttu-id="c6f36-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="c6f36-358">Owner</span></span>|@Owner|<span data-ttu-id="c6f36-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6f36-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="c6f36-360">2</span><span class="sxs-lookup"><span data-stu-id="c6f36-360">2</span></span>|  
|<span data-ttu-id="c6f36-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="c6f36-361">Table</span></span>|@Table|<span data-ttu-id="c6f36-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-362">TABLE_NAME</span></span>|<span data-ttu-id="c6f36-363">3</span><span class="sxs-lookup"><span data-stu-id="c6f36-363">3</span></span>|  
|<span data-ttu-id="c6f36-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="c6f36-364">Column</span></span>|@Column|<span data-ttu-id="c6f36-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6f36-365">COLUMN_NAME</span></span>|<span data-ttu-id="c6f36-366">4</span><span class="sxs-lookup"><span data-stu-id="c6f36-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6f36-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f36-367">See Also</span></span>  
 [<span data-ttu-id="c6f36-368">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c6f36-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
