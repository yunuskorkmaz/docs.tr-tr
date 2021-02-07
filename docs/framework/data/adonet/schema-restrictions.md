---
description: 'Daha fazla bilgi edinin: şema kısıtlamaları'
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 74ddfe5b8aaf9b8193e0c0b2a929ccde333eac26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719051"
---
# <a name="schema-restrictions"></a><span data-ttu-id="0993a-103">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="0993a-103">Schema Restrictions</span></span>

<span data-ttu-id="0993a-104">**GetSchema** yönteminin ikinci isteğe bağlı parametresi döndürülen şema bilgisi miktarını sınırlamak için kullanılan kısıtlamalardır ve **GetSchema** yöntemine dizeler dizisi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0993a-104">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="0993a-105">Dizideki konum, geçirebileceğinizi belirten değerleri belirler ve bu, kısıtlama numarasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0993a-105">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="0993a-106">Örneğin, aşağıdaki tabloda SQL Server için .NET Framework Veri Sağlayıcısı kullanılarak "tablolar" şema koleksiyonu tarafından desteklenen kısıtlamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0993a-106">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="0993a-107">SQL Server şema koleksiyonları için ek kısıtlamalar bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0993a-107">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="0993a-108">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-108">Restriction Name</span></span>|<span data-ttu-id="0993a-109">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-109">Parameter Name</span></span>|<span data-ttu-id="0993a-110">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-110">Restriction Default</span></span>|<span data-ttu-id="0993a-111">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-111">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-112">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-112">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-113">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-113">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-114">1</span><span class="sxs-lookup"><span data-stu-id="0993a-114">1</span></span>|  
|<span data-ttu-id="0993a-115">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-115">Owner</span></span>|@Owner|<span data-ttu-id="0993a-116">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-116">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-117">2</span><span class="sxs-lookup"><span data-stu-id="0993a-117">2</span></span>|  
|<span data-ttu-id="0993a-118">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-118">Table</span></span>|@Name|<span data-ttu-id="0993a-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-119">TABLE_NAME</span></span>|<span data-ttu-id="0993a-120">3</span><span class="sxs-lookup"><span data-stu-id="0993a-120">3</span></span>|  
|<span data-ttu-id="0993a-121">TableType</span><span class="sxs-lookup"><span data-stu-id="0993a-121">TableType</span></span>|@TableType|<span data-ttu-id="0993a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0993a-122">TABLE_TYPE</span></span>|<span data-ttu-id="0993a-123">4</span><span class="sxs-lookup"><span data-stu-id="0993a-123">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="0993a-124">Kısıtlama değerlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="0993a-124">Specifying Restriction Values</span></span>  

 <span data-ttu-id="0993a-125">"Tables" şema koleksiyonu kısıtlamalarından birini kullanmak için, dört öğeli bir dize dizisi oluşturmanız yeterlidir, sonra bir değeri kısıtlama numarasıyla eşleşen bir değere yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0993a-125">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="0993a-126">Örneğin, **GetSchema** yöntemi tarafından döndürülen tabloları yalnızca "Sales" şemasında bulunan tablolara kısıtlamak için, dizinin Ikinci öğesini **GetSchema** yöntemine geçirmeden önce "Sales" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0993a-126">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0993a-127">İçin kısıtlamalar koleksiyonları `SqlClient` ve `OracleClient` ek bir sütun vardır `ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="0993a-127">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="0993a-128">Kısıtlama varsayılan sütunu, geriye doğru uyumluluk için hala mevcuttur, ancak şu anda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0993a-128">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="0993a-129">Kısıtlama değerlerini belirtirken bir SQL ekleme saldırısının riskini en aza indirmek için, dize değiştirme yerine parametreli sorgular kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0993a-129">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0993a-130">Dizideki öğe sayısı, belirtilen şema koleksiyonu için desteklenen kısıtlama sayısına eşit veya ondan küçük olmalıdır, aksi takdirde bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0993a-130">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="0993a-131">En yüksek kısıtlama sayısından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="0993a-131">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="0993a-132">Eksik kısıtlamaların null (Kısıtlanmamış) olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0993a-132">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="0993a-133">"Kısıtlamalar" olan kısıtlama şeması koleksiyonu adı ile **GetSchema** yöntemini çağırarak desteklenen kısıtlamaların listesini öğrenmek için, .NET Framework yönetilen bir sağlayıcıyı sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0993a-133">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="0993a-134">Bu, <xref:System.Data.DataTable> koleksiyon adlarının, kısıtlama adlarının, varsayılan kısıtlama değerlerinin ve kısıtlama numaralarının listesini içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="0993a-134">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0993a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="0993a-135">Example</span></span>  

 <span data-ttu-id="0993a-136">Aşağıdaki örneklerde, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> **AdventureWorks** örnek veritabanında bulunan tüm tablolar hakkında şema bilgilerini almak ve yalnızca "Sales" şemasında bulunan tablolara döndürülen bilgileri kısıtlamak için SQL Server sınıfı için .NET Framework veri sağlayıcısı yönteminin nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0993a-136">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="0993a-137">SQL Server şeması kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="0993a-137">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="0993a-138">Aşağıdaki tablolarda SQL Server şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0993a-138">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="0993a-139">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="0993a-139">Users</span></span>  
  
