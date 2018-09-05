---
title: Şema kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563435"
---
# <a name="schema-restrictions"></a><span data-ttu-id="d0eb3-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="d0eb3-102">Schema Restrictions</span></span>
<span data-ttu-id="d0eb3-103">İsteğe bağlı ikinci parametresi **GetSchema** yöntemdir şema bilgileri miktarını sınırlamak için kullanılan kısıtlamaları döndürdü ve geçer **GetSchema** dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="d0eb3-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="d0eb3-104">Bu kısıtlama sayıya eşdeğerdir ve geçirebileceğiniz değerleri dizisinde konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="d0eb3-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="d0eb3-106">SQL Server şema koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="d0eb3-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-107">Restriction Name</span></span>|<span data-ttu-id="d0eb3-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-108">Parameter Name</span></span>|<span data-ttu-id="d0eb3-109">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-109">Restriction Default</span></span>|<span data-ttu-id="d0eb3-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-111">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-111">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-112">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-113">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-113">1</span></span>|  
|<span data-ttu-id="d0eb3-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-114">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-116">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-116">2</span></span>|  
|<span data-ttu-id="d0eb3-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-117">Table</span></span>|@Name|<span data-ttu-id="d0eb3-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-118">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-119">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-119">3</span></span>|  
|<span data-ttu-id="d0eb3-120">TableType</span><span class="sxs-lookup"><span data-stu-id="d0eb3-120">TableType</span></span>|@TableType|<span data-ttu-id="d0eb3-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d0eb3-121">TABLE_TYPE</span></span>|<span data-ttu-id="d0eb3-122">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="d0eb3-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="d0eb3-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="d0eb3-124">"Tablo" şema koleksiyonundaki kısıtlamaları birini kullanmak için yalnızca dört öğe içeren bir dizeler dizisi oluşturun, sonra bir değer kısıtlaması numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="d0eb3-125">Tarafından tabloları kısıtlamak için döndürülen **GetSchema** yöntemi yalnızca bu tablolara "Sales" şema öğesine iletmeden önce "Sales" için bir dizinin ikinci öğe ayarlama **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0eb3-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="d0eb3-127">Kısıtlama varsayılan sütun var. yine de geriye dönük uyumluluğa yöneliktir, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="d0eb3-128">Kısıtlama değerleri belirtmek için bir SQL ekleme saldırısına riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0eb3-129">Dizideki öğelerin sayısını başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır. bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="d0eb3-130">Olabilir en yüksek kısıtlama sayısı daha az.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="d0eb3-131">Eksik kısıtlamaları (sınırsız) null olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="d0eb3-132">Desteklenen kısıtlama listesine çağırarak belirlemek için bir .NET Framework yönetilen sağlayıcı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="d0eb3-133">Bu döndürür bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0eb3-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0eb3-134">Example</span></span>  
 <span data-ttu-id="d0eb3-135">Aşağıdaki örnek nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> tüm bulunan tabloların şema bilgilerini almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için döndürülen yalnızca şema "Satış" tablolar için:</span><span class="sxs-lookup"><span data-stu-id="d0eb3-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="d0eb3-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="d0eb3-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="d0eb3-137">SQL Server şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="d0eb3-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="d0eb3-138">Users</span></span>  
  
|<span data-ttu-id="d0eb3-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-139">Restriction Name</span></span>|<span data-ttu-id="d0eb3-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-140">Parameter Name</span></span>|<span data-ttu-id="d0eb3-141">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-141">Restriction Default</span></span>|<span data-ttu-id="d0eb3-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-143">User_name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-143">User_Name</span></span>|@Name|<span data-ttu-id="d0eb3-144">name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-144">name</span></span>|<span data-ttu-id="d0eb3-145">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="d0eb3-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="d0eb3-146">Databases</span></span>  
  
|<span data-ttu-id="d0eb3-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-147">Restriction Name</span></span>|<span data-ttu-id="d0eb3-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-148">Parameter Name</span></span>|<span data-ttu-id="d0eb3-149">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-149">Restriction Default</span></span>|<span data-ttu-id="d0eb3-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-151">Ad</span><span class="sxs-lookup"><span data-stu-id="d0eb3-151">Name</span></span>|@Name|<span data-ttu-id="d0eb3-152">Ad</span><span class="sxs-lookup"><span data-stu-id="d0eb3-152">Name</span></span>|<span data-ttu-id="d0eb3-153">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="d0eb3-154">Tabloları</span><span class="sxs-lookup"><span data-stu-id="d0eb3-154">Tables</span></span>  
  
