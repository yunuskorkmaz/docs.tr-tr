---
title: Şema kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079714"
---
# <a name="schema-restrictions"></a><span data-ttu-id="49745-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="49745-102">Schema Restrictions</span></span>
<span data-ttu-id="49745-103">İsteğe bağlı ikinci parametresi **GetSchema** yöntemdir şema bilgileri miktarını sınırlamak için kullanılan kısıtlamaları döndürdü ve geçer **GetSchema** dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="49745-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="49745-104">Bu kısıtlama sayıya eşdeğerdir ve geçirebileceğiniz değerleri dizisinde konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="49745-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="49745-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="49745-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="49745-106">SQL Server şema koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="49745-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="49745-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-107">Restriction Name</span></span>|<span data-ttu-id="49745-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-108">Parameter Name</span></span>|<span data-ttu-id="49745-109">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-109">Restriction Default</span></span>|<span data-ttu-id="49745-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-111">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-111">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-112">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-113">1.</span><span class="sxs-lookup"><span data-stu-id="49745-113">1</span></span>|  
|<span data-ttu-id="49745-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-114">Owner</span></span>|@Owner|<span data-ttu-id="49745-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-116">2</span><span class="sxs-lookup"><span data-stu-id="49745-116">2</span></span>|  
|<span data-ttu-id="49745-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-117">Table</span></span>|@Name|<span data-ttu-id="49745-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-118">TABLE_NAME</span></span>|<span data-ttu-id="49745-119">3</span><span class="sxs-lookup"><span data-stu-id="49745-119">3</span></span>|  
|<span data-ttu-id="49745-120">TableType</span><span class="sxs-lookup"><span data-stu-id="49745-120">TableType</span></span>|@TableType|<span data-ttu-id="49745-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="49745-121">TABLE_TYPE</span></span>|<span data-ttu-id="49745-122">4</span><span class="sxs-lookup"><span data-stu-id="49745-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="49745-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="49745-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="49745-124">"Tablo" şema koleksiyonundaki kısıtlamaları birini kullanmak için yalnızca dört öğe içeren bir dizeler dizisi oluşturun, sonra bir değer kısıtlaması numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="49745-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="49745-125">Tarafından tabloları kısıtlamak için döndürülen **GetSchema** yöntemi yalnızca bu tablolara "Sales" şema öğesine iletmeden önce "Sales" için bir dizinin ikinci öğe ayarlama **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="49745-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49745-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="49745-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="49745-127">Kısıtlama varsayılan sütun var. yine de geriye dönük uyumluluğa yöneliktir, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="49745-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="49745-128">Kısıtlama değerleri belirtmek için bir SQL ekleme saldırısına riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="49745-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49745-129">Dizideki öğelerin sayısını başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır. bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="49745-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="49745-130">Olabilir en yüksek kısıtlama sayısı daha az.</span><span class="sxs-lookup"><span data-stu-id="49745-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="49745-131">Eksik kısıtlamaları (sınırsız) null olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="49745-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="49745-132">Desteklenen kısıtlama listesine çağırarak belirlemek için bir .NET Framework yönetilen sağlayıcı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="49745-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="49745-133">Bu döndürür bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="49745-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="49745-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="49745-134">Example</span></span>  
 <span data-ttu-id="49745-135">Aşağıdaki örnek nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> tüm bulunan tabloların şema bilgilerini almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için döndürülen yalnızca şema "Satış" tablolar için:</span><span class="sxs-lookup"><span data-stu-id="49745-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="49745-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="49745-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="49745-137">SQL Server şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="49745-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="49745-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="49745-138">Users</span></span>  
  
|<span data-ttu-id="49745-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-139">Restriction Name</span></span>|<span data-ttu-id="49745-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-140">Parameter Name</span></span>|<span data-ttu-id="49745-141">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-141">Restriction Default</span></span>|<span data-ttu-id="49745-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-143">User_name</span><span class="sxs-lookup"><span data-stu-id="49745-143">User_Name</span></span>|@Name|<span data-ttu-id="49745-144">name</span><span class="sxs-lookup"><span data-stu-id="49745-144">name</span></span>|<span data-ttu-id="49745-145">1.</span><span class="sxs-lookup"><span data-stu-id="49745-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="49745-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="49745-146">Databases</span></span>  
  