|<span data-ttu-id="0993a-140">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-140">Restriction Name</span></span>|<span data-ttu-id="0993a-141">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-141">Parameter Name</span></span>|<span data-ttu-id="0993a-142">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-142">Restriction Default</span></span>|<span data-ttu-id="0993a-143">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-143">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-144">User_Name</span><span class="sxs-lookup"><span data-stu-id="0993a-144">User_Name</span></span>|@Name|<span data-ttu-id="0993a-145">name</span><span class="sxs-lookup"><span data-stu-id="0993a-145">name</span></span>|<span data-ttu-id="0993a-146">1</span><span class="sxs-lookup"><span data-stu-id="0993a-146">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="0993a-147">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="0993a-147">Databases</span></span>  
  
|<span data-ttu-id="0993a-148">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-148">Restriction Name</span></span>|<span data-ttu-id="0993a-149">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-149">Parameter Name</span></span>|<span data-ttu-id="0993a-150">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-150">Restriction Default</span></span>|<span data-ttu-id="0993a-151">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-151">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-152">Name</span><span class="sxs-lookup"><span data-stu-id="0993a-152">Name</span></span>|@Name|<span data-ttu-id="0993a-153">Name</span><span class="sxs-lookup"><span data-stu-id="0993a-153">Name</span></span>|<span data-ttu-id="0993a-154">1</span><span class="sxs-lookup"><span data-stu-id="0993a-154">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="0993a-155">Tablolar</span><span class="sxs-lookup"><span data-stu-id="0993a-155">Tables</span></span>  
  
|<span data-ttu-id="0993a-156">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-156">Restriction Name</span></span>|<span data-ttu-id="0993a-157">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-157">Parameter Name</span></span>|<span data-ttu-id="0993a-158">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-158">Restriction Default</span></span>|<span data-ttu-id="0993a-159">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-159">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-160">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-160">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-161">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-161">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-162">1</span><span class="sxs-lookup"><span data-stu-id="0993a-162">1</span></span>|  
|<span data-ttu-id="0993a-163">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-163">Owner</span></span>|@Owner|<span data-ttu-id="0993a-164">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-164">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-165">2</span><span class="sxs-lookup"><span data-stu-id="0993a-165">2</span></span>|  
|<span data-ttu-id="0993a-166">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-166">Table</span></span>|@Name|<span data-ttu-id="0993a-167">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-167">TABLE_NAME</span></span>|<span data-ttu-id="0993a-168">3</span><span class="sxs-lookup"><span data-stu-id="0993a-168">3</span></span>|  
|<span data-ttu-id="0993a-169">TableType</span><span class="sxs-lookup"><span data-stu-id="0993a-169">TableType</span></span>|@TableType|<span data-ttu-id="0993a-170">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0993a-170">TABLE_TYPE</span></span>|<span data-ttu-id="0993a-171">4</span><span class="sxs-lookup"><span data-stu-id="0993a-171">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0993a-172">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="0993a-172">Columns</span></span>  
  
