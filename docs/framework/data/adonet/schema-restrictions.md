---
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149017"
---
# <a name="schema-restrictions"></a><span data-ttu-id="4bb62-102">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="4bb62-102">Schema Restrictions</span></span>
<span data-ttu-id="4bb62-103">**GetSchema** yönteminin ikinci isteğe bağlı parametresi, döndürülen şema bilgi miktarını sınırlamak için kullanılan kısıtlamalardır ve bir dizi dize olarak **GetSchema** yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="4bb62-104">Dizideki konum geçebileceğiniz değerleri belirler ve bu kısıtlama numarasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="4bb62-105">Örneğin, aşağıdaki tabloda SQL Server için .NET Framework Data Provider kullanarak "Tablolar" şema koleksiyonu tarafından desteklenen kısıtlamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4bb62-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="4bb62-106">Bu konunun sonunda SQL Server şema koleksiyonları için ek kısıtlamalar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="4bb62-107">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-107">Restriction Name</span></span>|<span data-ttu-id="4bb62-108">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-108">Parameter Name</span></span>|<span data-ttu-id="4bb62-109">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-109">Restriction Default</span></span>|<span data-ttu-id="4bb62-110">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-111">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-111">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-112">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-113">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-113">1</span></span>|  
|<span data-ttu-id="4bb62-114">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-114">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-116">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-116">2</span></span>|  
|<span data-ttu-id="4bb62-117">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-117">Table</span></span>|@Name|<span data-ttu-id="4bb62-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-118">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-119">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-119">3</span></span>|  
|<span data-ttu-id="4bb62-120">Tablo Tipi</span><span class="sxs-lookup"><span data-stu-id="4bb62-120">TableType</span></span>|@TableType|<span data-ttu-id="4bb62-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4bb62-121">TABLE_TYPE</span></span>|<span data-ttu-id="4bb62-122">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="4bb62-123">Kısıtlama Değerlerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="4bb62-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="4bb62-124">"Tablolar" şema koleksiyonunun kısıtlamalarından birini kullanmak için, dört öğeli bir dizi dize oluşturmanız ve ardından kısıtlama numarasıyla eşleşen öğeye bir değer yerleştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="4bb62-125">Örneğin, **GetSchema** yöntemi tarafından döndürülen tabloları yalnızca "Satış" şemasındaki tablolarla sınırlamak için, dizinin ikinci öğesini **GetSchema** yöntemine geçirmeden önce "Satışlar" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4bb62-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bb62-126">Kısıtlamalar için `SqlClient` koleksiyonlar `OracleClient` ve `ParameterName` ek bir sütun var.</span><span class="sxs-lookup"><span data-stu-id="4bb62-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="4bb62-127">Kısıtlama varsayılan sütunu geriye dönük uyumluluk için hala oradadır, ancak şu anda yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4bb62-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="4bb62-128">Kısıtlama değerleri belirtilirken bir SQL enjeksiyon atağı riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb62-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bb62-129">Dizideki öğe sayısı, belirtilen şema koleksiyonu <xref:System.ArgumentException> için desteklenen kısıtlama sayısından daha az veya eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb62-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="4bb62-130">Maksimum kısıtlama sayısından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="4bb62-131">Eksik kısıtlamaların geçersiz (sınırsız) olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4bb62-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="4bb62-132">**GetSchema** yöntemini "Kısıtlamalar" olan schema koleksiyonunun adı ile arayarak desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcıyı sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bb62-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="4bb62-133">Bu, koleksiyon <xref:System.Data.DataTable> adlarının, kısıtlama adlarının, varsayılan kısıtlama değerlerinin ve kısıtlama numaralarının bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bb62-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4bb62-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bb62-134">Example</span></span>  
 <span data-ttu-id="4bb62-135">Aşağıdaki örnekler, **AdventureWorks** <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> örnek veritabanında yer alan tüm tablolar <xref:System.Data.SqlClient.SqlConnection> hakkında şema bilgilerini almak ve yalnızca "Satış" şemasındaki tablolara döndürülen bilgileri kısıtlamak için SQL Server sınıfı için .NET Framework Data Provider yönteminin nasıl kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="4bb62-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="4bb62-136">SQL Server Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="4bb62-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="4bb62-137">Aşağıdaki tablolarda SQL Server şema koleksiyonlarının kısıtlamaları listeleneb.r</span><span class="sxs-lookup"><span data-stu-id="4bb62-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="4bb62-138">Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="4bb62-138">Users</span></span>  
  