|<span data-ttu-id="49745-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-147">Restriction Name</span></span>|<span data-ttu-id="49745-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-148">Parameter Name</span></span>|<span data-ttu-id="49745-149">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-149">Restriction Default</span></span>|<span data-ttu-id="49745-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-151">Ad</span><span class="sxs-lookup"><span data-stu-id="49745-151">Name</span></span>|@Name|<span data-ttu-id="49745-152">Ad</span><span class="sxs-lookup"><span data-stu-id="49745-152">Name</span></span>|<span data-ttu-id="49745-153">1.</span><span class="sxs-lookup"><span data-stu-id="49745-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="49745-154">Tabloları</span><span class="sxs-lookup"><span data-stu-id="49745-154">Tables</span></span>  
  
|<span data-ttu-id="49745-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-155">Restriction Name</span></span>|<span data-ttu-id="49745-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-156">Parameter Name</span></span>|<span data-ttu-id="49745-157">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-157">Restriction Default</span></span>|<span data-ttu-id="49745-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-159">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-159">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-160">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-161">1.</span><span class="sxs-lookup"><span data-stu-id="49745-161">1</span></span>|  
|<span data-ttu-id="49745-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-162">Owner</span></span>|@Owner|<span data-ttu-id="49745-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-164">2</span><span class="sxs-lookup"><span data-stu-id="49745-164">2</span></span>|  
|<span data-ttu-id="49745-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-165">Table</span></span>|@Name|<span data-ttu-id="49745-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-166">TABLE_NAME</span></span>|<span data-ttu-id="49745-167">3</span><span class="sxs-lookup"><span data-stu-id="49745-167">3</span></span>|  
|<span data-ttu-id="49745-168">TableType</span><span class="sxs-lookup"><span data-stu-id="49745-168">TableType</span></span>|@TableType|<span data-ttu-id="49745-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="49745-169">TABLE_TYPE</span></span>|<span data-ttu-id="49745-170">4</span><span class="sxs-lookup"><span data-stu-id="49745-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="49745-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="49745-171">Columns</span></span>  
  
|<span data-ttu-id="49745-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-172">Restriction Name</span></span>|<span data-ttu-id="49745-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-173">Parameter Name</span></span>|<span data-ttu-id="49745-174">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-174">Restriction Default</span></span>|<span data-ttu-id="49745-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-176">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-176">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-177">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-178">1.</span><span class="sxs-lookup"><span data-stu-id="49745-178">1</span></span>|  
|<span data-ttu-id="49745-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-179">Owner</span></span>|@Owner|<span data-ttu-id="49745-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-181">2</span><span class="sxs-lookup"><span data-stu-id="49745-181">2</span></span>|  
|<span data-ttu-id="49745-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-182">Table</span></span>|@Table|<span data-ttu-id="49745-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-183">TABLE_NAME</span></span>|<span data-ttu-id="49745-184">3</span><span class="sxs-lookup"><span data-stu-id="49745-184">3</span></span>|  
|<span data-ttu-id="49745-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="49745-185">Column</span></span>|@Column|<span data-ttu-id="49745-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-186">COLUMN_NAME</span></span>|<span data-ttu-id="49745-187">4</span><span class="sxs-lookup"><span data-stu-id="49745-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="49745-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="49745-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="49745-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-189">Restriction Name</span></span>|<span data-ttu-id="49745-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-190">Parameter Name</span></span>|<span data-ttu-id="49745-191">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-191">Restriction Default</span></span>|<span data-ttu-id="49745-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-193">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-193">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-194">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-195">1.</span><span class="sxs-lookup"><span data-stu-id="49745-195">1</span></span>|  
|<span data-ttu-id="49745-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-196">Owner</span></span>|@Owner|<span data-ttu-id="49745-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-198">2</span><span class="sxs-lookup"><span data-stu-id="49745-198">2</span></span>|  
|<span data-ttu-id="49745-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-199">Table</span></span>|@Table|<span data-ttu-id="49745-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-200">TABLE_NAME</span></span>|<span data-ttu-id="49745-201">3</span><span class="sxs-lookup"><span data-stu-id="49745-201">3</span></span>|  
|<span data-ttu-id="49745-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="49745-202">Column</span></span>|@Column|<span data-ttu-id="49745-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-203">COLUMN_NAME</span></span>|<span data-ttu-id="49745-204">4</span><span class="sxs-lookup"><span data-stu-id="49745-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="49745-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="49745-205">Views</span></span>  
  
