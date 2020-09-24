---
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c0a3cafef45341cd95fa0a4f65c818129e120e44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147830"
---
# <a name="schema-restrictions"></a><span data-ttu-id="e4a8a-102">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e4a8a-102">Schema Restrictions</span></span>

<span data-ttu-id="e4a8a-103">**GetSchema** yönteminin ikinci isteğe bağlı parametresi döndürülen şema bilgisi miktarını sınırlamak için kullanılan kısıtlamalardır ve **GetSchema** yöntemine dizeler dizisi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="e4a8a-104">Dizideki konum, geçirebileceğinizi belirten değerleri belirler ve bu, kısıtlama numarasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="e4a8a-105">Örneğin, aşağıdaki tabloda SQL Server için .NET Framework Veri Sağlayıcısı kullanılarak "tablolar" şema koleksiyonu tarafından desteklenen kısıtlamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e4a8a-106">SQL Server şema koleksiyonları için ek kısıtlamalar bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="e4a8a-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-107">Restriction Name</span></span>|<span data-ttu-id="e4a8a-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-108">Parameter Name</span></span>|<span data-ttu-id="e4a8a-109">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-109">Restriction Default</span></span>|<span data-ttu-id="e4a8a-110">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-111">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-112">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-113">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-113">1</span></span>|  
|<span data-ttu-id="e4a8a-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-114">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-116">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-116">2</span></span>|  
|<span data-ttu-id="e4a8a-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-117">Table</span></span>|@Name|<span data-ttu-id="e4a8a-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-118">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-119">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-119">3</span></span>|  
|<span data-ttu-id="e4a8a-120">TableType</span><span class="sxs-lookup"><span data-stu-id="e4a8a-120">TableType</span></span>|@TableType|<span data-ttu-id="e4a8a-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e4a8a-121">TABLE_TYPE</span></span>|<span data-ttu-id="e4a8a-122">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="e4a8a-123">Kısıtlama değerlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="e4a8a-123">Specifying Restriction Values</span></span>  

 <span data-ttu-id="e4a8a-124">"Tables" şema koleksiyonu kısıtlamalarından birini kullanmak için, dört öğeli bir dize dizisi oluşturmanız yeterlidir, sonra bir değeri kısıtlama numarasıyla eşleşen bir değere yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="e4a8a-125">Örneğin, **GetSchema** yöntemi tarafından döndürülen tabloları yalnızca "Sales" şemasında bulunan tablolara kısıtlamak için, dizinin Ikinci öğesini **GetSchema** yöntemine geçirmeden önce "Sales" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4a8a-126">İçin kısıtlamalar koleksiyonları `SqlClient` ve `OracleClient` ek bir sütun vardır `ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="e4a8a-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="e4a8a-127">Kısıtlama varsayılan sütunu, geriye doğru uyumluluk için hala mevcuttur, ancak şu anda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="e4a8a-128">Kısıtlama değerlerini belirtirken bir SQL ekleme saldırısının riskini en aza indirmek için, dize değiştirme yerine parametreli sorgular kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4a8a-129">Dizideki öğe sayısı, belirtilen şema koleksiyonu için desteklenen kısıtlama sayısına eşit veya ondan küçük olmalıdır, aksi takdirde bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="e4a8a-130">En yüksek kısıtlama sayısından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="e4a8a-131">Eksik kısıtlamaların null (Kısıtlanmamış) olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="e4a8a-132">"Kısıtlamalar" olan kısıtlama şeması koleksiyonu adı ile **GetSchema** yöntemini çağırarak desteklenen kısıtlamaların listesini öğrenmek için, .NET Framework yönetilen bir sağlayıcıyı sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="e4a8a-133">Bu, <xref:System.Data.DataTable> koleksiyon adlarının, kısıtlama adlarının, varsayılan kısıtlama değerlerinin ve kısıtlama numaralarının listesini içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4a8a-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4a8a-134">Example</span></span>  

 <span data-ttu-id="e4a8a-135">Aşağıdaki örneklerde, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> **AdventureWorks** örnek veritabanında bulunan tüm tablolar hakkında şema bilgilerini almak ve yalnızca "Sales" şemasında bulunan tablolara döndürülen bilgileri kısıtlamak için SQL Server sınıfı için .NET Framework veri sağlayıcısı yönteminin nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e4a8a-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="e4a8a-136">SQL Server şeması kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e4a8a-136">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="e4a8a-137">Aşağıdaki tablolarda SQL Server şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="e4a8a-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="e4a8a-138">Users</span></span>  
  