|<span data-ttu-id="4bb62-139">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-139">Restriction Name</span></span>|<span data-ttu-id="4bb62-140">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-140">Parameter Name</span></span>|<span data-ttu-id="4bb62-141">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-141">Restriction Default</span></span>|<span data-ttu-id="4bb62-142">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-143">Kullanıcı_adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-143">User_Name</span></span>|@Name|<span data-ttu-id="4bb62-144">ad</span><span class="sxs-lookup"><span data-stu-id="4bb62-144">name</span></span>|<span data-ttu-id="4bb62-145">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="4bb62-146">Veritabanları</span><span class="sxs-lookup"><span data-stu-id="4bb62-146">Databases</span></span>  
  
|<span data-ttu-id="4bb62-147">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-147">Restriction Name</span></span>|<span data-ttu-id="4bb62-148">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-148">Parameter Name</span></span>|<span data-ttu-id="4bb62-149">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-149">Restriction Default</span></span>|<span data-ttu-id="4bb62-150">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-151">Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-151">Name</span></span>|@Name|<span data-ttu-id="4bb62-152">Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-152">Name</span></span>|<span data-ttu-id="4bb62-153">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="4bb62-154">Tablolar</span><span class="sxs-lookup"><span data-stu-id="4bb62-154">Tables</span></span>  
  
|<span data-ttu-id="4bb62-155">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-155">Restriction Name</span></span>|<span data-ttu-id="4bb62-156">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-156">Parameter Name</span></span>|<span data-ttu-id="4bb62-157">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-157">Restriction Default</span></span>|<span data-ttu-id="4bb62-158">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-159">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-160">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-161">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-161">1</span></span>|  
|<span data-ttu-id="4bb62-162">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-162">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-164">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-164">2</span></span>|  
|<span data-ttu-id="4bb62-165">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-165">Table</span></span>|@Name|<span data-ttu-id="4bb62-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-166">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-167">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-167">3</span></span>|  
|<span data-ttu-id="4bb62-168">Tablo Tipi</span><span class="sxs-lookup"><span data-stu-id="4bb62-168">TableType</span></span>|@TableType|<span data-ttu-id="4bb62-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4bb62-169">TABLE_TYPE</span></span>|<span data-ttu-id="4bb62-170">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4bb62-171">Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4bb62-171">Columns</span></span>  
  
|<span data-ttu-id="4bb62-172">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-172">Restriction Name</span></span>|<span data-ttu-id="4bb62-173">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-173">Parameter Name</span></span>|<span data-ttu-id="4bb62-174">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-174">Restriction Default</span></span>|<span data-ttu-id="4bb62-175">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-176">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-176">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-177">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-178">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-178">1</span></span>|  
|<span data-ttu-id="4bb62-179">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-179">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-181">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-181">2</span></span>|  
|<span data-ttu-id="4bb62-182">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-182">Table</span></span>|@Table|<span data-ttu-id="4bb62-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-183">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-184">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-184">3</span></span>|  
|<span data-ttu-id="4bb62-185">Sütun</span><span class="sxs-lookup"><span data-stu-id="4bb62-185">Column</span></span>|@Column|<span data-ttu-id="4bb62-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-186">COLUMN_NAME</span></span>|<span data-ttu-id="4bb62-187">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="4bb62-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="4bb62-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="4bb62-189">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-189">Restriction Name</span></span>|<span data-ttu-id="4bb62-190">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-190">Parameter Name</span></span>|<span data-ttu-id="4bb62-191">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-191">Restriction Default</span></span>|<span data-ttu-id="4bb62-192">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-193">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-193">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-194">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-195">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-195">1</span></span>|  
|<span data-ttu-id="4bb62-196">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-196">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-198">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-198">2</span></span>|  
|<span data-ttu-id="4bb62-199">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-199">Table</span></span>|@Table|<span data-ttu-id="4bb62-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-200">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-201">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-201">3</span></span>|  
|<span data-ttu-id="4bb62-202">Sütun</span><span class="sxs-lookup"><span data-stu-id="4bb62-202">Column</span></span>|@Column|<span data-ttu-id="4bb62-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-203">COLUMN_NAME</span></span>|<span data-ttu-id="4bb62-204">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="4bb62-205">Görünümler</span><span class="sxs-lookup"><span data-stu-id="4bb62-205">Views</span></span>  
  