|<span data-ttu-id="49745-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-206">Restriction Name</span></span>|<span data-ttu-id="49745-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-207">Parameter Name</span></span>|<span data-ttu-id="49745-208">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-208">Restriction Default</span></span>|<span data-ttu-id="49745-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-210">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-210">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-211">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-212">1.</span><span class="sxs-lookup"><span data-stu-id="49745-212">1</span></span>|  
|<span data-ttu-id="49745-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-213">Owner</span></span>|@Owner|<span data-ttu-id="49745-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-215">2</span><span class="sxs-lookup"><span data-stu-id="49745-215">2</span></span>|  
|<span data-ttu-id="49745-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-216">Table</span></span>|@Table|<span data-ttu-id="49745-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-217">TABLE_NAME</span></span>|<span data-ttu-id="49745-218">3</span><span class="sxs-lookup"><span data-stu-id="49745-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="49745-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="49745-219">ViewColumns</span></span>  
  
|<span data-ttu-id="49745-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-220">Restriction Name</span></span>|<span data-ttu-id="49745-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-221">Parameter Name</span></span>|<span data-ttu-id="49745-222">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-222">Restriction Default</span></span>|<span data-ttu-id="49745-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-224">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-224">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-225">VIEW_CATALOG</span></span>|<span data-ttu-id="49745-226">1.</span><span class="sxs-lookup"><span data-stu-id="49745-226">1</span></span>|  
|<span data-ttu-id="49745-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-227">Owner</span></span>|@Owner|<span data-ttu-id="49745-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="49745-229">2</span><span class="sxs-lookup"><span data-stu-id="49745-229">2</span></span>|  
|<span data-ttu-id="49745-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-230">Table</span></span>|@Table|<span data-ttu-id="49745-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-231">VIEW_NAME</span></span>|<span data-ttu-id="49745-232">3</span><span class="sxs-lookup"><span data-stu-id="49745-232">3</span></span>|  
|<span data-ttu-id="49745-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="49745-233">Column</span></span>|@Column|<span data-ttu-id="49745-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-234">COLUMN_NAME</span></span>|<span data-ttu-id="49745-235">4</span><span class="sxs-lookup"><span data-stu-id="49745-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="49745-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="49745-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="49745-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-237">Restriction Name</span></span>|<span data-ttu-id="49745-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-238">Parameter Name</span></span>|<span data-ttu-id="49745-239">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-239">Restriction Default</span></span>|<span data-ttu-id="49745-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-241">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-241">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="49745-243">1.</span><span class="sxs-lookup"><span data-stu-id="49745-243">1</span></span>|  
|<span data-ttu-id="49745-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-244">Owner</span></span>|@Owner|<span data-ttu-id="49745-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="49745-246">2</span><span class="sxs-lookup"><span data-stu-id="49745-246">2</span></span>|  
|<span data-ttu-id="49745-247">Ad</span><span class="sxs-lookup"><span data-stu-id="49745-247">Name</span></span>|@Name|<span data-ttu-id="49745-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="49745-249">3</span><span class="sxs-lookup"><span data-stu-id="49745-249">3</span></span>|  
|<span data-ttu-id="49745-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="49745-250">Parameter</span></span>|@Parameter|<span data-ttu-id="49745-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-251">PARAMETER_NAME</span></span>|<span data-ttu-id="49745-252">4</span><span class="sxs-lookup"><span data-stu-id="49745-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="49745-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="49745-253">Procedures</span></span>  
  