|<span data-ttu-id="e4a8a-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-139">Restriction Name</span></span>|<span data-ttu-id="e4a8a-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-140">Parameter Name</span></span>|<span data-ttu-id="e4a8a-141">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-141">Restriction Default</span></span>|<span data-ttu-id="e4a8a-142">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-143">User_Name</span></span>|@Name|<span data-ttu-id="e4a8a-144">name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-144">name</span></span>|<span data-ttu-id="e4a8a-145">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="e4a8a-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="e4a8a-146">Databases</span></span>  
  
|<span data-ttu-id="e4a8a-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-147">Restriction Name</span></span>|<span data-ttu-id="e4a8a-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-148">Parameter Name</span></span>|<span data-ttu-id="e4a8a-149">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-149">Restriction Default</span></span>|<span data-ttu-id="e4a8a-150">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-151">Ad</span><span class="sxs-lookup"><span data-stu-id="e4a8a-151">Name</span></span>|@Name|<span data-ttu-id="e4a8a-152">Ad</span><span class="sxs-lookup"><span data-stu-id="e4a8a-152">Name</span></span>|<span data-ttu-id="e4a8a-153">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="e4a8a-154">Tablolar</span><span class="sxs-lookup"><span data-stu-id="e4a8a-154">Tables</span></span>  
  
|<span data-ttu-id="e4a8a-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-155">Restriction Name</span></span>|<span data-ttu-id="e4a8a-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-156">Parameter Name</span></span>|<span data-ttu-id="e4a8a-157">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-157">Restriction Default</span></span>|<span data-ttu-id="e4a8a-158">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-159">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-160">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-161">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-161">1</span></span>|  
|<span data-ttu-id="e4a8a-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-162">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-164">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-164">2</span></span>|  
|<span data-ttu-id="e4a8a-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-165">Table</span></span>|@Name|<span data-ttu-id="e4a8a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-166">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-167">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-167">3</span></span>|  
|<span data-ttu-id="e4a8a-168">TableType</span><span class="sxs-lookup"><span data-stu-id="e4a8a-168">TableType</span></span>|@TableType|<span data-ttu-id="e4a8a-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e4a8a-169">TABLE_TYPE</span></span>|<span data-ttu-id="e4a8a-170">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e4a8a-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="e4a8a-171">Columns</span></span>  
  
|<span data-ttu-id="e4a8a-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-172">Restriction Name</span></span>|<span data-ttu-id="e4a8a-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-173">Parameter Name</span></span>|<span data-ttu-id="e4a8a-174">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-174">Restriction Default</span></span>|<span data-ttu-id="e4a8a-175">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-176">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-177">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-178">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-178">1</span></span>|  
|<span data-ttu-id="e4a8a-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-179">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-181">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-181">2</span></span>|  
|<span data-ttu-id="e4a8a-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-182">Table</span></span>|@Table|<span data-ttu-id="e4a8a-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-183">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-184">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-184">3</span></span>|  
|<span data-ttu-id="e4a8a-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="e4a8a-185">Column</span></span>|@Column|<span data-ttu-id="e4a8a-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-186">COLUMN_NAME</span></span>|<span data-ttu-id="e4a8a-187">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="e4a8a-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="e4a8a-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="e4a8a-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-189">Restriction Name</span></span>|<span data-ttu-id="e4a8a-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-190">Parameter Name</span></span>|<span data-ttu-id="e4a8a-191">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-191">Restriction Default</span></span>|<span data-ttu-id="e4a8a-192">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-193">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-194">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-195">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-195">1</span></span>|  
|<span data-ttu-id="e4a8a-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-196">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-198">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-198">2</span></span>|  
|<span data-ttu-id="e4a8a-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-199">Table</span></span>|@Table|<span data-ttu-id="e4a8a-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-200">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-201">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-201">3</span></span>|  
|<span data-ttu-id="e4a8a-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="e4a8a-202">Column</span></span>|@Column|<span data-ttu-id="e4a8a-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-203">COLUMN_NAME</span></span>|<span data-ttu-id="e4a8a-204">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e4a8a-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="e4a8a-205">Views</span></span>  
  
