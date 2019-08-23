---
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963171"
---
# <a name="schema-restrictions"></a><span data-ttu-id="3cc05-102">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3cc05-102">Schema Restrictions</span></span>
<span data-ttu-id="3cc05-103">**GetSchema** yönteminin ikinci isteğe bağlı parametresi döndürülen şema bilgisi miktarını sınırlamak için kullanılan kısıtlamalardır ve **GetSchema** yöntemine dizeler dizisi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="3cc05-104">Dizideki konum, geçirebileceğinizi belirten değerleri belirler ve bu, kısıtlama numarasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="3cc05-105">Örneğin, aşağıdaki tabloda SQL Server için .NET Framework Veri Sağlayıcısı kullanılarak "tablolar" şema koleksiyonu tarafından desteklenen kısıtlamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cc05-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="3cc05-106">SQL Server şema koleksiyonları için ek kısıtlamalar bu konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="3cc05-107">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-107">Restriction Name</span></span>|<span data-ttu-id="3cc05-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-108">Parameter Name</span></span>|<span data-ttu-id="3cc05-109">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-109">Restriction Default</span></span>|<span data-ttu-id="3cc05-110">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-111">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-112">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-113">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-113">1</span></span>|  
|<span data-ttu-id="3cc05-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-114">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-116">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-116">2</span></span>|  
|<span data-ttu-id="3cc05-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-117">Table</span></span>|@Name|<span data-ttu-id="3cc05-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-118">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-119">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-119">3</span></span>|  
|<span data-ttu-id="3cc05-120">TableType</span><span class="sxs-lookup"><span data-stu-id="3cc05-120">TableType</span></span>|@TableType|<span data-ttu-id="3cc05-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3cc05-121">TABLE_TYPE</span></span>|<span data-ttu-id="3cc05-122">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="3cc05-123">Kısıtlama değerlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="3cc05-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="3cc05-124">"Tables" şema koleksiyonu kısıtlamalarından birini kullanmak için, dört öğeli bir dize dizisi oluşturmanız yeterlidir, sonra bir değeri kısıtlama numarasıyla eşleşen bir değere yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cc05-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="3cc05-125">Örneğin, **GetSchema** yöntemi tarafından döndürülen tabloları yalnızca "Sales" şemasında bulunan tablolara kısıtlamak için, dizinin Ikinci öğesini **GetSchema** yöntemine geçirmeden önce "Sales" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3cc05-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cc05-126">İçin `SqlClient` kısıtlamalar koleksiyonları ve `OracleClient` ek `ParameterName` bir sütun vardır.</span><span class="sxs-lookup"><span data-stu-id="3cc05-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="3cc05-127">Kısıtlama varsayılan sütunu, geriye doğru uyumluluk için hala mevcuttur, ancak şu anda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="3cc05-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="3cc05-128">Kısıtlama değerlerini belirtirken bir SQL ekleme saldırısının riskini en aza indirmek için, dize değiştirme yerine parametreli sorgular kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3cc05-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cc05-129">Dizideki öğe sayısı, belirtilen şema koleksiyonu için desteklenen kısıtlama sayısına eşit veya ondan küçük olmalıdır, aksi takdirde bir <xref:System.ArgumentException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3cc05-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="3cc05-130">En yüksek kısıtlama sayısından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="3cc05-131">Eksik kısıtlamaların null (Kısıtlanmamış) olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3cc05-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="3cc05-132">"Kısıtlamalar" olan kısıtlama şeması koleksiyonu adı ile **GetSchema** yöntemini çağırarak desteklenen kısıtlamaların listesini öğrenmek için, .NET Framework yönetilen bir sağlayıcıyı sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cc05-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="3cc05-133">Bu, koleksiyon adlarının <xref:System.Data.DataTable> , kısıtlama adlarının, varsayılan kısıtlama değerlerinin ve kısıtlama numaralarının listesini içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cc05-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3cc05-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cc05-134">Example</span></span>  
 <span data-ttu-id="3cc05-135">Aşağıdaki örneklerde, **AdventureWorks** örnek veritabanında bulunan tüm <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> tablolar hakkında şema bilgilerini almak için SQL Server <xref:System.Data.SqlClient.SqlConnection> sınıfının .NET Framework veri sağlayıcısı yönteminin nasıl kullanılacağı gösterilmektedir. ve döndürülen bilgileri yalnızca "Sales" şemasında bulunan tablolara kısıtlamak için:</span><span class="sxs-lookup"><span data-stu-id="3cc05-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="3cc05-136">SQL Server şeması kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3cc05-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="3cc05-137">Aşağıdaki tablolarda SQL Server şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="3cc05-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="3cc05-138">Users</span></span>  
  