|<span data-ttu-id="0993a-173">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-173">Restriction Name</span></span>|<span data-ttu-id="0993a-174">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-174">Parameter Name</span></span>|<span data-ttu-id="0993a-175">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-175">Restriction Default</span></span>|<span data-ttu-id="0993a-176">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-176">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-177">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-177">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-178">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-178">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-179">1</span><span class="sxs-lookup"><span data-stu-id="0993a-179">1</span></span>|  
|<span data-ttu-id="0993a-180">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-180">Owner</span></span>|@Owner|<span data-ttu-id="0993a-181">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-181">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-182">2</span><span class="sxs-lookup"><span data-stu-id="0993a-182">2</span></span>|  
|<span data-ttu-id="0993a-183">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-183">Table</span></span>|@Table|<span data-ttu-id="0993a-184">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-184">TABLE_NAME</span></span>|<span data-ttu-id="0993a-185">3</span><span class="sxs-lookup"><span data-stu-id="0993a-185">3</span></span>|  
|<span data-ttu-id="0993a-186">Sütun</span><span class="sxs-lookup"><span data-stu-id="0993a-186">Column</span></span>|@Column|<span data-ttu-id="0993a-187">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-187">COLUMN_NAME</span></span>|<span data-ttu-id="0993a-188">4</span><span class="sxs-lookup"><span data-stu-id="0993a-188">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="0993a-189">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="0993a-189">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="0993a-190">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-190">Restriction Name</span></span>|<span data-ttu-id="0993a-191">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-191">Parameter Name</span></span>|<span data-ttu-id="0993a-192">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-192">Restriction Default</span></span>|<span data-ttu-id="0993a-193">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-193">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-194">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-194">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-195">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-195">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-196">1</span><span class="sxs-lookup"><span data-stu-id="0993a-196">1</span></span>|  
|<span data-ttu-id="0993a-197">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-197">Owner</span></span>|@Owner|<span data-ttu-id="0993a-198">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-198">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-199">2</span><span class="sxs-lookup"><span data-stu-id="0993a-199">2</span></span>|  
|<span data-ttu-id="0993a-200">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-200">Table</span></span>|@Table|<span data-ttu-id="0993a-201">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-201">TABLE_NAME</span></span>|<span data-ttu-id="0993a-202">3</span><span class="sxs-lookup"><span data-stu-id="0993a-202">3</span></span>|  
|<span data-ttu-id="0993a-203">Sütun</span><span class="sxs-lookup"><span data-stu-id="0993a-203">Column</span></span>|@Column|<span data-ttu-id="0993a-204">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-204">COLUMN_NAME</span></span>|<span data-ttu-id="0993a-205">4</span><span class="sxs-lookup"><span data-stu-id="0993a-205">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0993a-206">Görünümler</span><span class="sxs-lookup"><span data-stu-id="0993a-206">Views</span></span>  
  
|<span data-ttu-id="0993a-207">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-207">Restriction Name</span></span>|<span data-ttu-id="0993a-208">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-208">Parameter Name</span></span>|<span data-ttu-id="0993a-209">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-209">Restriction Default</span></span>|<span data-ttu-id="0993a-210">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-210">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-211">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-211">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-212">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-212">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-213">1</span><span class="sxs-lookup"><span data-stu-id="0993a-213">1</span></span>|  
|<span data-ttu-id="0993a-214">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-214">Owner</span></span>|@Owner|<span data-ttu-id="0993a-215">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-215">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-216">2</span><span class="sxs-lookup"><span data-stu-id="0993a-216">2</span></span>|  
|<span data-ttu-id="0993a-217">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-217">Table</span></span>|@Table|<span data-ttu-id="0993a-218">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-218">TABLE_NAME</span></span>|<span data-ttu-id="0993a-219">3</span><span class="sxs-lookup"><span data-stu-id="0993a-219">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="0993a-220">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="0993a-220">ViewColumns</span></span>  
  