|<span data-ttu-id="e4a8a-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-206">Restriction Name</span></span>|<span data-ttu-id="e4a8a-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-207">Parameter Name</span></span>|<span data-ttu-id="e4a8a-208">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-208">Restriction Default</span></span>|<span data-ttu-id="e4a8a-209">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-210">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-211">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-212">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-212">1</span></span>|  
|<span data-ttu-id="e4a8a-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-213">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-215">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-215">2</span></span>|  
|<span data-ttu-id="e4a8a-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-216">Table</span></span>|@Table|<span data-ttu-id="e4a8a-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-217">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-218">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="e4a8a-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="e4a8a-219">ViewColumns</span></span>  
  
|<span data-ttu-id="e4a8a-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-220">Restriction Name</span></span>|<span data-ttu-id="e4a8a-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-221">Parameter Name</span></span>|<span data-ttu-id="e4a8a-222">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-222">Restriction Default</span></span>|<span data-ttu-id="e4a8a-223">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-224">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-225">VIEW_CATALOG</span></span>|<span data-ttu-id="e4a8a-226">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-226">1</span></span>|  
|<span data-ttu-id="e4a8a-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-227">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="e4a8a-229">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-229">2</span></span>|  
|<span data-ttu-id="e4a8a-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-230">Table</span></span>|@Table|<span data-ttu-id="e4a8a-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-231">VIEW_NAME</span></span>|<span data-ttu-id="e4a8a-232">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-232">3</span></span>|  
|<span data-ttu-id="e4a8a-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="e4a8a-233">Column</span></span>|@Column|<span data-ttu-id="e4a8a-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-234">COLUMN_NAME</span></span>|<span data-ttu-id="e4a8a-235">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e4a8a-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e4a8a-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e4a8a-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-237">Restriction Name</span></span>|<span data-ttu-id="e4a8a-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-238">Parameter Name</span></span>|<span data-ttu-id="e4a8a-239">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-239">Restriction Default</span></span>|<span data-ttu-id="e4a8a-240">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-241">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e4a8a-243">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-243">1</span></span>|  
|<span data-ttu-id="e4a8a-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-244">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e4a8a-246">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-246">2</span></span>|  
|<span data-ttu-id="e4a8a-247">Ad</span><span class="sxs-lookup"><span data-stu-id="e4a8a-247">Name</span></span>|@Name|<span data-ttu-id="e4a8a-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="e4a8a-249">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-249">3</span></span>|  
|<span data-ttu-id="e4a8a-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="e4a8a-250">Parameter</span></span>|@Parameter|<span data-ttu-id="e4a8a-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-251">PARAMETER_NAME</span></span>|<span data-ttu-id="e4a8a-252">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e4a8a-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e4a8a-253">Procedures</span></span>  
  