|<span data-ttu-id="d0eb3-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-155">Restriction Name</span></span>|<span data-ttu-id="d0eb3-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-156">Parameter Name</span></span>|<span data-ttu-id="d0eb3-157">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-157">Restriction Default</span></span>|<span data-ttu-id="d0eb3-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-159">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-159">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-160">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-161">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-161">1</span></span>|  
|<span data-ttu-id="d0eb3-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-162">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-164">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-164">2</span></span>|  
|<span data-ttu-id="d0eb3-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-165">Table</span></span>|@Name|<span data-ttu-id="d0eb3-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-166">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-167">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-167">3</span></span>|  
|<span data-ttu-id="d0eb3-168">TableType</span><span class="sxs-lookup"><span data-stu-id="d0eb3-168">TableType</span></span>|@TableType|<span data-ttu-id="d0eb3-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d0eb3-169">TABLE_TYPE</span></span>|<span data-ttu-id="d0eb3-170">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="d0eb3-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="d0eb3-171">Columns</span></span>  
  
|<span data-ttu-id="d0eb3-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-172">Restriction Name</span></span>|<span data-ttu-id="d0eb3-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-173">Parameter Name</span></span>|<span data-ttu-id="d0eb3-174">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-174">Restriction Default</span></span>|<span data-ttu-id="d0eb3-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-176">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-176">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-177">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-178">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-178">1</span></span>|  
|<span data-ttu-id="d0eb3-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-179">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-181">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-181">2</span></span>|  
|<span data-ttu-id="d0eb3-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-182">Table</span></span>|@Table|<span data-ttu-id="d0eb3-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-183">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-184">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-184">3</span></span>|  
|<span data-ttu-id="d0eb3-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="d0eb3-185">Column</span></span>|@Column|<span data-ttu-id="d0eb3-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-186">COLUMN_NAME</span></span>|<span data-ttu-id="d0eb3-187">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="d0eb3-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="d0eb3-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="d0eb3-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-189">Restriction Name</span></span>|<span data-ttu-id="d0eb3-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-190">Parameter Name</span></span>|<span data-ttu-id="d0eb3-191">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-191">Restriction Default</span></span>|<span data-ttu-id="d0eb3-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-193">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-193">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-194">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-195">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-195">1</span></span>|  
|<span data-ttu-id="d0eb3-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-196">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-198">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-198">2</span></span>|  
|<span data-ttu-id="d0eb3-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-199">Table</span></span>|@Table|<span data-ttu-id="d0eb3-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-200">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-201">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-201">3</span></span>|  
|<span data-ttu-id="d0eb3-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="d0eb3-202">Column</span></span>|@Column|<span data-ttu-id="d0eb3-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-203">COLUMN_NAME</span></span>|<span data-ttu-id="d0eb3-204">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="d0eb3-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d0eb3-205">Views</span></span>  
  
|<span data-ttu-id="d0eb3-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-206">Restriction Name</span></span>|<span data-ttu-id="d0eb3-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-207">Parameter Name</span></span>|<span data-ttu-id="d0eb3-208">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-208">Restriction Default</span></span>|<span data-ttu-id="d0eb3-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-210">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-210">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-211">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-212">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-212">1</span></span>|  
|<span data-ttu-id="d0eb3-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-213">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-215">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-215">2</span></span>|  
|<span data-ttu-id="d0eb3-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-216">Table</span></span>|@Table|<span data-ttu-id="d0eb3-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-217">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-218">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="d0eb3-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="d0eb3-219">ViewColumns</span></span>  
  