|<span data-ttu-id="0993a-221">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-221">Restriction Name</span></span>|<span data-ttu-id="0993a-222">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-222">Parameter Name</span></span>|<span data-ttu-id="0993a-223">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-223">Restriction Default</span></span>|<span data-ttu-id="0993a-224">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-224">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-225">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-225">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-226">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-226">VIEW_CATALOG</span></span>|<span data-ttu-id="0993a-227">1</span><span class="sxs-lookup"><span data-stu-id="0993a-227">1</span></span>|  
|<span data-ttu-id="0993a-228">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-228">Owner</span></span>|@Owner|<span data-ttu-id="0993a-229">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-229">VIEW_SCHEMA</span></span>|<span data-ttu-id="0993a-230">2</span><span class="sxs-lookup"><span data-stu-id="0993a-230">2</span></span>|  
|<span data-ttu-id="0993a-231">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-231">Table</span></span>|@Table|<span data-ttu-id="0993a-232">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-232">VIEW_NAME</span></span>|<span data-ttu-id="0993a-233">3</span><span class="sxs-lookup"><span data-stu-id="0993a-233">3</span></span>|  
|<span data-ttu-id="0993a-234">Sütun</span><span class="sxs-lookup"><span data-stu-id="0993a-234">Column</span></span>|@Column|<span data-ttu-id="0993a-235">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-235">COLUMN_NAME</span></span>|<span data-ttu-id="0993a-236">4</span><span class="sxs-lookup"><span data-stu-id="0993a-236">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0993a-237">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0993a-237">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0993a-238">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-238">Restriction Name</span></span>|<span data-ttu-id="0993a-239">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-239">Parameter Name</span></span>|<span data-ttu-id="0993a-240">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-240">Restriction Default</span></span>|<span data-ttu-id="0993a-241">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-241">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-242">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-242">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-243">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-243">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="0993a-244">1</span><span class="sxs-lookup"><span data-stu-id="0993a-244">1</span></span>|  
|<span data-ttu-id="0993a-245">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-245">Owner</span></span>|@Owner|<span data-ttu-id="0993a-246">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-246">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="0993a-247">2</span><span class="sxs-lookup"><span data-stu-id="0993a-247">2</span></span>|  
|<span data-ttu-id="0993a-248">Name</span><span class="sxs-lookup"><span data-stu-id="0993a-248">Name</span></span>|@Name|<span data-ttu-id="0993a-249">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-249">SPECIFIC_NAME</span></span>|<span data-ttu-id="0993a-250">3</span><span class="sxs-lookup"><span data-stu-id="0993a-250">3</span></span>|  
|<span data-ttu-id="0993a-251">Parametre</span><span class="sxs-lookup"><span data-stu-id="0993a-251">Parameter</span></span>|@Parameter|<span data-ttu-id="0993a-252">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-252">PARAMETER_NAME</span></span>|<span data-ttu-id="0993a-253">4</span><span class="sxs-lookup"><span data-stu-id="0993a-253">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0993a-254">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0993a-254">Procedures</span></span>  
  
|<span data-ttu-id="0993a-255">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-255">Restriction Name</span></span>|<span data-ttu-id="0993a-256">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-256">Parameter Name</span></span>|<span data-ttu-id="0993a-257">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-257">Restriction Default</span></span>|<span data-ttu-id="0993a-258">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-258">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-259">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-259">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-260">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-260">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="0993a-261">1</span><span class="sxs-lookup"><span data-stu-id="0993a-261">1</span></span>|  
|<span data-ttu-id="0993a-262">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-262">Owner</span></span>|@Owner|<span data-ttu-id="0993a-263">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-263">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="0993a-264">2</span><span class="sxs-lookup"><span data-stu-id="0993a-264">2</span></span>|  
|<span data-ttu-id="0993a-265">Name</span><span class="sxs-lookup"><span data-stu-id="0993a-265">Name</span></span>|@Name|<span data-ttu-id="0993a-266">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-266">SPECIFIC_NAME</span></span>|<span data-ttu-id="0993a-267">3</span><span class="sxs-lookup"><span data-stu-id="0993a-267">3</span></span>|  
|<span data-ttu-id="0993a-268">Tür</span><span class="sxs-lookup"><span data-stu-id="0993a-268">Type</span></span>|@Type|<span data-ttu-id="0993a-269">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0993a-269">ROUTINE_TYPE</span></span>|<span data-ttu-id="0993a-270">4</span><span class="sxs-lookup"><span data-stu-id="0993a-270">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="0993a-271">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="0993a-271">IndexColumns</span></span>  
  
