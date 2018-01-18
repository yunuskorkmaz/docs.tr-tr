---
title: "Şema kısıtlamaları"
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
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5b004b70716c61af8ac37fef76f660c488e5a74
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="09def-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="09def-102">Schema Restrictions</span></span>
<span data-ttu-id="09def-103">İkinci isteğe bağlı parametresi, **GetSchema** yöntemdir şema bilgi tutarını sınırlamak için kullanılan kısıtlamaları döndürülür ve için geçirilen **GetSchema** bir dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="09def-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="09def-104">Dizideki konumu geçirebilirsiniz değerleri belirler ve bu kısıtlama sayıya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="09def-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="09def-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="09def-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="09def-106">SQL Server şeması koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="09def-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="09def-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-107">Restriction Name</span></span>|<span data-ttu-id="09def-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-108">Parameter Name</span></span>|<span data-ttu-id="09def-109">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-109">Restriction Default</span></span>|<span data-ttu-id="09def-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-111">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-112">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-113">1.</span><span class="sxs-lookup"><span data-stu-id="09def-113">1</span></span>|  
|<span data-ttu-id="09def-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-114">Owner</span></span>|@Owner|<span data-ttu-id="09def-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-116">2</span><span class="sxs-lookup"><span data-stu-id="09def-116">2</span></span>|  
|<span data-ttu-id="09def-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-117">Table</span></span>|@Name|<span data-ttu-id="09def-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-118">TABLE_NAME</span></span>|<span data-ttu-id="09def-119">3</span><span class="sxs-lookup"><span data-stu-id="09def-119">3</span></span>|  
|<span data-ttu-id="09def-120">TableType</span><span class="sxs-lookup"><span data-stu-id="09def-120">TableType</span></span>|@TableType|<span data-ttu-id="09def-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="09def-121">TABLE_TYPE</span></span>|<span data-ttu-id="09def-122">4</span><span class="sxs-lookup"><span data-stu-id="09def-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="09def-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="09def-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="09def-124">"Tablo" şema koleksiyonu kısıtlamalarını birini kullanmak için yalnızca bir dizeler dizisi ile dört öğeleri oluşturun, sonra bir değer kısıtlama numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="09def-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="09def-125">Örneğin, tablolar kısıtlamak için tarafından geri döndürülen **GetSchema** geçirmeden önce "Satış" diziye ikinci öğesini set yöntemi yalnızca "Satış" şemasında tablolara **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="09def-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09def-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="09def-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="09def-127">Kısıtlama varsayılan sütunu yine için geriye dönük uyumluluk yoktur, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="09def-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="09def-128">Dize değiştirme yerine parametreli sorgular kısıtlama değerleri belirtirken SQL ekleme saldırı riskini en aza indirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="09def-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09def-129">Dizideki öğelerin sayısı başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="09def-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="09def-130">Olabilir kısıtlamaları maksimum sayısından az.</span><span class="sxs-lookup"><span data-stu-id="09def-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="09def-131">Eksik kısıtlamaları (sınırsız) null olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="09def-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="09def-132">Çağıran desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="09def-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="09def-133">Bu döndürülecek bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="09def-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="09def-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="09def-134">Example</span></span>  
 <span data-ttu-id="09def-135">Aşağıdaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> şema tüm içinde yer alan tabloları hakkında bilgi almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için yalnızca "Satış" şemasında tablolar için:</span><span class="sxs-lookup"><span data-stu-id="09def-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="09def-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="09def-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="09def-137">SQL Server şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="09def-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="09def-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="09def-138">Users</span></span>  
  
|<span data-ttu-id="09def-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-139">Restriction Name</span></span>|<span data-ttu-id="09def-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-140">Parameter Name</span></span>|<span data-ttu-id="09def-141">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-141">Restriction Default</span></span>|<span data-ttu-id="09def-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="09def-143">User_Name</span></span>|@Name|<span data-ttu-id="09def-144">name</span><span class="sxs-lookup"><span data-stu-id="09def-144">name</span></span>|<span data-ttu-id="09def-145">1.</span><span class="sxs-lookup"><span data-stu-id="09def-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="09def-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="09def-146">Databases</span></span>  
  
