---
title: Şema kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198614"
---
# <a name="schema-restrictions"></a><span data-ttu-id="8fb85-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="8fb85-102">Schema Restrictions</span></span>
<span data-ttu-id="8fb85-103">İsteğe bağlı ikinci parametresi **GetSchema** yöntemdir şema bilgileri miktarını sınırlamak için kullanılan kısıtlamaları döndürdü ve geçer **GetSchema** dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="8fb85-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="8fb85-104">Bu kısıtlama sayıya eşdeğerdir ve geçirebileceğiniz değerleri dizisinde konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="8fb85-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="8fb85-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fb85-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="8fb85-106">SQL Server şema koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="8fb85-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-107">Restriction Name</span></span>|<span data-ttu-id="8fb85-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-108">Parameter Name</span></span>|<span data-ttu-id="8fb85-109">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-109">Restriction Default</span></span>|<span data-ttu-id="8fb85-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-111">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-111">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-112">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-113">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-113">1</span></span>|  
|<span data-ttu-id="8fb85-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-114">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-116">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-116">2</span></span>|  
|<span data-ttu-id="8fb85-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-117">Table</span></span>|@Name|<span data-ttu-id="8fb85-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-118">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-119">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-119">3</span></span>|  
|<span data-ttu-id="8fb85-120">TableType</span><span class="sxs-lookup"><span data-stu-id="8fb85-120">TableType</span></span>|@TableType|<span data-ttu-id="8fb85-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fb85-121">TABLE_TYPE</span></span>|<span data-ttu-id="8fb85-122">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="8fb85-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="8fb85-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="8fb85-124">"Tablo" şema koleksiyonundaki kısıtlamaları birini kullanmak için yalnızca dört öğe içeren bir dizeler dizisi oluşturun, sonra bir değer kısıtlaması numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8fb85-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="8fb85-125">Tarafından tabloları kısıtlamak için döndürülen **GetSchema** yöntemi yalnızca bu tablolara "Sales" şema öğesine iletmeden önce "Sales" için bir dizinin ikinci öğe ayarlama **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fb85-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fb85-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="8fb85-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="8fb85-127">Kısıtlama varsayılan sütun var. yine de geriye dönük uyumluluğa yöneliktir, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="8fb85-128">Kısıtlama değerleri belirtmek için bir SQL ekleme saldırısına riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fb85-129">Dizideki öğelerin sayısını başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır. bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8fb85-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="8fb85-130">Olabilir en yüksek kısıtlama sayısı daha az.</span><span class="sxs-lookup"><span data-stu-id="8fb85-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="8fb85-131">Eksik kısıtlamaları (sınırsız) null olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="8fb85-132">Desteklenen kısıtlama listesine çağırarak belirlemek için bir .NET Framework yönetilen sağlayıcı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="8fb85-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="8fb85-133">Bu döndürür bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="8fb85-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8fb85-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fb85-134">Example</span></span>  
 <span data-ttu-id="8fb85-135">Aşağıdaki örnek nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> tüm bulunan tabloların şema bilgilerini almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için döndürülen yalnızca şema "Satış" tablolar için:</span><span class="sxs-lookup"><span data-stu-id="8fb85-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="8fb85-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="8fb85-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="8fb85-137">SQL Server şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="8fb85-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="8fb85-138">Users</span></span>  
  
|<span data-ttu-id="8fb85-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-139">Restriction Name</span></span>|<span data-ttu-id="8fb85-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-140">Parameter Name</span></span>|<span data-ttu-id="8fb85-141">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-141">Restriction Default</span></span>|<span data-ttu-id="8fb85-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-143">User_name</span><span class="sxs-lookup"><span data-stu-id="8fb85-143">User_Name</span></span>|@Name|<span data-ttu-id="8fb85-144">name</span><span class="sxs-lookup"><span data-stu-id="8fb85-144">name</span></span>|<span data-ttu-id="8fb85-145">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="8fb85-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="8fb85-146">Databases</span></span>  
  
|<span data-ttu-id="8fb85-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-147">Restriction Name</span></span>|<span data-ttu-id="8fb85-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-148">Parameter Name</span></span>|<span data-ttu-id="8fb85-149">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-149">Restriction Default</span></span>|<span data-ttu-id="8fb85-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-151">Ad</span><span class="sxs-lookup"><span data-stu-id="8fb85-151">Name</span></span>|@Name|<span data-ttu-id="8fb85-152">Ad</span><span class="sxs-lookup"><span data-stu-id="8fb85-152">Name</span></span>|<span data-ttu-id="8fb85-153">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="8fb85-154">Tabloları</span><span class="sxs-lookup"><span data-stu-id="8fb85-154">Tables</span></span>  
  
