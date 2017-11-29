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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="a92b4-102">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="a92b4-102">Schema Restrictions</span></span>
<span data-ttu-id="a92b4-103">İkinci isteğe bağlı parametresi, **GetSchema** yöntemdir şema bilgi tutarını sınırlamak için kullanılan kısıtlamaları döndürülür ve için geçirilen **GetSchema** bir dize dizisi olarak yöntemi .</span><span class="sxs-lookup"><span data-stu-id="a92b4-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="a92b4-104">Dizideki konumu geçirebilirsiniz değerleri belirler ve bu kısıtlama sayıya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="a92b4-105">Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="a92b4-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="a92b4-106">SQL Server şeması koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="a92b4-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-107">Restriction Name</span></span>|<span data-ttu-id="a92b4-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-108">Parameter Name</span></span>|<span data-ttu-id="a92b4-109">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-109">Restriction Default</span></span>|<span data-ttu-id="a92b4-110">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-111">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-112">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-113">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-113">1</span></span>|  
|<span data-ttu-id="a92b4-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-114">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-116">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-116">2</span></span>|  
|<span data-ttu-id="a92b4-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-117">Table</span></span>|@Name|<span data-ttu-id="a92b4-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-118">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-119">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-119">3</span></span>|  
|<span data-ttu-id="a92b4-120">TableType</span><span class="sxs-lookup"><span data-stu-id="a92b4-120">TableType</span></span>|@TableType|<span data-ttu-id="a92b4-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a92b4-121">TABLE_TYPE</span></span>|<span data-ttu-id="a92b4-122">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="a92b4-123">Kısıtlama değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="a92b4-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="a92b4-124">"Tablo" şema koleksiyonu kısıtlamalarını birini kullanmak için yalnızca bir dizeler dizisi ile dört öğeleri oluşturun, sonra bir değer kısıtlama numarasıyla eşleşen öğe yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a92b4-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="a92b4-125">Örneğin, tablolar kısıtlamak için tarafından geri döndürülen **GetSchema** geçirmeden önce "Satış" diziye ikinci öğesini set yöntemi yalnızca "Satış" şemasında tablolara **GetSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a92b4-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a92b4-126">Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun.</span><span class="sxs-lookup"><span data-stu-id="a92b4-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="a92b4-127">Kısıtlama varsayılan sütunu yine için geriye dönük uyumluluk yoktur, ancak şu anda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="a92b4-128">Dize değiştirme yerine parametreli sorgular kısıtlama değerleri belirtirken SQL ekleme saldırı riskini en aza indirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a92b4-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a92b4-129">Dizideki öğelerin sayısı başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a92b4-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="a92b4-130">Olabilir kısıtlamaları maksimum sayısından az.</span><span class="sxs-lookup"><span data-stu-id="a92b4-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="a92b4-131">Eksik kısıtlamaları (sınırsız) null olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a92b4-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="a92b4-132">Çağıran desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="a92b4-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="a92b4-133">Bu döndürülecek bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.</span><span class="sxs-lookup"><span data-stu-id="a92b4-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a92b4-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="a92b4-134">Example</span></span>  
 <span data-ttu-id="a92b4-135">Aşağıdaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> şema tüm içinde yer alan tabloları hakkında bilgi almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için yalnızca "Satış" şemasında tablolar için:</span><span class="sxs-lookup"><span data-stu-id="a92b4-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="a92b4-136">SQL Server şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="a92b4-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="a92b4-137">SQL Server şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="a92b4-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="a92b4-138">Users</span></span>  
  
|<span data-ttu-id="a92b4-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-139">Restriction Name</span></span>|<span data-ttu-id="a92b4-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-140">Parameter Name</span></span>|<span data-ttu-id="a92b4-141">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-141">Restriction Default</span></span>|<span data-ttu-id="a92b4-142">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-143">User_name</span><span class="sxs-lookup"><span data-stu-id="a92b4-143">User_Name</span></span>|@Name|<span data-ttu-id="a92b4-144">name</span><span class="sxs-lookup"><span data-stu-id="a92b4-144">name</span></span>|<span data-ttu-id="a92b4-145">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="a92b4-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="a92b4-146">Databases</span></span>  
  