|<span data-ttu-id="09def-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-147">Restriction Name</span></span>|<span data-ttu-id="09def-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-148">Parameter Name</span></span>|<span data-ttu-id="09def-149">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-149">Restriction Default</span></span>|<span data-ttu-id="09def-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-151">Ad</span><span class="sxs-lookup"><span data-stu-id="09def-151">Name</span></span>|@Name|<span data-ttu-id="09def-152">Ad</span><span class="sxs-lookup"><span data-stu-id="09def-152">Name</span></span>|<span data-ttu-id="09def-153">1.</span><span class="sxs-lookup"><span data-stu-id="09def-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="09def-154">tabloları</span><span class="sxs-lookup"><span data-stu-id="09def-154">Tables</span></span>  
  
|<span data-ttu-id="09def-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-155">Restriction Name</span></span>|<span data-ttu-id="09def-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-156">Parameter Name</span></span>|<span data-ttu-id="09def-157">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-157">Restriction Default</span></span>|<span data-ttu-id="09def-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-159">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-160">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-161">1.</span><span class="sxs-lookup"><span data-stu-id="09def-161">1</span></span>|  
|<span data-ttu-id="09def-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-162">Owner</span></span>|@Owner|<span data-ttu-id="09def-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-164">2</span><span class="sxs-lookup"><span data-stu-id="09def-164">2</span></span>|  
|<span data-ttu-id="09def-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-165">Table</span></span>|@Name|<span data-ttu-id="09def-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-166">TABLE_NAME</span></span>|<span data-ttu-id="09def-167">3</span><span class="sxs-lookup"><span data-stu-id="09def-167">3</span></span>|  
|<span data-ttu-id="09def-168">TableType</span><span class="sxs-lookup"><span data-stu-id="09def-168">TableType</span></span>|@TableType|<span data-ttu-id="09def-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="09def-169">TABLE_TYPE</span></span>|<span data-ttu-id="09def-170">4</span><span class="sxs-lookup"><span data-stu-id="09def-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="09def-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="09def-171">Columns</span></span>  
  
|<span data-ttu-id="09def-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-172">Restriction Name</span></span>|<span data-ttu-id="09def-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-173">Parameter Name</span></span>|<span data-ttu-id="09def-174">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-174">Restriction Default</span></span>|<span data-ttu-id="09def-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-176">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-177">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-178">1.</span><span class="sxs-lookup"><span data-stu-id="09def-178">1</span></span>|  
|<span data-ttu-id="09def-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-179">Owner</span></span>|@Owner|<span data-ttu-id="09def-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-181">2</span><span class="sxs-lookup"><span data-stu-id="09def-181">2</span></span>|  
|<span data-ttu-id="09def-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-182">Table</span></span>|@Table|<span data-ttu-id="09def-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-183">TABLE_NAME</span></span>|<span data-ttu-id="09def-184">3</span><span class="sxs-lookup"><span data-stu-id="09def-184">3</span></span>|  
|<span data-ttu-id="09def-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="09def-185">Column</span></span>|@Column|<span data-ttu-id="09def-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-186">COLUMN_NAME</span></span>|<span data-ttu-id="09def-187">4</span><span class="sxs-lookup"><span data-stu-id="09def-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="09def-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="09def-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="09def-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-189">Restriction Name</span></span>|<span data-ttu-id="09def-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-190">Parameter Name</span></span>|<span data-ttu-id="09def-191">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-191">Restriction Default</span></span>|<span data-ttu-id="09def-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-193">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-194">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-195">1.</span><span class="sxs-lookup"><span data-stu-id="09def-195">1</span></span>|  
|<span data-ttu-id="09def-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-196">Owner</span></span>|@Owner|<span data-ttu-id="09def-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-198">2</span><span class="sxs-lookup"><span data-stu-id="09def-198">2</span></span>|  
|<span data-ttu-id="09def-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-199">Table</span></span>|@Table|<span data-ttu-id="09def-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-200">TABLE_NAME</span></span>|<span data-ttu-id="09def-201">3</span><span class="sxs-lookup"><span data-stu-id="09def-201">3</span></span>|  
|<span data-ttu-id="09def-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="09def-202">Column</span></span>|@Column|<span data-ttu-id="09def-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-203">COLUMN_NAME</span></span>|<span data-ttu-id="09def-204">4</span><span class="sxs-lookup"><span data-stu-id="09def-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="09def-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="09def-205">Views</span></span>  
  