|<span data-ttu-id="8fb85-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-155">Restriction Name</span></span>|<span data-ttu-id="8fb85-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-156">Parameter Name</span></span>|<span data-ttu-id="8fb85-157">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-157">Restriction Default</span></span>|<span data-ttu-id="8fb85-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-159">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-159">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-160">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-161">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-161">1</span></span>|  
|<span data-ttu-id="8fb85-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-162">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-164">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-164">2</span></span>|  
|<span data-ttu-id="8fb85-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-165">Table</span></span>|@Name|<span data-ttu-id="8fb85-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-166">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-167">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-167">3</span></span>|  
|<span data-ttu-id="8fb85-168">TableType</span><span class="sxs-lookup"><span data-stu-id="8fb85-168">TableType</span></span>|@TableType|<span data-ttu-id="8fb85-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fb85-169">TABLE_TYPE</span></span>|<span data-ttu-id="8fb85-170">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8fb85-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="8fb85-171">Columns</span></span>  
  
|<span data-ttu-id="8fb85-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-172">Restriction Name</span></span>|<span data-ttu-id="8fb85-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-173">Parameter Name</span></span>|<span data-ttu-id="8fb85-174">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-174">Restriction Default</span></span>|<span data-ttu-id="8fb85-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-176">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-176">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-177">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-178">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-178">1</span></span>|  
|<span data-ttu-id="8fb85-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-179">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-181">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-181">2</span></span>|  
|<span data-ttu-id="8fb85-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-182">Table</span></span>|@Table|<span data-ttu-id="8fb85-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-183">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-184">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-184">3</span></span>|  
|<span data-ttu-id="8fb85-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="8fb85-185">Column</span></span>|@Column|<span data-ttu-id="8fb85-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-186">COLUMN_NAME</span></span>|<span data-ttu-id="8fb85-187">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="8fb85-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="8fb85-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="8fb85-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-189">Restriction Name</span></span>|<span data-ttu-id="8fb85-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-190">Parameter Name</span></span>|<span data-ttu-id="8fb85-191">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-191">Restriction Default</span></span>|<span data-ttu-id="8fb85-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-193">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-193">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-194">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-195">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-195">1</span></span>|  
|<span data-ttu-id="8fb85-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-196">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-198">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-198">2</span></span>|  
|<span data-ttu-id="8fb85-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-199">Table</span></span>|@Table|<span data-ttu-id="8fb85-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-200">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-201">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-201">3</span></span>|  
|<span data-ttu-id="8fb85-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="8fb85-202">Column</span></span>|@Column|<span data-ttu-id="8fb85-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-203">COLUMN_NAME</span></span>|<span data-ttu-id="8fb85-204">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8fb85-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="8fb85-205">Views</span></span>  
  
|<span data-ttu-id="8fb85-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-206">Restriction Name</span></span>|<span data-ttu-id="8fb85-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-207">Parameter Name</span></span>|<span data-ttu-id="8fb85-208">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-208">Restriction Default</span></span>|<span data-ttu-id="8fb85-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-210">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-210">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-211">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-212">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-212">1</span></span>|  
|<span data-ttu-id="8fb85-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-213">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-215">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-215">2</span></span>|  
|<span data-ttu-id="8fb85-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-216">Table</span></span>|@Table|<span data-ttu-id="8fb85-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-217">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-218">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="8fb85-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="8fb85-219">ViewColumns</span></span>  
  