|<span data-ttu-id="a92b4-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-147">Restriction Name</span></span>|<span data-ttu-id="a92b4-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-148">Parameter Name</span></span>|<span data-ttu-id="a92b4-149">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-149">Restriction Default</span></span>|<span data-ttu-id="a92b4-150">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-151">Ad</span><span class="sxs-lookup"><span data-stu-id="a92b4-151">Name</span></span>|@Name|<span data-ttu-id="a92b4-152">Ad</span><span class="sxs-lookup"><span data-stu-id="a92b4-152">Name</span></span>|<span data-ttu-id="a92b4-153">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="a92b4-154">tabloları</span><span class="sxs-lookup"><span data-stu-id="a92b4-154">Tables</span></span>  
  
|<span data-ttu-id="a92b4-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-155">Restriction Name</span></span>|<span data-ttu-id="a92b4-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-156">Parameter Name</span></span>|<span data-ttu-id="a92b4-157">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-157">Restriction Default</span></span>|<span data-ttu-id="a92b4-158">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-159">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-160">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-161">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-161">1</span></span>|  
|<span data-ttu-id="a92b4-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-162">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-164">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-164">2</span></span>|  
|<span data-ttu-id="a92b4-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-165">Table</span></span>|@Name|<span data-ttu-id="a92b4-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-166">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-167">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-167">3</span></span>|  
|<span data-ttu-id="a92b4-168">TableType</span><span class="sxs-lookup"><span data-stu-id="a92b4-168">TableType</span></span>|@TableType|<span data-ttu-id="a92b4-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a92b4-169">TABLE_TYPE</span></span>|<span data-ttu-id="a92b4-170">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a92b4-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="a92b4-171">Columns</span></span>  
  
|<span data-ttu-id="a92b4-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-172">Restriction Name</span></span>|<span data-ttu-id="a92b4-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-173">Parameter Name</span></span>|<span data-ttu-id="a92b4-174">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-174">Restriction Default</span></span>|<span data-ttu-id="a92b4-175">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-176">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-177">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-178">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-178">1</span></span>|  
|<span data-ttu-id="a92b4-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-179">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-181">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-181">2</span></span>|  
|<span data-ttu-id="a92b4-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-182">Table</span></span>|@Table|<span data-ttu-id="a92b4-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-183">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-184">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-184">3</span></span>|  
|<span data-ttu-id="a92b4-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="a92b4-185">Column</span></span>|@Column|<span data-ttu-id="a92b4-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-186">COLUMN_NAME</span></span>|<span data-ttu-id="a92b4-187">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="a92b4-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="a92b4-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="a92b4-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-189">Restriction Name</span></span>|<span data-ttu-id="a92b4-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-190">Parameter Name</span></span>|<span data-ttu-id="a92b4-191">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-191">Restriction Default</span></span>|<span data-ttu-id="a92b4-192">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-193">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-194">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-195">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-195">1</span></span>|  
|<span data-ttu-id="a92b4-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-196">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-198">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-198">2</span></span>|  
|<span data-ttu-id="a92b4-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-199">Table</span></span>|@Table|<span data-ttu-id="a92b4-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-200">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-201">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-201">3</span></span>|  
|<span data-ttu-id="a92b4-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="a92b4-202">Column</span></span>|@Column|<span data-ttu-id="a92b4-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-203">COLUMN_NAME</span></span>|<span data-ttu-id="a92b4-204">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a92b4-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="a92b4-205">Views</span></span>  
  
|<span data-ttu-id="a92b4-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-206">Restriction Name</span></span>|<span data-ttu-id="a92b4-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-207">Parameter Name</span></span>|<span data-ttu-id="a92b4-208">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-208">Restriction Default</span></span>|<span data-ttu-id="a92b4-209">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-210">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-211">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-212">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-212">1</span></span>|  
|<span data-ttu-id="a92b4-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-213">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-215">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-215">2</span></span>|  
|<span data-ttu-id="a92b4-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-216">Table</span></span>|@Table|<span data-ttu-id="a92b4-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-217">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-218">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="a92b4-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="a92b4-219">ViewColumns</span></span>  
  