|<span data-ttu-id="4bb62-206">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-206">Restriction Name</span></span>|<span data-ttu-id="4bb62-207">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-207">Parameter Name</span></span>|<span data-ttu-id="4bb62-208">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-208">Restriction Default</span></span>|<span data-ttu-id="4bb62-209">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-210">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-210">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-211">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-212">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-212">1</span></span>|  
|<span data-ttu-id="4bb62-213">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-213">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-215">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-215">2</span></span>|  
|<span data-ttu-id="4bb62-216">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-216">Table</span></span>|@Table|<span data-ttu-id="4bb62-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-217">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-218">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="4bb62-219">Sütunları Görüntüle</span><span class="sxs-lookup"><span data-stu-id="4bb62-219">ViewColumns</span></span>  
  
|<span data-ttu-id="4bb62-220">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-220">Restriction Name</span></span>|<span data-ttu-id="4bb62-221">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-221">Parameter Name</span></span>|<span data-ttu-id="4bb62-222">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-222">Restriction Default</span></span>|<span data-ttu-id="4bb62-223">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-224">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-224">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-225">VIEW_CATALOG</span></span>|<span data-ttu-id="4bb62-226">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-226">1</span></span>|  
|<span data-ttu-id="4bb62-227">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-227">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="4bb62-229">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-229">2</span></span>|  
|<span data-ttu-id="4bb62-230">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-230">Table</span></span>|@Table|<span data-ttu-id="4bb62-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-231">VIEW_NAME</span></span>|<span data-ttu-id="4bb62-232">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-232">3</span></span>|  
|<span data-ttu-id="4bb62-233">Sütun</span><span class="sxs-lookup"><span data-stu-id="4bb62-233">Column</span></span>|@Column|<span data-ttu-id="4bb62-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-234">COLUMN_NAME</span></span>|<span data-ttu-id="4bb62-235">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="4bb62-236">Prosedür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="4bb62-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="4bb62-237">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-237">Restriction Name</span></span>|<span data-ttu-id="4bb62-238">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-238">Parameter Name</span></span>|<span data-ttu-id="4bb62-239">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-239">Restriction Default</span></span>|<span data-ttu-id="4bb62-240">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-241">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-241">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="4bb62-243">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-243">1</span></span>|  
|<span data-ttu-id="4bb62-244">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-244">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="4bb62-246">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-246">2</span></span>|  
|<span data-ttu-id="4bb62-247">Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-247">Name</span></span>|@Name|<span data-ttu-id="4bb62-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="4bb62-249">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-249">3</span></span>|  
|<span data-ttu-id="4bb62-250">Parametre</span><span class="sxs-lookup"><span data-stu-id="4bb62-250">Parameter</span></span>|@Parameter|<span data-ttu-id="4bb62-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-251">PARAMETER_NAME</span></span>|<span data-ttu-id="4bb62-252">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4bb62-253">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4bb62-253">Procedures</span></span>  
  
|<span data-ttu-id="4bb62-254">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-254">Restriction Name</span></span>|<span data-ttu-id="4bb62-255">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-255">Parameter Name</span></span>|<span data-ttu-id="4bb62-256">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-256">Restriction Default</span></span>|<span data-ttu-id="4bb62-257">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-258">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="4bb62-260">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-260">1</span></span>|  
|<span data-ttu-id="4bb62-261">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-261">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="4bb62-263">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-263">2</span></span>|  
|<span data-ttu-id="4bb62-264">Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-264">Name</span></span>|@Name|<span data-ttu-id="4bb62-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="4bb62-266">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-266">3</span></span>|  
|<span data-ttu-id="4bb62-267">Tür</span><span class="sxs-lookup"><span data-stu-id="4bb62-267">Type</span></span>|@Type|<span data-ttu-id="4bb62-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4bb62-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="4bb62-269">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="4bb62-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="4bb62-270">IndexColumns</span></span>  
  