|<span data-ttu-id="8fb85-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-220">Restriction Name</span></span>|<span data-ttu-id="8fb85-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-221">Parameter Name</span></span>|<span data-ttu-id="8fb85-222">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-222">Restriction Default</span></span>|<span data-ttu-id="8fb85-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-224">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-224">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-225">VIEW_CATALOG</span></span>|<span data-ttu-id="8fb85-226">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-226">1</span></span>|  
|<span data-ttu-id="8fb85-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-227">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="8fb85-229">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-229">2</span></span>|  
|<span data-ttu-id="8fb85-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-230">Table</span></span>|@Table|<span data-ttu-id="8fb85-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-231">VIEW_NAME</span></span>|<span data-ttu-id="8fb85-232">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-232">3</span></span>|  
|<span data-ttu-id="8fb85-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="8fb85-233">Column</span></span>|@Column|<span data-ttu-id="8fb85-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-234">COLUMN_NAME</span></span>|<span data-ttu-id="8fb85-235">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="8fb85-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8fb85-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="8fb85-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-237">Restriction Name</span></span>|<span data-ttu-id="8fb85-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-238">Parameter Name</span></span>|<span data-ttu-id="8fb85-239">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-239">Restriction Default</span></span>|<span data-ttu-id="8fb85-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-241">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-241">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="8fb85-243">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-243">1</span></span>|  
|<span data-ttu-id="8fb85-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-244">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="8fb85-246">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-246">2</span></span>|  
|<span data-ttu-id="8fb85-247">Ad</span><span class="sxs-lookup"><span data-stu-id="8fb85-247">Name</span></span>|@Name|<span data-ttu-id="8fb85-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="8fb85-249">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-249">3</span></span>|  
|<span data-ttu-id="8fb85-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="8fb85-250">Parameter</span></span>|@Parameter|<span data-ttu-id="8fb85-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-251">PARAMETER_NAME</span></span>|<span data-ttu-id="8fb85-252">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8fb85-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8fb85-253">Procedures</span></span>  
  
|<span data-ttu-id="8fb85-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-254">Restriction Name</span></span>|<span data-ttu-id="8fb85-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-255">Parameter Name</span></span>|<span data-ttu-id="8fb85-256">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-256">Restriction Default</span></span>|<span data-ttu-id="8fb85-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-258">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-258">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="8fb85-260">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-260">1</span></span>|  
|<span data-ttu-id="8fb85-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-261">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="8fb85-263">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-263">2</span></span>|  
|<span data-ttu-id="8fb85-264">Ad</span><span class="sxs-lookup"><span data-stu-id="8fb85-264">Name</span></span>|@Name|<span data-ttu-id="8fb85-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="8fb85-266">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-266">3</span></span>|  
|<span data-ttu-id="8fb85-267">Tür</span><span class="sxs-lookup"><span data-stu-id="8fb85-267">Type</span></span>|@Type|<span data-ttu-id="8fb85-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8fb85-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="8fb85-269">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="8fb85-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="8fb85-270">IndexColumns</span></span>  
  
|<span data-ttu-id="8fb85-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-271">Restriction Name</span></span>|<span data-ttu-id="8fb85-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-272">Parameter Name</span></span>|<span data-ttu-id="8fb85-273">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-273">Restriction Default</span></span>|<span data-ttu-id="8fb85-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-275">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-275">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="8fb85-276">db_name()</span></span>|<span data-ttu-id="8fb85-277">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-277">1</span></span>|  
|<span data-ttu-id="8fb85-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-278">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-279">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="8fb85-279">user_name()</span></span>|<span data-ttu-id="8fb85-280">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-280">2</span></span>|  
|<span data-ttu-id="8fb85-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-281">Table</span></span>|@Table|<span data-ttu-id="8fb85-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="8fb85-282">o.name</span></span>|<span data-ttu-id="8fb85-283">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-283">3</span></span>|  
|<span data-ttu-id="8fb85-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="8fb85-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="8fb85-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="8fb85-285">x.name</span></span>|<span data-ttu-id="8fb85-286">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-286">4</span></span>|  
|<span data-ttu-id="8fb85-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="8fb85-287">Column</span></span>|@Column|<span data-ttu-id="8fb85-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="8fb85-288">c.name</span></span>|<span data-ttu-id="8fb85-289">5</span><span class="sxs-lookup"><span data-stu-id="8fb85-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8fb85-290">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="8fb85-290">Indexes</span></span>  
  