|<span data-ttu-id="a92b4-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-220">Restriction Name</span></span>|<span data-ttu-id="a92b4-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-221">Parameter Name</span></span>|<span data-ttu-id="a92b4-222">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-222">Restriction Default</span></span>|<span data-ttu-id="a92b4-223">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-224">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-225">VIEW_CATALOG</span></span>|<span data-ttu-id="a92b4-226">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-226">1</span></span>|  
|<span data-ttu-id="a92b4-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-227">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="a92b4-229">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-229">2</span></span>|  
|<span data-ttu-id="a92b4-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-230">Table</span></span>|@Table|<span data-ttu-id="a92b4-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-231">VIEW_NAME</span></span>|<span data-ttu-id="a92b4-232">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-232">3</span></span>|  
|<span data-ttu-id="a92b4-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="a92b4-233">Column</span></span>|@Column|<span data-ttu-id="a92b4-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-234">COLUMN_NAME</span></span>|<span data-ttu-id="a92b4-235">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="a92b4-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a92b4-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="a92b4-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-237">Restriction Name</span></span>|<span data-ttu-id="a92b4-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-238">Parameter Name</span></span>|<span data-ttu-id="a92b4-239">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-239">Restriction Default</span></span>|<span data-ttu-id="a92b4-240">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-241">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a92b4-243">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-243">1</span></span>|  
|<span data-ttu-id="a92b4-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-244">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a92b4-246">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-246">2</span></span>|  
|<span data-ttu-id="a92b4-247">Ad</span><span class="sxs-lookup"><span data-stu-id="a92b4-247">Name</span></span>|@Name|<span data-ttu-id="a92b4-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="a92b4-249">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-249">3</span></span>|  
|<span data-ttu-id="a92b4-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="a92b4-250">Parameter</span></span>|@Parameter|<span data-ttu-id="a92b4-251">PARAMETRE_ADÝ</span><span class="sxs-lookup"><span data-stu-id="a92b4-251">PARAMETER_NAME</span></span>|<span data-ttu-id="a92b4-252">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a92b4-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a92b4-253">Procedures</span></span>  
  
|<span data-ttu-id="a92b4-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-254">Restriction Name</span></span>|<span data-ttu-id="a92b4-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-255">Parameter Name</span></span>|<span data-ttu-id="a92b4-256">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-256">Restriction Default</span></span>|<span data-ttu-id="a92b4-257">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-258">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a92b4-260">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-260">1</span></span>|  
|<span data-ttu-id="a92b4-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-261">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a92b4-263">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-263">2</span></span>|  
|<span data-ttu-id="a92b4-264">Ad</span><span class="sxs-lookup"><span data-stu-id="a92b4-264">Name</span></span>|@Name|<span data-ttu-id="a92b4-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="a92b4-266">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-266">3</span></span>|  
|<span data-ttu-id="a92b4-267">Tür</span><span class="sxs-lookup"><span data-stu-id="a92b4-267">Type</span></span>|@Type|<span data-ttu-id="a92b4-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a92b4-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="a92b4-269">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="a92b4-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="a92b4-270">IndexColumns</span></span>  
  
|<span data-ttu-id="a92b4-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-271">Restriction Name</span></span>|<span data-ttu-id="a92b4-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-272">Parameter Name</span></span>|<span data-ttu-id="a92b4-273">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-273">Restriction Default</span></span>|<span data-ttu-id="a92b4-274">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-275">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="a92b4-276">db_name()</span></span>|<span data-ttu-id="a92b4-277">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-277">1</span></span>|  
|<span data-ttu-id="a92b4-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-278">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-279">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="a92b4-279">user_name()</span></span>|<span data-ttu-id="a92b4-280">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-280">2</span></span>|  
|<span data-ttu-id="a92b4-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-281">Table</span></span>|@Table|<span data-ttu-id="a92b4-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="a92b4-282">o.name</span></span>|<span data-ttu-id="a92b4-283">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-283">3</span></span>|  
|<span data-ttu-id="a92b4-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="a92b4-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="a92b4-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="a92b4-285">x.name</span></span>|<span data-ttu-id="a92b4-286">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-286">4</span></span>|  
|<span data-ttu-id="a92b4-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="a92b4-287">Column</span></span>|@Column|<span data-ttu-id="a92b4-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="a92b4-288">c.name</span></span>|<span data-ttu-id="a92b4-289">5</span><span class="sxs-lookup"><span data-stu-id="a92b4-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a92b4-290">Dizinler</span><span class="sxs-lookup"><span data-stu-id="a92b4-290">Indexes</span></span>  
  