|<span data-ttu-id="4bb62-271">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-271">Restriction Name</span></span>|<span data-ttu-id="4bb62-272">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-272">Parameter Name</span></span>|<span data-ttu-id="4bb62-273">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-273">Restriction Default</span></span>|<span data-ttu-id="4bb62-274">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-275">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-275">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="4bb62-276">db_name()</span></span>|<span data-ttu-id="4bb62-277">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-277">1</span></span>|  
|<span data-ttu-id="4bb62-278">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-278">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="4bb62-279">user_name()</span></span>|<span data-ttu-id="4bb62-280">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-280">2</span></span>|  
|<span data-ttu-id="4bb62-281">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-281">Table</span></span>|@Table|<span data-ttu-id="4bb62-282">o.name</span><span class="sxs-lookup"><span data-stu-id="4bb62-282">o.name</span></span>|<span data-ttu-id="4bb62-283">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-283">3</span></span>|  
|<span data-ttu-id="4bb62-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="4bb62-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="4bb62-285">x.name</span><span class="sxs-lookup"><span data-stu-id="4bb62-285">x.name</span></span>|<span data-ttu-id="4bb62-286">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-286">4</span></span>|  
|<span data-ttu-id="4bb62-287">Sütun</span><span class="sxs-lookup"><span data-stu-id="4bb62-287">Column</span></span>|@Column|<span data-ttu-id="4bb62-288">c.name</span><span class="sxs-lookup"><span data-stu-id="4bb62-288">c.name</span></span>|<span data-ttu-id="4bb62-289">5</span><span class="sxs-lookup"><span data-stu-id="4bb62-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4bb62-290">Dizinler</span><span class="sxs-lookup"><span data-stu-id="4bb62-290">Indexes</span></span>  
  
|<span data-ttu-id="4bb62-291">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-291">Restriction Name</span></span>|<span data-ttu-id="4bb62-292">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-292">Parameter Name</span></span>|<span data-ttu-id="4bb62-293">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-293">Restriction Default</span></span>|<span data-ttu-id="4bb62-294">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-295">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-295">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="4bb62-296">db_name()</span></span>|<span data-ttu-id="4bb62-297">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-297">1</span></span>|  
|<span data-ttu-id="4bb62-298">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-298">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="4bb62-299">user_name()</span></span>|<span data-ttu-id="4bb62-300">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-300">2</span></span>|  
|<span data-ttu-id="4bb62-301">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-301">Table</span></span>|@Table|<span data-ttu-id="4bb62-302">o.name</span><span class="sxs-lookup"><span data-stu-id="4bb62-302">o.name</span></span>|<span data-ttu-id="4bb62-303">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="4bb62-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="4bb62-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="4bb62-305">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-305">Restriction Name</span></span>|<span data-ttu-id="4bb62-306">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-306">Parameter Name</span></span>|<span data-ttu-id="4bb62-307">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-307">Restriction Default</span></span>|<span data-ttu-id="4bb62-308">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-309">Assembly_name</span><span class="sxs-lookup"><span data-stu-id="4bb62-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="4bb62-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="4bb62-310">assemblies.name</span></span>|<span data-ttu-id="4bb62-311">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-311">1</span></span>|  
|<span data-ttu-id="4bb62-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="4bb62-312">udt_name</span></span>|@UDTName|<span data-ttu-id="4bb62-313">türleri.assembly_class</span><span class="sxs-lookup"><span data-stu-id="4bb62-313">types.assembly_class</span></span>|<span data-ttu-id="4bb62-314">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="4bb62-315">Yabancı Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="4bb62-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="4bb62-316">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-316">Restriction Name</span></span>|<span data-ttu-id="4bb62-317">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-317">Parameter Name</span></span>|<span data-ttu-id="4bb62-318">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-318">Restriction Default</span></span>|<span data-ttu-id="4bb62-319">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-320">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-320">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="4bb62-322">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-322">1</span></span>|  
|<span data-ttu-id="4bb62-323">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-323">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="4bb62-325">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-325">2</span></span>|  
|<span data-ttu-id="4bb62-326">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-326">Table</span></span>|@Table|<span data-ttu-id="4bb62-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-327">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-328">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-328">3</span></span>|  
|<span data-ttu-id="4bb62-329">Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-329">Name</span></span>|@Name|<span data-ttu-id="4bb62-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="4bb62-331">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="4bb62-332">SQL Server 2008 Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="4bb62-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="4bb62-333">Aşağıdaki tablolarda SQL Server 2008 şema koleksiyonlarının kısıtlamaları listeleneb.)'de.</span><span class="sxs-lookup"><span data-stu-id="4bb62-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="4bb62-334">Bu kısıtlamalar ,NET Framework ve SQL Server 2008 sürümü 3.5 SP1 ile başlayan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4bb62-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="4bb62-335">.NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4bb62-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="4bb62-336">SütunSeti Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4bb62-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="4bb62-337">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-337">Restriction Name</span></span>|<span data-ttu-id="4bb62-338">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-338">Parameter Name</span></span>|<span data-ttu-id="4bb62-339">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-339">Restriction Default</span></span>|<span data-ttu-id="4bb62-340">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-341">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-341">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-342">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-343">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-343">1</span></span>|  
|<span data-ttu-id="4bb62-344">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-344">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-346">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-346">2</span></span>|  
|<span data-ttu-id="4bb62-347">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-347">Table</span></span>|@Table|<span data-ttu-id="4bb62-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-348">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-349">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="4bb62-350">Tüm Sütunlar</span><span class="sxs-lookup"><span data-stu-id="4bb62-350">AllColumns</span></span>  
  