|<span data-ttu-id="09def-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-206">Restriction Name</span></span>|<span data-ttu-id="09def-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-207">Parameter Name</span></span>|<span data-ttu-id="09def-208">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-208">Restriction Default</span></span>|<span data-ttu-id="09def-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-210">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-211">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-212">1.</span><span class="sxs-lookup"><span data-stu-id="09def-212">1</span></span>|  
|<span data-ttu-id="09def-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-213">Owner</span></span>|@Owner|<span data-ttu-id="09def-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-215">2</span><span class="sxs-lookup"><span data-stu-id="09def-215">2</span></span>|  
|<span data-ttu-id="09def-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-216">Table</span></span>|@Table|<span data-ttu-id="09def-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-217">TABLE_NAME</span></span>|<span data-ttu-id="09def-218">3</span><span class="sxs-lookup"><span data-stu-id="09def-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="09def-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="09def-219">ViewColumns</span></span>  
  
|<span data-ttu-id="09def-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-220">Restriction Name</span></span>|<span data-ttu-id="09def-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-221">Parameter Name</span></span>|<span data-ttu-id="09def-222">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-222">Restriction Default</span></span>|<span data-ttu-id="09def-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-224">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-225">VIEW_CATALOG</span></span>|<span data-ttu-id="09def-226">1.</span><span class="sxs-lookup"><span data-stu-id="09def-226">1</span></span>|  
|<span data-ttu-id="09def-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-227">Owner</span></span>|@Owner|<span data-ttu-id="09def-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="09def-229">2</span><span class="sxs-lookup"><span data-stu-id="09def-229">2</span></span>|  
|<span data-ttu-id="09def-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-230">Table</span></span>|@Table|<span data-ttu-id="09def-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-231">VIEW_NAME</span></span>|<span data-ttu-id="09def-232">3</span><span class="sxs-lookup"><span data-stu-id="09def-232">3</span></span>|  
|<span data-ttu-id="09def-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="09def-233">Column</span></span>|@Column|<span data-ttu-id="09def-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-234">COLUMN_NAME</span></span>|<span data-ttu-id="09def-235">4</span><span class="sxs-lookup"><span data-stu-id="09def-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="09def-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="09def-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="09def-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-237">Restriction Name</span></span>|<span data-ttu-id="09def-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-238">Parameter Name</span></span>|<span data-ttu-id="09def-239">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-239">Restriction Default</span></span>|<span data-ttu-id="09def-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-241">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="09def-243">1.</span><span class="sxs-lookup"><span data-stu-id="09def-243">1</span></span>|  
|<span data-ttu-id="09def-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-244">Owner</span></span>|@Owner|<span data-ttu-id="09def-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="09def-246">2</span><span class="sxs-lookup"><span data-stu-id="09def-246">2</span></span>|  
|<span data-ttu-id="09def-247">Ad</span><span class="sxs-lookup"><span data-stu-id="09def-247">Name</span></span>|@Name|<span data-ttu-id="09def-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="09def-249">3</span><span class="sxs-lookup"><span data-stu-id="09def-249">3</span></span>|  
|<span data-ttu-id="09def-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="09def-250">Parameter</span></span>|@Parameter|<span data-ttu-id="09def-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-251">PARAMETER_NAME</span></span>|<span data-ttu-id="09def-252">4</span><span class="sxs-lookup"><span data-stu-id="09def-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="09def-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="09def-253">Procedures</span></span>  
  