|<span data-ttu-id="a92b4-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-291">Restriction Name</span></span>|<span data-ttu-id="a92b4-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-292">Parameter Name</span></span>|<span data-ttu-id="a92b4-293">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-293">Restriction Default</span></span>|<span data-ttu-id="a92b4-294">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-295">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="a92b4-296">db_name()</span></span>|<span data-ttu-id="a92b4-297">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-297">1</span></span>|  
|<span data-ttu-id="a92b4-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-298">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-299">USER_NAME()</span><span class="sxs-lookup"><span data-stu-id="a92b4-299">user_name()</span></span>|<span data-ttu-id="a92b4-300">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-300">2</span></span>|  
|<span data-ttu-id="a92b4-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-301">Table</span></span>|@Table|<span data-ttu-id="a92b4-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="a92b4-302">o.name</span></span>|<span data-ttu-id="a92b4-303">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="a92b4-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="a92b4-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="a92b4-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-305">Restriction Name</span></span>|<span data-ttu-id="a92b4-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-306">Parameter Name</span></span>|<span data-ttu-id="a92b4-307">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-307">Restriction Default</span></span>|<span data-ttu-id="a92b4-308">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="a92b4-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="a92b4-310">Assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="a92b4-310">assemblies.name</span></span>|<span data-ttu-id="a92b4-311">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-311">1</span></span>|  
|<span data-ttu-id="a92b4-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="a92b4-312">udt_name</span></span>|@UDTName|<span data-ttu-id="a92b4-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="a92b4-313">types.assembly_class</span></span>|<span data-ttu-id="a92b4-314">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="a92b4-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="a92b4-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="a92b4-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-316">Restriction Name</span></span>|<span data-ttu-id="a92b4-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-317">Parameter Name</span></span>|<span data-ttu-id="a92b4-318">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-318">Restriction Default</span></span>|<span data-ttu-id="a92b4-319">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-320">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="a92b4-322">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-322">1</span></span>|  
|<span data-ttu-id="a92b4-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-323">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="a92b4-325">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-325">2</span></span>|  
|<span data-ttu-id="a92b4-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-326">Table</span></span>|@Table|<span data-ttu-id="a92b4-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-327">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-328">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-328">3</span></span>|  
|<span data-ttu-id="a92b4-329">Ad</span><span class="sxs-lookup"><span data-stu-id="a92b4-329">Name</span></span>|@Name|<span data-ttu-id="a92b4-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="a92b4-331">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="a92b4-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="a92b4-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="a92b4-333">SQL Server 2008 şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="a92b4-334">Bu kısıtlamalar sürüm SQL Server 2008 ve .NET Framework 3.5 SP1 ile başlayan geçerli ' dir.</span><span class="sxs-lookup"><span data-stu-id="a92b4-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="a92b4-335">Önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a92b4-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="a92b4-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="a92b4-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="a92b4-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-337">Restriction Name</span></span>|<span data-ttu-id="a92b4-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-338">Parameter Name</span></span>|<span data-ttu-id="a92b4-339">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-339">Restriction Default</span></span>|<span data-ttu-id="a92b4-340">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-341">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-342">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-343">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-343">1</span></span>|  
|<span data-ttu-id="a92b4-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-344">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-346">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-346">2</span></span>|  
|<span data-ttu-id="a92b4-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-347">Table</span></span>|@Table|<span data-ttu-id="a92b4-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-348">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-349">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="a92b4-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="a92b4-350">AllColumns</span></span>  
  
|<span data-ttu-id="a92b4-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-351">Restriction Name</span></span>|<span data-ttu-id="a92b4-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="a92b4-352">Parameter Name</span></span>|<span data-ttu-id="a92b4-353">Kısıtlama varsayılan</span><span class="sxs-lookup"><span data-stu-id="a92b4-353">Restriction Default</span></span>|<span data-ttu-id="a92b4-354">Kısıtlama sayısı</span><span class="sxs-lookup"><span data-stu-id="a92b4-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a92b4-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="a92b4-355">Catalog</span></span>|@Catalog|<span data-ttu-id="a92b4-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a92b4-356">TABLE_CATALOG</span></span>|<span data-ttu-id="a92b4-357">1.</span><span class="sxs-lookup"><span data-stu-id="a92b4-357">1</span></span>|  
|<span data-ttu-id="a92b4-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="a92b4-358">Owner</span></span>|@Owner|<span data-ttu-id="a92b4-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a92b4-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="a92b4-360">2</span><span class="sxs-lookup"><span data-stu-id="a92b4-360">2</span></span>|  
|<span data-ttu-id="a92b4-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="a92b4-361">Table</span></span>|@Table|<span data-ttu-id="a92b4-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-362">TABLE_NAME</span></span>|<span data-ttu-id="a92b4-363">3</span><span class="sxs-lookup"><span data-stu-id="a92b4-363">3</span></span>|  
|<span data-ttu-id="a92b4-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="a92b4-364">Column</span></span>|@Column|<span data-ttu-id="a92b4-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a92b4-365">COLUMN_NAME</span></span>|<span data-ttu-id="a92b4-366">4</span><span class="sxs-lookup"><span data-stu-id="a92b4-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a92b4-367">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a92b4-367">See Also</span></span>  
 [<span data-ttu-id="a92b4-368">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a92b4-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