|<span data-ttu-id="4bb62-351">Kısıtlama Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-351">Restriction Name</span></span>|<span data-ttu-id="4bb62-352">Parametre Adı</span><span class="sxs-lookup"><span data-stu-id="4bb62-352">Parameter Name</span></span>|<span data-ttu-id="4bb62-353">Kısıtlama Varsayılan</span><span class="sxs-lookup"><span data-stu-id="4bb62-353">Restriction Default</span></span>|<span data-ttu-id="4bb62-354">Kısıtlama Numarası</span><span class="sxs-lookup"><span data-stu-id="4bb62-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4bb62-355">Katalog</span><span class="sxs-lookup"><span data-stu-id="4bb62-355">Catalog</span></span>|@Catalog|<span data-ttu-id="4bb62-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4bb62-356">TABLE_CATALOG</span></span>|<span data-ttu-id="4bb62-357">1</span><span class="sxs-lookup"><span data-stu-id="4bb62-357">1</span></span>|  
|<span data-ttu-id="4bb62-358">Sahip</span><span class="sxs-lookup"><span data-stu-id="4bb62-358">Owner</span></span>|@Owner|<span data-ttu-id="4bb62-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4bb62-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="4bb62-360">2</span><span class="sxs-lookup"><span data-stu-id="4bb62-360">2</span></span>|  
|<span data-ttu-id="4bb62-361">Tablo</span><span class="sxs-lookup"><span data-stu-id="4bb62-361">Table</span></span>|@Table|<span data-ttu-id="4bb62-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-362">TABLE_NAME</span></span>|<span data-ttu-id="4bb62-363">3</span><span class="sxs-lookup"><span data-stu-id="4bb62-363">3</span></span>|  
|<span data-ttu-id="4bb62-364">Sütun</span><span class="sxs-lookup"><span data-stu-id="4bb62-364">Column</span></span>|@Column|<span data-ttu-id="4bb62-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4bb62-365">COLUMN_NAME</span></span>|<span data-ttu-id="4bb62-366">4</span><span class="sxs-lookup"><span data-stu-id="4bb62-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bb62-367">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bb62-367">See also</span></span>

- [<span data-ttu-id="4bb62-368">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4bb62-368">ADO.NET Overview</span></span>](ado-net-overview.md)