|<span data-ttu-id="09def-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-254">Restriction Name</span></span>|<span data-ttu-id="09def-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-255">Parameter Name</span></span>|<span data-ttu-id="09def-256">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-256">Restriction Default</span></span>|<span data-ttu-id="09def-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-258">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="09def-260">1.</span><span class="sxs-lookup"><span data-stu-id="09def-260">1</span></span>|  
|<span data-ttu-id="09def-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-261">Owner</span></span>|@Owner|<span data-ttu-id="09def-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="09def-263">2</span><span class="sxs-lookup"><span data-stu-id="09def-263">2</span></span>|  
|<span data-ttu-id="09def-264">Ad</span><span class="sxs-lookup"><span data-stu-id="09def-264">Name</span></span>|@Name|<span data-ttu-id="09def-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="09def-266">3</span><span class="sxs-lookup"><span data-stu-id="09def-266">3</span></span>|  
|<span data-ttu-id="09def-267">Tür</span><span class="sxs-lookup"><span data-stu-id="09def-267">Type</span></span>|@Type|<span data-ttu-id="09def-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="09def-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="09def-269">4</span><span class="sxs-lookup"><span data-stu-id="09def-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="09def-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="09def-270">IndexColumns</span></span>  
  
|<span data-ttu-id="09def-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-271">Restriction Name</span></span>|<span data-ttu-id="09def-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-272">Parameter Name</span></span>|<span data-ttu-id="09def-273">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-273">Restriction Default</span></span>|<span data-ttu-id="09def-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-275">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="09def-276">db_name()</span></span>|<span data-ttu-id="09def-277">1.</span><span class="sxs-lookup"><span data-stu-id="09def-277">1</span></span>|  
|<span data-ttu-id="09def-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-278">Owner</span></span>|@Owner|<span data-ttu-id="09def-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="09def-279">user_name()</span></span>|<span data-ttu-id="09def-280">2</span><span class="sxs-lookup"><span data-stu-id="09def-280">2</span></span>|  
|<span data-ttu-id="09def-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-281">Table</span></span>|@Table|<span data-ttu-id="09def-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="09def-282">o.name</span></span>|<span data-ttu-id="09def-283">3</span><span class="sxs-lookup"><span data-stu-id="09def-283">3</span></span>|  
|<span data-ttu-id="09def-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="09def-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="09def-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="09def-285">x.name</span></span>|<span data-ttu-id="09def-286">4</span><span class="sxs-lookup"><span data-stu-id="09def-286">4</span></span>|  
|<span data-ttu-id="09def-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="09def-287">Column</span></span>|@Column|<span data-ttu-id="09def-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="09def-288">c.name</span></span>|<span data-ttu-id="09def-289">5</span><span class="sxs-lookup"><span data-stu-id="09def-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="09def-290">Dizinler</span><span class="sxs-lookup"><span data-stu-id="09def-290">Indexes</span></span>  
  