|<span data-ttu-id="0993a-272">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-272">Restriction Name</span></span>|<span data-ttu-id="0993a-273">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-273">Parameter Name</span></span>|<span data-ttu-id="0993a-274">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-274">Restriction Default</span></span>|<span data-ttu-id="0993a-275">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-275">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-276">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-276">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-277">db_name ()</span><span class="sxs-lookup"><span data-stu-id="0993a-277">db_name()</span></span>|<span data-ttu-id="0993a-278">1</span><span class="sxs-lookup"><span data-stu-id="0993a-278">1</span></span>|  
|<span data-ttu-id="0993a-279">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-279">Owner</span></span>|@Owner|<span data-ttu-id="0993a-280">user_name ()</span><span class="sxs-lookup"><span data-stu-id="0993a-280">user_name()</span></span>|<span data-ttu-id="0993a-281">2</span><span class="sxs-lookup"><span data-stu-id="0993a-281">2</span></span>|  
|<span data-ttu-id="0993a-282">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-282">Table</span></span>|@Table|<span data-ttu-id="0993a-283">o.name</span><span class="sxs-lookup"><span data-stu-id="0993a-283">o.name</span></span>|<span data-ttu-id="0993a-284">3</span><span class="sxs-lookup"><span data-stu-id="0993a-284">3</span></span>|  
|<span data-ttu-id="0993a-285">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="0993a-285">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="0993a-286">x.name</span><span class="sxs-lookup"><span data-stu-id="0993a-286">x.name</span></span>|<span data-ttu-id="0993a-287">4</span><span class="sxs-lookup"><span data-stu-id="0993a-287">4</span></span>|  
|<span data-ttu-id="0993a-288">Sütun</span><span class="sxs-lookup"><span data-stu-id="0993a-288">Column</span></span>|@Column|<span data-ttu-id="0993a-289">c.name</span><span class="sxs-lookup"><span data-stu-id="0993a-289">c.name</span></span>|<span data-ttu-id="0993a-290">5</span><span class="sxs-lookup"><span data-stu-id="0993a-290">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0993a-291">Dizinler</span><span class="sxs-lookup"><span data-stu-id="0993a-291">Indexes</span></span>  
  
|<span data-ttu-id="0993a-292">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-292">Restriction Name</span></span>|<span data-ttu-id="0993a-293">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-293">Parameter Name</span></span>|<span data-ttu-id="0993a-294">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-294">Restriction Default</span></span>|<span data-ttu-id="0993a-295">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-295">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-296">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-296">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-297">db_name ()</span><span class="sxs-lookup"><span data-stu-id="0993a-297">db_name()</span></span>|<span data-ttu-id="0993a-298">1</span><span class="sxs-lookup"><span data-stu-id="0993a-298">1</span></span>|  
|<span data-ttu-id="0993a-299">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-299">Owner</span></span>|@Owner|<span data-ttu-id="0993a-300">user_name ()</span><span class="sxs-lookup"><span data-stu-id="0993a-300">user_name()</span></span>|<span data-ttu-id="0993a-301">2</span><span class="sxs-lookup"><span data-stu-id="0993a-301">2</span></span>|  
|<span data-ttu-id="0993a-302">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-302">Table</span></span>|@Table|<span data-ttu-id="0993a-303">o.name</span><span class="sxs-lookup"><span data-stu-id="0993a-303">o.name</span></span>|<span data-ttu-id="0993a-304">3</span><span class="sxs-lookup"><span data-stu-id="0993a-304">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="0993a-305">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="0993a-305">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="0993a-306">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-306">Restriction Name</span></span>|<span data-ttu-id="0993a-307">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-307">Parameter Name</span></span>|<span data-ttu-id="0993a-308">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-308">Restriction Default</span></span>|<span data-ttu-id="0993a-309">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-309">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-310">assembly_name</span><span class="sxs-lookup"><span data-stu-id="0993a-310">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="0993a-311">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="0993a-311">assemblies.name</span></span>|<span data-ttu-id="0993a-312">1</span><span class="sxs-lookup"><span data-stu-id="0993a-312">1</span></span>|  
|<span data-ttu-id="0993a-313">udt_name</span><span class="sxs-lookup"><span data-stu-id="0993a-313">udt_name</span></span>|@UDTName|<span data-ttu-id="0993a-314">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="0993a-314">types.assembly_class</span></span>|<span data-ttu-id="0993a-315">2</span><span class="sxs-lookup"><span data-stu-id="0993a-315">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="0993a-316">Yabancıanahtarlar</span><span class="sxs-lookup"><span data-stu-id="0993a-316">ForeignKeys</span></span>  
  