|<span data-ttu-id="3cc05-139">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-139">Restriction Name</span></span>|<span data-ttu-id="3cc05-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-140">Parameter Name</span></span>|<span data-ttu-id="3cc05-141">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-141">Restriction Default</span></span>|<span data-ttu-id="3cc05-142">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-143">Kullanıcı_adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-143">User_Name</span></span>|@Name|<span data-ttu-id="3cc05-144">name</span><span class="sxs-lookup"><span data-stu-id="3cc05-144">name</span></span>|<span data-ttu-id="3cc05-145">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="3cc05-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="3cc05-146">Databases</span></span>  
  
|<span data-ttu-id="3cc05-147">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-147">Restriction Name</span></span>|<span data-ttu-id="3cc05-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-148">Parameter Name</span></span>|<span data-ttu-id="3cc05-149">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-149">Restriction Default</span></span>|<span data-ttu-id="3cc05-150">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-151">Ad</span><span class="sxs-lookup"><span data-stu-id="3cc05-151">Name</span></span>|@Name|<span data-ttu-id="3cc05-152">Ad</span><span class="sxs-lookup"><span data-stu-id="3cc05-152">Name</span></span>|<span data-ttu-id="3cc05-153">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="3cc05-154">Takvimleri</span><span class="sxs-lookup"><span data-stu-id="3cc05-154">Tables</span></span>  
  
|<span data-ttu-id="3cc05-155">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-155">Restriction Name</span></span>|<span data-ttu-id="3cc05-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-156">Parameter Name</span></span>|<span data-ttu-id="3cc05-157">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-157">Restriction Default</span></span>|<span data-ttu-id="3cc05-158">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-159">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-160">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-161">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-161">1</span></span>|  
|<span data-ttu-id="3cc05-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-162">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-164">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-164">2</span></span>|  
|<span data-ttu-id="3cc05-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-165">Table</span></span>|@Name|<span data-ttu-id="3cc05-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-166">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-167">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-167">3</span></span>|  
|<span data-ttu-id="3cc05-168">TableType</span><span class="sxs-lookup"><span data-stu-id="3cc05-168">TableType</span></span>|@TableType|<span data-ttu-id="3cc05-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3cc05-169">TABLE_TYPE</span></span>|<span data-ttu-id="3cc05-170">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3cc05-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="3cc05-171">Columns</span></span>  
  
|<span data-ttu-id="3cc05-172">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-172">Restriction Name</span></span>|<span data-ttu-id="3cc05-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-173">Parameter Name</span></span>|<span data-ttu-id="3cc05-174">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-174">Restriction Default</span></span>|<span data-ttu-id="3cc05-175">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-176">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-177">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-178">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-178">1</span></span>|  
|<span data-ttu-id="3cc05-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-179">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-181">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-181">2</span></span>|  
|<span data-ttu-id="3cc05-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-182">Table</span></span>|@Table|<span data-ttu-id="3cc05-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-183">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-184">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-184">3</span></span>|  
|<span data-ttu-id="3cc05-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="3cc05-185">Column</span></span>|@Column|<span data-ttu-id="3cc05-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-186">COLUMN_NAME</span></span>|<span data-ttu-id="3cc05-187">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="3cc05-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="3cc05-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="3cc05-189">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-189">Restriction Name</span></span>|<span data-ttu-id="3cc05-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-190">Parameter Name</span></span>|<span data-ttu-id="3cc05-191">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-191">Restriction Default</span></span>|<span data-ttu-id="3cc05-192">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-193">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-194">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-195">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-195">1</span></span>|  
|<span data-ttu-id="3cc05-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-196">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-198">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-198">2</span></span>|  
|<span data-ttu-id="3cc05-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-199">Table</span></span>|@Table|<span data-ttu-id="3cc05-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-200">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-201">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-201">3</span></span>|  
|<span data-ttu-id="3cc05-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="3cc05-202">Column</span></span>|@Column|<span data-ttu-id="3cc05-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-203">COLUMN_NAME</span></span>|<span data-ttu-id="3cc05-204">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3cc05-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="3cc05-205">Views</span></span>  
  