|<span data-ttu-id="e4a8a-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-254">Restriction Name</span></span>|<span data-ttu-id="e4a8a-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-255">Parameter Name</span></span>|<span data-ttu-id="e4a8a-256">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-256">Restriction Default</span></span>|<span data-ttu-id="e4a8a-257">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-258">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="e4a8a-260">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-260">1</span></span>|  
|<span data-ttu-id="e4a8a-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-261">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="e4a8a-263">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-263">2</span></span>|  
|<span data-ttu-id="e4a8a-264">Ad</span><span class="sxs-lookup"><span data-stu-id="e4a8a-264">Name</span></span>|@Name|<span data-ttu-id="e4a8a-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="e4a8a-266">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-266">3</span></span>|  
|<span data-ttu-id="e4a8a-267">Tür</span><span class="sxs-lookup"><span data-stu-id="e4a8a-267">Type</span></span>|@Type|<span data-ttu-id="e4a8a-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e4a8a-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="e4a8a-269">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="e4a8a-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="e4a8a-270">IndexColumns</span></span>  
  
|<span data-ttu-id="e4a8a-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-271">Restriction Name</span></span>|<span data-ttu-id="e4a8a-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-272">Parameter Name</span></span>|<span data-ttu-id="e4a8a-273">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-273">Restriction Default</span></span>|<span data-ttu-id="e4a8a-274">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-275">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-276">db_name ()</span><span class="sxs-lookup"><span data-stu-id="e4a8a-276">db_name()</span></span>|<span data-ttu-id="e4a8a-277">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-277">1</span></span>|  
|<span data-ttu-id="e4a8a-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-278">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-279">user_name ()</span><span class="sxs-lookup"><span data-stu-id="e4a8a-279">user_name()</span></span>|<span data-ttu-id="e4a8a-280">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-280">2</span></span>|  
|<span data-ttu-id="e4a8a-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-281">Table</span></span>|@Table|<span data-ttu-id="e4a8a-282">o.name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-282">o.name</span></span>|<span data-ttu-id="e4a8a-283">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-283">3</span></span>|  
|<span data-ttu-id="e4a8a-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="e4a8a-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="e4a8a-285">x.name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-285">x.name</span></span>|<span data-ttu-id="e4a8a-286">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-286">4</span></span>|  
|<span data-ttu-id="e4a8a-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="e4a8a-287">Column</span></span>|@Column|<span data-ttu-id="e4a8a-288">c.name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-288">c.name</span></span>|<span data-ttu-id="e4a8a-289">5</span><span class="sxs-lookup"><span data-stu-id="e4a8a-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e4a8a-290">Dizinler</span><span class="sxs-lookup"><span data-stu-id="e4a8a-290">Indexes</span></span>  
  