|<span data-ttu-id="0993a-317">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-317">Restriction Name</span></span>|<span data-ttu-id="0993a-318">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-318">Parameter Name</span></span>|<span data-ttu-id="0993a-319">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-319">Restriction Default</span></span>|<span data-ttu-id="0993a-320">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-320">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-321">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-321">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-322">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-322">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="0993a-323">1</span><span class="sxs-lookup"><span data-stu-id="0993a-323">1</span></span>|  
|<span data-ttu-id="0993a-324">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-324">Owner</span></span>|@Owner|<span data-ttu-id="0993a-325">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-325">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="0993a-326">2</span><span class="sxs-lookup"><span data-stu-id="0993a-326">2</span></span>|  
|<span data-ttu-id="0993a-327">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-327">Table</span></span>|@Table|<span data-ttu-id="0993a-328">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-328">TABLE_NAME</span></span>|<span data-ttu-id="0993a-329">3</span><span class="sxs-lookup"><span data-stu-id="0993a-329">3</span></span>|  
|<span data-ttu-id="0993a-330">Name</span><span class="sxs-lookup"><span data-stu-id="0993a-330">Name</span></span>|@Name|<span data-ttu-id="0993a-331">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-331">CONSTRAINT_NAME</span></span>|<span data-ttu-id="0993a-332">4</span><span class="sxs-lookup"><span data-stu-id="0993a-332">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="0993a-333">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="0993a-333">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="0993a-334">Aşağıdaki tablolarda SQL Server 2008 şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0993a-334">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="0993a-335">Bu kısıtlamalar .NET Framework sürüm 3,5 SP1 ve 2008 SQL Server itibaren geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0993a-335">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="0993a-336">.NET Framework ve SQL Server daha önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0993a-336">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="0993a-337">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="0993a-337">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="0993a-338">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-338">Restriction Name</span></span>|<span data-ttu-id="0993a-339">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-339">Parameter Name</span></span>|<span data-ttu-id="0993a-340">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-340">Restriction Default</span></span>|<span data-ttu-id="0993a-341">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-341">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-342">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-342">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-343">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-343">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-344">1</span><span class="sxs-lookup"><span data-stu-id="0993a-344">1</span></span>|  
|<span data-ttu-id="0993a-345">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-345">Owner</span></span>|@Owner|<span data-ttu-id="0993a-346">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-346">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-347">2</span><span class="sxs-lookup"><span data-stu-id="0993a-347">2</span></span>|  
|<span data-ttu-id="0993a-348">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-348">Table</span></span>|@Table|<span data-ttu-id="0993a-349">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-349">TABLE_NAME</span></span>|<span data-ttu-id="0993a-350">3</span><span class="sxs-lookup"><span data-stu-id="0993a-350">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="0993a-351">AllColumns</span><span class="sxs-lookup"><span data-stu-id="0993a-351">AllColumns</span></span>  
  
|<span data-ttu-id="0993a-352">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="0993a-352">Restriction Name</span></span>|<span data-ttu-id="0993a-353">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="0993a-353">Parameter Name</span></span>|<span data-ttu-id="0993a-354">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0993a-354">Restriction Default</span></span>|<span data-ttu-id="0993a-355">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="0993a-355">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="0993a-356">Katalog</span><span class="sxs-lookup"><span data-stu-id="0993a-356">Catalog</span></span>|@Catalog|<span data-ttu-id="0993a-357">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0993a-357">TABLE_CATALOG</span></span>|<span data-ttu-id="0993a-358">1</span><span class="sxs-lookup"><span data-stu-id="0993a-358">1</span></span>|  
|<span data-ttu-id="0993a-359">Sahip</span><span class="sxs-lookup"><span data-stu-id="0993a-359">Owner</span></span>|@Owner|<span data-ttu-id="0993a-360">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0993a-360">TABLE_SCHEMA</span></span>|<span data-ttu-id="0993a-361">2</span><span class="sxs-lookup"><span data-stu-id="0993a-361">2</span></span>|  
|<span data-ttu-id="0993a-362">Tablo</span><span class="sxs-lookup"><span data-stu-id="0993a-362">Table</span></span>|@Table|<span data-ttu-id="0993a-363">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-363">TABLE_NAME</span></span>|<span data-ttu-id="0993a-364">3</span><span class="sxs-lookup"><span data-stu-id="0993a-364">3</span></span>|  
|<span data-ttu-id="0993a-365">Sütun</span><span class="sxs-lookup"><span data-stu-id="0993a-365">Column</span></span>|@Column|<span data-ttu-id="0993a-366">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0993a-366">COLUMN_NAME</span></span>|<span data-ttu-id="0993a-367">4</span><span class="sxs-lookup"><span data-stu-id="0993a-367">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0993a-368">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0993a-368">See also</span></span>

- [<span data-ttu-id="0993a-369">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0993a-369">ADO.NET Overview</span></span>](ado-net-overview.md)