|<span data-ttu-id="3cc05-206">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-206">Restriction Name</span></span>|<span data-ttu-id="3cc05-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-207">Parameter Name</span></span>|<span data-ttu-id="3cc05-208">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-208">Restriction Default</span></span>|<span data-ttu-id="3cc05-209">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-210">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-211">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-212">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-212">1</span></span>|  
|<span data-ttu-id="3cc05-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-213">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-215">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-215">2</span></span>|  
|<span data-ttu-id="3cc05-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-216">Table</span></span>|@Table|<span data-ttu-id="3cc05-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-217">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-218">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="3cc05-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="3cc05-219">ViewColumns</span></span>  
  
|<span data-ttu-id="3cc05-220">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-220">Restriction Name</span></span>|<span data-ttu-id="3cc05-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-221">Parameter Name</span></span>|<span data-ttu-id="3cc05-222">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-222">Restriction Default</span></span>|<span data-ttu-id="3cc05-223">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-224">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-225">VIEW_CATALOG</span></span>|<span data-ttu-id="3cc05-226">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-226">1</span></span>|  
|<span data-ttu-id="3cc05-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-227">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="3cc05-229">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-229">2</span></span>|  
|<span data-ttu-id="3cc05-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-230">Table</span></span>|@Table|<span data-ttu-id="3cc05-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-231">VIEW_NAME</span></span>|<span data-ttu-id="3cc05-232">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-232">3</span></span>|  
|<span data-ttu-id="3cc05-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="3cc05-233">Column</span></span>|@Column|<span data-ttu-id="3cc05-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-234">COLUMN_NAME</span></span>|<span data-ttu-id="3cc05-235">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3cc05-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3cc05-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3cc05-237">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-237">Restriction Name</span></span>|<span data-ttu-id="3cc05-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-238">Parameter Name</span></span>|<span data-ttu-id="3cc05-239">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-239">Restriction Default</span></span>|<span data-ttu-id="3cc05-240">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-241">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="3cc05-243">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-243">1</span></span>|  
|<span data-ttu-id="3cc05-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-244">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="3cc05-246">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-246">2</span></span>|  
|<span data-ttu-id="3cc05-247">Ad</span><span class="sxs-lookup"><span data-stu-id="3cc05-247">Name</span></span>|@Name|<span data-ttu-id="3cc05-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="3cc05-249">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-249">3</span></span>|  
|<span data-ttu-id="3cc05-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="3cc05-250">Parameter</span></span>|@Parameter|<span data-ttu-id="3cc05-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-251">PARAMETER_NAME</span></span>|<span data-ttu-id="3cc05-252">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3cc05-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3cc05-253">Procedures</span></span>  
  