|<span data-ttu-id="e4a8a-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-291">Restriction Name</span></span>|<span data-ttu-id="e4a8a-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-292">Parameter Name</span></span>|<span data-ttu-id="e4a8a-293">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-293">Restriction Default</span></span>|<span data-ttu-id="e4a8a-294">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-295">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-296">db_name ()</span><span class="sxs-lookup"><span data-stu-id="e4a8a-296">db_name()</span></span>|<span data-ttu-id="e4a8a-297">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-297">1</span></span>|  
|<span data-ttu-id="e4a8a-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-298">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-299">user_name ()</span><span class="sxs-lookup"><span data-stu-id="e4a8a-299">user_name()</span></span>|<span data-ttu-id="e4a8a-300">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-300">2</span></span>|  
|<span data-ttu-id="e4a8a-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-301">Table</span></span>|@Table|<span data-ttu-id="e4a8a-302">o.name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-302">o.name</span></span>|<span data-ttu-id="e4a8a-303">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="e4a8a-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e4a8a-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="e4a8a-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-305">Restriction Name</span></span>|<span data-ttu-id="e4a8a-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-306">Parameter Name</span></span>|<span data-ttu-id="e4a8a-307">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-307">Restriction Default</span></span>|<span data-ttu-id="e4a8a-308">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="e4a8a-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-310">assemblies.name</span></span>|<span data-ttu-id="e4a8a-311">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-311">1</span></span>|  
|<span data-ttu-id="e4a8a-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="e4a8a-312">udt_name</span></span>|@UDTName|<span data-ttu-id="e4a8a-313">türler. assembly_class</span><span class="sxs-lookup"><span data-stu-id="e4a8a-313">types.assembly_class</span></span>|<span data-ttu-id="e4a8a-314">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="e4a8a-315">Yabancıanahtarlar</span><span class="sxs-lookup"><span data-stu-id="e4a8a-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="e4a8a-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-316">Restriction Name</span></span>|<span data-ttu-id="e4a8a-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-317">Parameter Name</span></span>|<span data-ttu-id="e4a8a-318">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-318">Restriction Default</span></span>|<span data-ttu-id="e4a8a-319">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-320">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="e4a8a-322">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-322">1</span></span>|  
|<span data-ttu-id="e4a8a-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-323">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="e4a8a-325">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-325">2</span></span>|  
|<span data-ttu-id="e4a8a-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-326">Table</span></span>|@Table|<span data-ttu-id="e4a8a-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-327">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-328">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-328">3</span></span>|  
|<span data-ttu-id="e4a8a-329">Ad</span><span class="sxs-lookup"><span data-stu-id="e4a8a-329">Name</span></span>|@Name|<span data-ttu-id="e4a8a-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="e4a8a-331">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="e4a8a-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e4a8a-332">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="e4a8a-333">Aşağıdaki tablolarda SQL Server 2008 şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="e4a8a-334">Bu kısıtlamalar .NET Framework sürüm 3,5 SP1 ve 2008 SQL Server itibaren geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="e4a8a-335">.NET Framework ve SQL Server daha önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="e4a8a-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="e4a8a-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="e4a8a-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-337">Restriction Name</span></span>|<span data-ttu-id="e4a8a-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-338">Parameter Name</span></span>|<span data-ttu-id="e4a8a-339">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-339">Restriction Default</span></span>|<span data-ttu-id="e4a8a-340">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-341">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-342">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-343">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-343">1</span></span>|  
|<span data-ttu-id="e4a8a-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-344">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-346">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-346">2</span></span>|  
|<span data-ttu-id="e4a8a-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-347">Table</span></span>|@Table|<span data-ttu-id="e4a8a-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-348">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-349">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="e4a8a-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="e4a8a-350">AllColumns</span></span>  
  
|<span data-ttu-id="e4a8a-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-351">Restriction Name</span></span>|<span data-ttu-id="e4a8a-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-352">Parameter Name</span></span>|<span data-ttu-id="e4a8a-353">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e4a8a-353">Restriction Default</span></span>|<span data-ttu-id="e4a8a-354">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="e4a8a-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="e4a8a-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="e4a8a-355">Catalog</span></span>|@Catalog|<span data-ttu-id="e4a8a-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e4a8a-356">TABLE_CATALOG</span></span>|<span data-ttu-id="e4a8a-357">1</span><span class="sxs-lookup"><span data-stu-id="e4a8a-357">1</span></span>|  
|<span data-ttu-id="e4a8a-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="e4a8a-358">Owner</span></span>|@Owner|<span data-ttu-id="e4a8a-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e4a8a-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="e4a8a-360">2</span><span class="sxs-lookup"><span data-stu-id="e4a8a-360">2</span></span>|  
|<span data-ttu-id="e4a8a-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="e4a8a-361">Table</span></span>|@Table|<span data-ttu-id="e4a8a-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-362">TABLE_NAME</span></span>|<span data-ttu-id="e4a8a-363">3</span><span class="sxs-lookup"><span data-stu-id="e4a8a-363">3</span></span>|  
|<span data-ttu-id="e4a8a-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="e4a8a-364">Column</span></span>|@Column|<span data-ttu-id="e4a8a-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e4a8a-365">COLUMN_NAME</span></span>|<span data-ttu-id="e4a8a-366">4</span><span class="sxs-lookup"><span data-stu-id="e4a8a-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4a8a-367">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4a8a-367">See also</span></span>

- [<span data-ttu-id="e4a8a-368">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4a8a-368">ADO.NET Overview</span></span>](ado-net-overview.md)