|<span data-ttu-id="d0eb3-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-220">Restriction Name</span></span>|<span data-ttu-id="d0eb3-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-221">Parameter Name</span></span>|<span data-ttu-id="d0eb3-222">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-222">Restriction Default</span></span>|<span data-ttu-id="d0eb3-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-224">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-224">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-225">VIEW_CATALOG</span></span>|<span data-ttu-id="d0eb3-226">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-226">1</span></span>|  
|<span data-ttu-id="d0eb3-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-227">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="d0eb3-229">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-229">2</span></span>|  
|<span data-ttu-id="d0eb3-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-230">Table</span></span>|@Table|<span data-ttu-id="d0eb3-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-231">VIEW_NAME</span></span>|<span data-ttu-id="d0eb3-232">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-232">3</span></span>|  
|<span data-ttu-id="d0eb3-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="d0eb3-233">Column</span></span>|@Column|<span data-ttu-id="d0eb3-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-234">COLUMN_NAME</span></span>|<span data-ttu-id="d0eb3-235">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="d0eb3-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="d0eb3-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="d0eb3-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-237">Restriction Name</span></span>|<span data-ttu-id="d0eb3-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-238">Parameter Name</span></span>|<span data-ttu-id="d0eb3-239">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-239">Restriction Default</span></span>|<span data-ttu-id="d0eb3-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-241">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-241">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="d0eb3-243">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-243">1</span></span>|  
|<span data-ttu-id="d0eb3-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-244">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="d0eb3-246">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-246">2</span></span>|  
|<span data-ttu-id="d0eb3-247">Ad</span><span class="sxs-lookup"><span data-stu-id="d0eb3-247">Name</span></span>|@Name|<span data-ttu-id="d0eb3-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="d0eb3-249">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-249">3</span></span>|  
|<span data-ttu-id="d0eb3-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="d0eb3-250">Parameter</span></span>|@Parameter|<span data-ttu-id="d0eb3-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-251">PARAMETER_NAME</span></span>|<span data-ttu-id="d0eb3-252">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="d0eb3-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d0eb3-253">Procedures</span></span>  
  
|<span data-ttu-id="d0eb3-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-254">Restriction Name</span></span>|<span data-ttu-id="d0eb3-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-255">Parameter Name</span></span>|<span data-ttu-id="d0eb3-256">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-256">Restriction Default</span></span>|<span data-ttu-id="d0eb3-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-258">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-258">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="d0eb3-260">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-260">1</span></span>|  
|<span data-ttu-id="d0eb3-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-261">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="d0eb3-263">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-263">2</span></span>|  
|<span data-ttu-id="d0eb3-264">Ad</span><span class="sxs-lookup"><span data-stu-id="d0eb3-264">Name</span></span>|@Name|<span data-ttu-id="d0eb3-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="d0eb3-266">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-266">3</span></span>|  
|<span data-ttu-id="d0eb3-267">Tür</span><span class="sxs-lookup"><span data-stu-id="d0eb3-267">Type</span></span>|@Type|<span data-ttu-id="d0eb3-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="d0eb3-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="d0eb3-269">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="d0eb3-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="d0eb3-270">IndexColumns</span></span>  
  
|<span data-ttu-id="d0eb3-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-271">Restriction Name</span></span>|<span data-ttu-id="d0eb3-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-272">Parameter Name</span></span>|<span data-ttu-id="d0eb3-273">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-273">Restriction Default</span></span>|<span data-ttu-id="d0eb3-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-275">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-275">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="d0eb3-276">db_name()</span></span>|<span data-ttu-id="d0eb3-277">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-277">1</span></span>|  
|<span data-ttu-id="d0eb3-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-278">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-279">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="d0eb3-279">user_name()</span></span>|<span data-ttu-id="d0eb3-280">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-280">2</span></span>|  
|<span data-ttu-id="d0eb3-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-281">Table</span></span>|@Table|<span data-ttu-id="d0eb3-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-282">o.name</span></span>|<span data-ttu-id="d0eb3-283">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-283">3</span></span>|  
|<span data-ttu-id="d0eb3-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="d0eb3-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="d0eb3-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-285">x.name</span></span>|<span data-ttu-id="d0eb3-286">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-286">4</span></span>|  
|<span data-ttu-id="d0eb3-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="d0eb3-287">Column</span></span>|@Column|<span data-ttu-id="d0eb3-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-288">c.name</span></span>|<span data-ttu-id="d0eb3-289">5</span><span class="sxs-lookup"><span data-stu-id="d0eb3-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="d0eb3-290">Dizinleri</span><span class="sxs-lookup"><span data-stu-id="d0eb3-290">Indexes</span></span>  
  