|<span data-ttu-id="49745-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-254">Restriction Name</span></span>|<span data-ttu-id="49745-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-255">Parameter Name</span></span>|<span data-ttu-id="49745-256">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-256">Restriction Default</span></span>|<span data-ttu-id="49745-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-258">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-258">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="49745-260">1.</span><span class="sxs-lookup"><span data-stu-id="49745-260">1</span></span>|  
|<span data-ttu-id="49745-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-261">Owner</span></span>|@Owner|<span data-ttu-id="49745-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="49745-263">2</span><span class="sxs-lookup"><span data-stu-id="49745-263">2</span></span>|  
|<span data-ttu-id="49745-264">Ad</span><span class="sxs-lookup"><span data-stu-id="49745-264">Name</span></span>|@Name|<span data-ttu-id="49745-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="49745-266">3</span><span class="sxs-lookup"><span data-stu-id="49745-266">3</span></span>|  
|<span data-ttu-id="49745-267">Tür</span><span class="sxs-lookup"><span data-stu-id="49745-267">Type</span></span>|@Type|<span data-ttu-id="49745-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="49745-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="49745-269">4</span><span class="sxs-lookup"><span data-stu-id="49745-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="49745-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="49745-270">IndexColumns</span></span>  
  
|<span data-ttu-id="49745-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-271">Restriction Name</span></span>|<span data-ttu-id="49745-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-272">Parameter Name</span></span>|<span data-ttu-id="49745-273">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-273">Restriction Default</span></span>|<span data-ttu-id="49745-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-275">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-275">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="49745-276">db_name()</span></span>|<span data-ttu-id="49745-277">1.</span><span class="sxs-lookup"><span data-stu-id="49745-277">1</span></span>|  
|<span data-ttu-id="49745-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-278">Owner</span></span>|@Owner|<span data-ttu-id="49745-279">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="49745-279">user_name()</span></span>|<span data-ttu-id="49745-280">2</span><span class="sxs-lookup"><span data-stu-id="49745-280">2</span></span>|  
|<span data-ttu-id="49745-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-281">Table</span></span>|@Table|<span data-ttu-id="49745-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="49745-282">o.name</span></span>|<span data-ttu-id="49745-283">3</span><span class="sxs-lookup"><span data-stu-id="49745-283">3</span></span>|  
|<span data-ttu-id="49745-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="49745-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="49745-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="49745-285">x.name</span></span>|<span data-ttu-id="49745-286">4</span><span class="sxs-lookup"><span data-stu-id="49745-286">4</span></span>|  
|<span data-ttu-id="49745-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="49745-287">Column</span></span>|@Column|<span data-ttu-id="49745-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="49745-288">c.name</span></span>|<span data-ttu-id="49745-289">5</span><span class="sxs-lookup"><span data-stu-id="49745-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="49745-290">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="49745-290">Indexes</span></span>  
  