|<span data-ttu-id="09def-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-291">Restriction Name</span></span>|<span data-ttu-id="09def-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-292">Parameter Name</span></span>|<span data-ttu-id="09def-293">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-293">Restriction Default</span></span>|<span data-ttu-id="09def-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-295">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="09def-296">db_name()</span></span>|<span data-ttu-id="09def-297">1.</span><span class="sxs-lookup"><span data-stu-id="09def-297">1</span></span>|  
|<span data-ttu-id="09def-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-298">Owner</span></span>|@Owner|<span data-ttu-id="09def-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="09def-299">user_name()</span></span>|<span data-ttu-id="09def-300">2</span><span class="sxs-lookup"><span data-stu-id="09def-300">2</span></span>|  
|<span data-ttu-id="09def-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-301">Table</span></span>|@Table|<span data-ttu-id="09def-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="09def-302">o.name</span></span>|<span data-ttu-id="09def-303">3</span><span class="sxs-lookup"><span data-stu-id="09def-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="09def-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="09def-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="09def-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-305">Restriction Name</span></span>|<span data-ttu-id="09def-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-306">Parameter Name</span></span>|<span data-ttu-id="09def-307">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-307">Restriction Default</span></span>|<span data-ttu-id="09def-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="09def-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="09def-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="09def-310">assemblies.name</span></span>|<span data-ttu-id="09def-311">1.</span><span class="sxs-lookup"><span data-stu-id="09def-311">1</span></span>|  
|<span data-ttu-id="09def-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="09def-312">udt_name</span></span>|@UDTName|<span data-ttu-id="09def-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="09def-313">types.assembly_class</span></span>|<span data-ttu-id="09def-314">2</span><span class="sxs-lookup"><span data-stu-id="09def-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="09def-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="09def-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="09def-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-316">Restriction Name</span></span>|<span data-ttu-id="09def-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-317">Parameter Name</span></span>|<span data-ttu-id="09def-318">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-318">Restriction Default</span></span>|<span data-ttu-id="09def-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-320">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="09def-322">1.</span><span class="sxs-lookup"><span data-stu-id="09def-322">1</span></span>|  
|<span data-ttu-id="09def-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-323">Owner</span></span>|@Owner|<span data-ttu-id="09def-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="09def-325">2</span><span class="sxs-lookup"><span data-stu-id="09def-325">2</span></span>|  
|<span data-ttu-id="09def-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-326">Table</span></span>|@Table|<span data-ttu-id="09def-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-327">TABLE_NAME</span></span>|<span data-ttu-id="09def-328">3</span><span class="sxs-lookup"><span data-stu-id="09def-328">3</span></span>|  
|<span data-ttu-id="09def-329">Ad</span><span class="sxs-lookup"><span data-stu-id="09def-329">Name</span></span>|@Name|<span data-ttu-id="09def-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="09def-331">4</span><span class="sxs-lookup"><span data-stu-id="09def-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="09def-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="09def-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="09def-333">SQL Server 2008 şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="09def-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="09def-334">Bu kısıtlamalar sürüm SQL Server 2008 ve .NET Framework 3.5 SP1 ile başlayan geçerli ' dir.</span><span class="sxs-lookup"><span data-stu-id="09def-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="09def-335">Önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="09def-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="09def-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="09def-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="09def-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-337">Restriction Name</span></span>|<span data-ttu-id="09def-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-338">Parameter Name</span></span>|<span data-ttu-id="09def-339">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-339">Restriction Default</span></span>|<span data-ttu-id="09def-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-341">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-342">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-343">1.</span><span class="sxs-lookup"><span data-stu-id="09def-343">1</span></span>|  
|<span data-ttu-id="09def-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-344">Owner</span></span>|@Owner|<span data-ttu-id="09def-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-346">2</span><span class="sxs-lookup"><span data-stu-id="09def-346">2</span></span>|  
|<span data-ttu-id="09def-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-347">Table</span></span>|@Table|<span data-ttu-id="09def-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-348">TABLE_NAME</span></span>|<span data-ttu-id="09def-349">3</span><span class="sxs-lookup"><span data-stu-id="09def-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="09def-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="09def-350">AllColumns</span></span>  
  
|<span data-ttu-id="09def-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="09def-351">Restriction Name</span></span>|<span data-ttu-id="09def-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="09def-352">Parameter Name</span></span>|<span data-ttu-id="09def-353">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="09def-353">Restriction Default</span></span>|<span data-ttu-id="09def-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="09def-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="09def-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="09def-355">Catalog</span></span>|@Catalog|<span data-ttu-id="09def-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="09def-356">TABLE_CATALOG</span></span>|<span data-ttu-id="09def-357">1.</span><span class="sxs-lookup"><span data-stu-id="09def-357">1</span></span>|  
|<span data-ttu-id="09def-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="09def-358">Owner</span></span>|@Owner|<span data-ttu-id="09def-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="09def-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="09def-360">2</span><span class="sxs-lookup"><span data-stu-id="09def-360">2</span></span>|  
|<span data-ttu-id="09def-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="09def-361">Table</span></span>|@Table|<span data-ttu-id="09def-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-362">TABLE_NAME</span></span>|<span data-ttu-id="09def-363">3</span><span class="sxs-lookup"><span data-stu-id="09def-363">3</span></span>|  
|<span data-ttu-id="09def-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="09def-364">Column</span></span>|@Column|<span data-ttu-id="09def-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="09def-365">COLUMN_NAME</span></span>|<span data-ttu-id="09def-366">4</span><span class="sxs-lookup"><span data-stu-id="09def-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09def-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09def-367">See Also</span></span>  
 [<span data-ttu-id="09def-368">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="09def-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