|<span data-ttu-id="8fb85-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-291">Restriction Name</span></span>|<span data-ttu-id="8fb85-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-292">Parameter Name</span></span>|<span data-ttu-id="8fb85-293">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-293">Restriction Default</span></span>|<span data-ttu-id="8fb85-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-295">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-295">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="8fb85-296">db_name()</span></span>|<span data-ttu-id="8fb85-297">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-297">1</span></span>|  
|<span data-ttu-id="8fb85-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-298">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-299">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="8fb85-299">user_name()</span></span>|<span data-ttu-id="8fb85-300">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-300">2</span></span>|  
|<span data-ttu-id="8fb85-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-301">Table</span></span>|@Table|<span data-ttu-id="8fb85-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="8fb85-302">o.name</span></span>|<span data-ttu-id="8fb85-303">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="8fb85-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="8fb85-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="8fb85-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-305">Restriction Name</span></span>|<span data-ttu-id="8fb85-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-306">Parameter Name</span></span>|<span data-ttu-id="8fb85-307">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-307">Restriction Default</span></span>|<span data-ttu-id="8fb85-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="8fb85-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="8fb85-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="8fb85-310">assemblies.name</span></span>|<span data-ttu-id="8fb85-311">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-311">1</span></span>|  
|<span data-ttu-id="8fb85-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="8fb85-312">udt_name</span></span>|@UDTName|<span data-ttu-id="8fb85-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="8fb85-313">types.assembly_class</span></span>|<span data-ttu-id="8fb85-314">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="8fb85-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="8fb85-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="8fb85-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-316">Restriction Name</span></span>|<span data-ttu-id="8fb85-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-317">Parameter Name</span></span>|<span data-ttu-id="8fb85-318">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-318">Restriction Default</span></span>|<span data-ttu-id="8fb85-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-320">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-320">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="8fb85-322">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-322">1</span></span>|  
|<span data-ttu-id="8fb85-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-323">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="8fb85-325">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-325">2</span></span>|  
|<span data-ttu-id="8fb85-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-326">Table</span></span>|@Table|<span data-ttu-id="8fb85-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-327">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-328">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-328">3</span></span>|  
|<span data-ttu-id="8fb85-329">Ad</span><span class="sxs-lookup"><span data-stu-id="8fb85-329">Name</span></span>|@Name|<span data-ttu-id="8fb85-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="8fb85-331">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="8fb85-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="8fb85-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="8fb85-333">SQL Server 2008 şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8fb85-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="8fb85-334">Bu kısıtlamalar, SQL Server 2008 ve .NET Framework 3.5 SP1 sürümle geçerli başlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="8fb85-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="8fb85-335">.NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8fb85-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="8fb85-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="8fb85-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="8fb85-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-337">Restriction Name</span></span>|<span data-ttu-id="8fb85-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-338">Parameter Name</span></span>|<span data-ttu-id="8fb85-339">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-339">Restriction Default</span></span>|<span data-ttu-id="8fb85-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-341">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-341">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-342">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-343">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-343">1</span></span>|  
|<span data-ttu-id="8fb85-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-344">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-346">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-346">2</span></span>|  
|<span data-ttu-id="8fb85-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-347">Table</span></span>|@Table|<span data-ttu-id="8fb85-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-348">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-349">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="8fb85-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="8fb85-350">AllColumns</span></span>  
  
|<span data-ttu-id="8fb85-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-351">Restriction Name</span></span>|<span data-ttu-id="8fb85-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="8fb85-352">Parameter Name</span></span>|<span data-ttu-id="8fb85-353">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="8fb85-353">Restriction Default</span></span>|<span data-ttu-id="8fb85-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="8fb85-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="8fb85-355">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="8fb85-355">Catalog</span></span>|@Catalog|<span data-ttu-id="8fb85-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8fb85-356">TABLE_CATALOG</span></span>|<span data-ttu-id="8fb85-357">1.</span><span class="sxs-lookup"><span data-stu-id="8fb85-357">1</span></span>|  
|<span data-ttu-id="8fb85-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="8fb85-358">Owner</span></span>|@Owner|<span data-ttu-id="8fb85-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8fb85-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="8fb85-360">2</span><span class="sxs-lookup"><span data-stu-id="8fb85-360">2</span></span>|  
|<span data-ttu-id="8fb85-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="8fb85-361">Table</span></span>|@Table|<span data-ttu-id="8fb85-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-362">TABLE_NAME</span></span>|<span data-ttu-id="8fb85-363">3</span><span class="sxs-lookup"><span data-stu-id="8fb85-363">3</span></span>|  
|<span data-ttu-id="8fb85-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="8fb85-364">Column</span></span>|@Column|<span data-ttu-id="8fb85-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8fb85-365">COLUMN_NAME</span></span>|<span data-ttu-id="8fb85-366">4</span><span class="sxs-lookup"><span data-stu-id="8fb85-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fb85-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb85-367">See Also</span></span>  
 [<span data-ttu-id="8fb85-368">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8fb85-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