|<span data-ttu-id="d0eb3-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-291">Restriction Name</span></span>|<span data-ttu-id="d0eb3-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-292">Parameter Name</span></span>|<span data-ttu-id="d0eb3-293">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-293">Restriction Default</span></span>|<span data-ttu-id="d0eb3-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-295">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-295">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="d0eb3-296">db_name()</span></span>|<span data-ttu-id="d0eb3-297">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-297">1</span></span>|  
|<span data-ttu-id="d0eb3-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-298">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-299">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="d0eb3-299">user_name()</span></span>|<span data-ttu-id="d0eb3-300">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-300">2</span></span>|  
|<span data-ttu-id="d0eb3-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-301">Table</span></span>|@Table|<span data-ttu-id="d0eb3-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-302">o.name</span></span>|<span data-ttu-id="d0eb3-303">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="d0eb3-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="d0eb3-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="d0eb3-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-305">Restriction Name</span></span>|<span data-ttu-id="d0eb3-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-306">Parameter Name</span></span>|<span data-ttu-id="d0eb3-307">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-307">Restriction Default</span></span>|<span data-ttu-id="d0eb3-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="d0eb3-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-310">assemblies.name</span></span>|<span data-ttu-id="d0eb3-311">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-311">1</span></span>|  
|<span data-ttu-id="d0eb3-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="d0eb3-312">udt_name</span></span>|@UDTName|<span data-ttu-id="d0eb3-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="d0eb3-313">types.assembly_class</span></span>|<span data-ttu-id="d0eb3-314">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="d0eb3-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="d0eb3-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="d0eb3-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-316">Restriction Name</span></span>|<span data-ttu-id="d0eb3-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-317">Parameter Name</span></span>|<span data-ttu-id="d0eb3-318">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-318">Restriction Default</span></span>|<span data-ttu-id="d0eb3-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-320">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-320">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="d0eb3-322">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-322">1</span></span>|  
|<span data-ttu-id="d0eb3-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-323">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="d0eb3-325">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-325">2</span></span>|  
|<span data-ttu-id="d0eb3-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-326">Table</span></span>|@Table|<span data-ttu-id="d0eb3-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-327">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-328">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-328">3</span></span>|  
|<span data-ttu-id="d0eb3-329">Ad</span><span class="sxs-lookup"><span data-stu-id="d0eb3-329">Name</span></span>|@Name|<span data-ttu-id="d0eb3-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="d0eb3-331">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="d0eb3-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="d0eb3-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="d0eb3-333">SQL Server 2008 şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="d0eb3-334">Bu kısıtlamalar, SQL Server 2008 ve .NET Framework 3.5 SP1 sürümle geçerli başlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="d0eb3-335">.NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="d0eb3-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="d0eb3-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="d0eb3-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-337">Restriction Name</span></span>|<span data-ttu-id="d0eb3-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-338">Parameter Name</span></span>|<span data-ttu-id="d0eb3-339">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-339">Restriction Default</span></span>|<span data-ttu-id="d0eb3-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-341">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-341">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-342">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-343">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-343">1</span></span>|  
|<span data-ttu-id="d0eb3-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-344">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-346">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-346">2</span></span>|  
|<span data-ttu-id="d0eb3-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-347">Table</span></span>|@Table|<span data-ttu-id="d0eb3-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-348">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-349">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="d0eb3-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="d0eb3-350">AllColumns</span></span>  
  
|<span data-ttu-id="d0eb3-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-351">Restriction Name</span></span>|<span data-ttu-id="d0eb3-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-352">Parameter Name</span></span>|<span data-ttu-id="d0eb3-353">Varsayılan kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d0eb3-353">Restriction Default</span></span>|<span data-ttu-id="d0eb3-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="d0eb3-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="d0eb3-355">Kataloğu</span><span class="sxs-lookup"><span data-stu-id="d0eb3-355">Catalog</span></span>|@Catalog|<span data-ttu-id="d0eb3-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="d0eb3-356">TABLE_CATALOG</span></span>|<span data-ttu-id="d0eb3-357">1.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-357">1</span></span>|  
|<span data-ttu-id="d0eb3-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="d0eb3-358">Owner</span></span>|@Owner|<span data-ttu-id="d0eb3-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="d0eb3-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="d0eb3-360">2</span><span class="sxs-lookup"><span data-stu-id="d0eb3-360">2</span></span>|  
|<span data-ttu-id="d0eb3-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="d0eb3-361">Table</span></span>|@Table|<span data-ttu-id="d0eb3-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-362">TABLE_NAME</span></span>|<span data-ttu-id="d0eb3-363">3</span><span class="sxs-lookup"><span data-stu-id="d0eb3-363">3</span></span>|  
|<span data-ttu-id="d0eb3-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="d0eb3-364">Column</span></span>|@Column|<span data-ttu-id="d0eb3-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="d0eb3-365">COLUMN_NAME</span></span>|<span data-ttu-id="d0eb3-366">4</span><span class="sxs-lookup"><span data-stu-id="d0eb3-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0eb3-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0eb3-367">See Also</span></span>  
 [<span data-ttu-id="d0eb3-368">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d0eb3-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