|<span data-ttu-id="3cc05-254">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-254">Restriction Name</span></span>|<span data-ttu-id="3cc05-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-255">Parameter Name</span></span>|<span data-ttu-id="3cc05-256">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-256">Restriction Default</span></span>|<span data-ttu-id="3cc05-257">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-258">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="3cc05-260">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-260">1</span></span>|  
|<span data-ttu-id="3cc05-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-261">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="3cc05-263">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-263">2</span></span>|  
|<span data-ttu-id="3cc05-264">Ad</span><span class="sxs-lookup"><span data-stu-id="3cc05-264">Name</span></span>|@Name|<span data-ttu-id="3cc05-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="3cc05-266">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-266">3</span></span>|  
|<span data-ttu-id="3cc05-267">Tür</span><span class="sxs-lookup"><span data-stu-id="3cc05-267">Type</span></span>|@Type|<span data-ttu-id="3cc05-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3cc05-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="3cc05-269">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="3cc05-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="3cc05-270">IndexColumns</span></span>  
  
|<span data-ttu-id="3cc05-271">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-271">Restriction Name</span></span>|<span data-ttu-id="3cc05-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-272">Parameter Name</span></span>|<span data-ttu-id="3cc05-273">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-273">Restriction Default</span></span>|<span data-ttu-id="3cc05-274">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-275">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="3cc05-276">db_name()</span></span>|<span data-ttu-id="3cc05-277">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-277">1</span></span>|  
|<span data-ttu-id="3cc05-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-278">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-279">user_name ()</span><span class="sxs-lookup"><span data-stu-id="3cc05-279">user_name()</span></span>|<span data-ttu-id="3cc05-280">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-280">2</span></span>|  
|<span data-ttu-id="3cc05-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-281">Table</span></span>|@Table|<span data-ttu-id="3cc05-282">o.name</span><span class="sxs-lookup"><span data-stu-id="3cc05-282">o.name</span></span>|<span data-ttu-id="3cc05-283">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-283">3</span></span>|  
|<span data-ttu-id="3cc05-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="3cc05-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="3cc05-285">x.name</span><span class="sxs-lookup"><span data-stu-id="3cc05-285">x.name</span></span>|<span data-ttu-id="3cc05-286">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-286">4</span></span>|  
|<span data-ttu-id="3cc05-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="3cc05-287">Column</span></span>|@Column|<span data-ttu-id="3cc05-288">c.name</span><span class="sxs-lookup"><span data-stu-id="3cc05-288">c.name</span></span>|<span data-ttu-id="3cc05-289">5</span><span class="sxs-lookup"><span data-stu-id="3cc05-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3cc05-290">Dizinlerde</span><span class="sxs-lookup"><span data-stu-id="3cc05-290">Indexes</span></span>  
  