|<span data-ttu-id="49745-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-291">Restriction Name</span></span>|<span data-ttu-id="49745-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-292">Parameter Name</span></span>|<span data-ttu-id="49745-293">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-293">Restriction Default</span></span>|<span data-ttu-id="49745-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-295">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-295">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="49745-296">db_name()</span></span>|<span data-ttu-id="49745-297">1.</span><span class="sxs-lookup"><span data-stu-id="49745-297">1</span></span>|  
|<span data-ttu-id="49745-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-298">Owner</span></span>|@Owner|<span data-ttu-id="49745-299">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="49745-299">user_name()</span></span>|<span data-ttu-id="49745-300">2</span><span class="sxs-lookup"><span data-stu-id="49745-300">2</span></span>|  
|<span data-ttu-id="49745-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-301">Table</span></span>|@Table|<span data-ttu-id="49745-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="49745-302">o.name</span></span>|<span data-ttu-id="49745-303">3</span><span class="sxs-lookup"><span data-stu-id="49745-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="49745-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="49745-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="49745-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-305">Restriction Name</span></span>|<span data-ttu-id="49745-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-306">Parameter Name</span></span>|<span data-ttu-id="49745-307">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-307">Restriction Default</span></span>|<span data-ttu-id="49745-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="49745-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="49745-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="49745-310">assemblies.name</span></span>|<span data-ttu-id="49745-311">1.</span><span class="sxs-lookup"><span data-stu-id="49745-311">1</span></span>|  
|<span data-ttu-id="49745-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="49745-312">udt_name</span></span>|@UDTName|<span data-ttu-id="49745-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="49745-313">types.assembly_class</span></span>|<span data-ttu-id="49745-314">2</span><span class="sxs-lookup"><span data-stu-id="49745-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="49745-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="49745-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="49745-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-316">Restriction Name</span></span>|<span data-ttu-id="49745-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-317">Parameter Name</span></span>|<span data-ttu-id="49745-318">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-318">Restriction Default</span></span>|<span data-ttu-id="49745-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-320">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-320">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="49745-322">1.</span><span class="sxs-lookup"><span data-stu-id="49745-322">1</span></span>|  
|<span data-ttu-id="49745-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-323">Owner</span></span>|@Owner|<span data-ttu-id="49745-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="49745-325">2</span><span class="sxs-lookup"><span data-stu-id="49745-325">2</span></span>|  
|<span data-ttu-id="49745-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-326">Table</span></span>|@Table|<span data-ttu-id="49745-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-327">TABLE_NAME</span></span>|<span data-ttu-id="49745-328">3</span><span class="sxs-lookup"><span data-stu-id="49745-328">3</span></span>|  
|<span data-ttu-id="49745-329">Ad</span><span class="sxs-lookup"><span data-stu-id="49745-329">Name</span></span>|@Name|<span data-ttu-id="49745-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="49745-331">4</span><span class="sxs-lookup"><span data-stu-id="49745-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="49745-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="49745-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="49745-333">SQL Server 2008 şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="49745-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="49745-334">Bu kısıtlamalar, SQL Server 2008 ve .NET Framework 3.5 SP1 sürümle geçerli başlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="49745-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="49745-335">.NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="49745-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="49745-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="49745-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="49745-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-337">Restriction Name</span></span>|<span data-ttu-id="49745-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-338">Parameter Name</span></span>|<span data-ttu-id="49745-339">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-339">Restriction Default</span></span>|<span data-ttu-id="49745-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-341">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-341">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-342">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-343">1.</span><span class="sxs-lookup"><span data-stu-id="49745-343">1</span></span>|  
|<span data-ttu-id="49745-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-344">Owner</span></span>|@Owner|<span data-ttu-id="49745-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-346">2</span><span class="sxs-lookup"><span data-stu-id="49745-346">2</span></span>|  
|<span data-ttu-id="49745-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-347">Table</span></span>|@Table|<span data-ttu-id="49745-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-348">TABLE_NAME</span></span>|<span data-ttu-id="49745-349">3</span><span class="sxs-lookup"><span data-stu-id="49745-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="49745-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="49745-350">AllColumns</span></span>  
  
|<span data-ttu-id="49745-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="49745-351">Restriction Name</span></span>|<span data-ttu-id="49745-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="49745-352">Parameter Name</span></span>|<span data-ttu-id="49745-353">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="49745-353">Restriction Default</span></span>|<span data-ttu-id="49745-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="49745-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="49745-355">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="49745-355">Catalog</span></span>|@Catalog|<span data-ttu-id="49745-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="49745-356">TABLE_CATALOG</span></span>|<span data-ttu-id="49745-357">1.</span><span class="sxs-lookup"><span data-stu-id="49745-357">1</span></span>|  
|<span data-ttu-id="49745-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="49745-358">Owner</span></span>|@Owner|<span data-ttu-id="49745-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="49745-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="49745-360">2</span><span class="sxs-lookup"><span data-stu-id="49745-360">2</span></span>|  
|<span data-ttu-id="49745-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="49745-361">Table</span></span>|@Table|<span data-ttu-id="49745-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-362">TABLE_NAME</span></span>|<span data-ttu-id="49745-363">3</span><span class="sxs-lookup"><span data-stu-id="49745-363">3</span></span>|  
|<span data-ttu-id="49745-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="49745-364">Column</span></span>|@Column|<span data-ttu-id="49745-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="49745-365">COLUMN_NAME</span></span>|<span data-ttu-id="49745-366">4</span><span class="sxs-lookup"><span data-stu-id="49745-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49745-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49745-367">See Also</span></span>  
 [<span data-ttu-id="49745-368">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="49745-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