|<span data-ttu-id="3cc05-291">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-291">Restriction Name</span></span>|<span data-ttu-id="3cc05-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-292">Parameter Name</span></span>|<span data-ttu-id="3cc05-293">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-293">Restriction Default</span></span>|<span data-ttu-id="3cc05-294">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-295">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="3cc05-296">db_name()</span></span>|<span data-ttu-id="3cc05-297">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-297">1</span></span>|  
|<span data-ttu-id="3cc05-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-298">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-299">user_name ()</span><span class="sxs-lookup"><span data-stu-id="3cc05-299">user_name()</span></span>|<span data-ttu-id="3cc05-300">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-300">2</span></span>|  
|<span data-ttu-id="3cc05-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-301">Table</span></span>|@Table|<span data-ttu-id="3cc05-302">o.name</span><span class="sxs-lookup"><span data-stu-id="3cc05-302">o.name</span></span>|<span data-ttu-id="3cc05-303">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="3cc05-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="3cc05-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="3cc05-305">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-305">Restriction Name</span></span>|<span data-ttu-id="3cc05-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-306">Parameter Name</span></span>|<span data-ttu-id="3cc05-307">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-307">Restriction Default</span></span>|<span data-ttu-id="3cc05-308">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="3cc05-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="3cc05-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="3cc05-310">assemblies.name</span></span>|<span data-ttu-id="3cc05-311">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-311">1</span></span>|  
|<span data-ttu-id="3cc05-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="3cc05-312">udt_name</span></span>|@UDTName|<span data-ttu-id="3cc05-313">Types. assembly_class</span><span class="sxs-lookup"><span data-stu-id="3cc05-313">types.assembly_class</span></span>|<span data-ttu-id="3cc05-314">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="3cc05-315">Yabancıanahtarlar</span><span class="sxs-lookup"><span data-stu-id="3cc05-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="3cc05-316">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-316">Restriction Name</span></span>|<span data-ttu-id="3cc05-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-317">Parameter Name</span></span>|<span data-ttu-id="3cc05-318">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-318">Restriction Default</span></span>|<span data-ttu-id="3cc05-319">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-320">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="3cc05-322">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-322">1</span></span>|  
|<span data-ttu-id="3cc05-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-323">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="3cc05-325">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-325">2</span></span>|  
|<span data-ttu-id="3cc05-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-326">Table</span></span>|@Table|<span data-ttu-id="3cc05-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-327">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-328">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-328">3</span></span>|  
|<span data-ttu-id="3cc05-329">Ad</span><span class="sxs-lookup"><span data-stu-id="3cc05-329">Name</span></span>|@Name|<span data-ttu-id="3cc05-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="3cc05-331">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="3cc05-332">SQL Server 2008 şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3cc05-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="3cc05-333">Aşağıdaki tablolarda SQL Server 2008 şema koleksiyonları için kısıtlamalar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="3cc05-334">Bu kısıtlamalar .NET Framework sürüm 3,5 SP1 ve 2008 SQL Server itibaren geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3cc05-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="3cc05-335">.NET Framework ve SQL Server daha önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3cc05-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="3cc05-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="3cc05-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="3cc05-337">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-337">Restriction Name</span></span>|<span data-ttu-id="3cc05-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-338">Parameter Name</span></span>|<span data-ttu-id="3cc05-339">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-339">Restriction Default</span></span>|<span data-ttu-id="3cc05-340">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-341">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-342">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-343">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-343">1</span></span>|  
|<span data-ttu-id="3cc05-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-344">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-346">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-346">2</span></span>|  
|<span data-ttu-id="3cc05-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-347">Table</span></span>|@Table|<span data-ttu-id="3cc05-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-348">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-349">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="3cc05-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="3cc05-350">AllColumns</span></span>  
  
|<span data-ttu-id="3cc05-351">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-351">Restriction Name</span></span>|<span data-ttu-id="3cc05-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="3cc05-352">Parameter Name</span></span>|<span data-ttu-id="3cc05-353">Kısıtlama varsayılanı</span><span class="sxs-lookup"><span data-stu-id="3cc05-353">Restriction Default</span></span>|<span data-ttu-id="3cc05-354">Kısıtlama numarası</span><span class="sxs-lookup"><span data-stu-id="3cc05-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="3cc05-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="3cc05-355">Catalog</span></span>|@Catalog|<span data-ttu-id="3cc05-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3cc05-356">TABLE_CATALOG</span></span>|<span data-ttu-id="3cc05-357">1\.</span><span class="sxs-lookup"><span data-stu-id="3cc05-357">1</span></span>|  
|<span data-ttu-id="3cc05-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="3cc05-358">Owner</span></span>|@Owner|<span data-ttu-id="3cc05-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3cc05-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="3cc05-360">2</span><span class="sxs-lookup"><span data-stu-id="3cc05-360">2</span></span>|  
|<span data-ttu-id="3cc05-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="3cc05-361">Table</span></span>|@Table|<span data-ttu-id="3cc05-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-362">TABLE_NAME</span></span>|<span data-ttu-id="3cc05-363">3</span><span class="sxs-lookup"><span data-stu-id="3cc05-363">3</span></span>|  
|<span data-ttu-id="3cc05-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="3cc05-364">Column</span></span>|@Column|<span data-ttu-id="3cc05-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3cc05-365">COLUMN_NAME</span></span>|<span data-ttu-id="3cc05-366">4</span><span class="sxs-lookup"><span data-stu-id="3cc05-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cc05-367">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cc05-367">See also</span></span>

- [<span data-ttu-id="3cc05-368">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3cc05-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
