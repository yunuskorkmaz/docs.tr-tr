---
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 012bddc0b4c29a0b50abc3a0df5c3cd34dc4725a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452402"
---
# <a name="large-udts"></a><span data-ttu-id="06449-102">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="06449-102">Large UDTs</span></span>
<span data-ttu-id="06449-103">Kullanıcı tanımlı türler (UDTs), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skalar tür sistemini genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="06449-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="06449-104">UDTs birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinden farklı olarak davranışları olabilir.</span><span class="sxs-lookup"><span data-stu-id="06449-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06449-105">Büyük UDTs için gelişmiş SqlClient desteğinin avantajlarından yararlanabilmek için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="06449-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="06449-106">Daha önce, UDTs, 8 kilobayt olan en büyük boyutla sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="06449-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="06449-107">SQL Server 2008 ' de, bu kısıtlama <xref:Microsoft.SqlServer.Server.Format.UserDefined>biçiminde olan UDTs 'ler için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="06449-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="06449-108">Kullanıcı tanımlı türlerin tam belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="06449-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="06449-109">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="06449-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="06449-110">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="06449-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="06449-111">GetSchema kullanarak UDT şemaları alma</span><span class="sxs-lookup"><span data-stu-id="06449-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="06449-112"><xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> yöntemi, bir <xref:System.Data.DataTable>veritabanı şeması bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="06449-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="06449-113">Daha fazla bilgi için bkz. [SQL Server şema koleksiyonları](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="06449-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="06449-114">UDTs için GetSchemaTable sütun değerleri</span><span class="sxs-lookup"><span data-stu-id="06449-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="06449-115">Bir <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> yöntemi, sütun meta verilerini açıklayan bir <xref:System.Data.DataTable> döndürür.</span><span class="sxs-lookup"><span data-stu-id="06449-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="06449-116">Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasındaki büyük UDTs için sütun meta verilerindeki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06449-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="06449-117">SqlDataReader sütunu</span><span class="sxs-lookup"><span data-stu-id="06449-117">SqlDataReader column</span></span>|<span data-ttu-id="06449-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="06449-118">SQL Server 2005</span></span>|<span data-ttu-id="06449-119">SQL Server 2008 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="06449-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="06449-120">Değişir</span><span class="sxs-lookup"><span data-stu-id="06449-120">Varies</span></span>|<span data-ttu-id="06449-121">Değişir</span><span class="sxs-lookup"><span data-stu-id="06449-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="06449-122">255</span><span class="sxs-lookup"><span data-stu-id="06449-122">255</span></span>|<span data-ttu-id="06449-123">255</span><span class="sxs-lookup"><span data-stu-id="06449-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="06449-124">255</span><span class="sxs-lookup"><span data-stu-id="06449-124">255</span></span>|<span data-ttu-id="06449-125">255</span><span class="sxs-lookup"><span data-stu-id="06449-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="06449-126">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="06449-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="06449-127">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="06449-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="06449-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="06449-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="06449-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06449-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="06449-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06449-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="06449-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="06449-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="06449-132">*Database. SchemaName. TypeName*olarak belirtilen üç bölüm adı.</span><span class="sxs-lookup"><span data-stu-id="06449-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="06449-133">Değişir</span><span class="sxs-lookup"><span data-stu-id="06449-133">Varies</span></span>|<span data-ttu-id="06449-134">Değişir</span><span class="sxs-lookup"><span data-stu-id="06449-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="06449-135">SqlDataReader konuları</span><span class="sxs-lookup"><span data-stu-id="06449-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="06449-136">Büyük UDT değerlerini almayı desteklemek için <xref:System.Data.SqlClient.SqlDataReader> SQL Server 2008 ' den başlayarak genişletildi.</span><span class="sxs-lookup"><span data-stu-id="06449-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="06449-137">Büyük UDT değerlerinin bir <xref:System.Data.SqlClient.SqlDataReader> nasıl işlendiği, kullandığınız SQL Server sürümüne ve bağlantı dizesinde belirtilen `Type System Version` göre değişir.</span><span class="sxs-lookup"><span data-stu-id="06449-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="06449-138">Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="06449-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="06449-139">Aşağıdaki <xref:System.Data.SqlClient.SqlDataReader> yöntemleri, `Type System Version` SQL Server 2005 olarak ayarlandığında UDT yerine <xref:System.Data.SqlTypes.SqlBinary> döndürür:</span><span class="sxs-lookup"><span data-stu-id="06449-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="06449-140">Aşağıdaki yöntemler, `Type System Version` SQL Server 2005 olarak ayarlandığında UDT yerine bir `Byte[]` dizisi döndürür:</span><span class="sxs-lookup"><span data-stu-id="06449-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="06449-141">Geçerli ADO.NET sürümü için hiçbir dönüştürme yapılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06449-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="06449-142">SqlParameters belirtme</span><span class="sxs-lookup"><span data-stu-id="06449-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="06449-143">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> özellikleri, büyük UDTs ile çalışacak şekilde genişletildi.</span><span class="sxs-lookup"><span data-stu-id="06449-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="06449-144">SqlParameter özelliği</span><span class="sxs-lookup"><span data-stu-id="06449-144">SqlParameter Property</span></span>|<span data-ttu-id="06449-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06449-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="06449-146">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06449-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="06449-147">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="06449-147">The default is null.</span></span> <span data-ttu-id="06449-148">Özellik `SqlBinary`, `Byte[]`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="06449-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="06449-149">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06449-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="06449-150">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="06449-150">The default is null.</span></span> <span data-ttu-id="06449-151">Özellik `SqlBinary`, `Byte[]`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="06449-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="06449-152">Çözülecek parametre değerinin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06449-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="06449-153">Varsayılan değer 0’dır.</span><span class="sxs-lookup"><span data-stu-id="06449-153">The default value is 0.</span></span> <span data-ttu-id="06449-154">Özelliği parametre değerinin boyutunu temsil eden bir tamsayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="06449-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="06449-155">Büyük UDTs 'ler için, UDT 'nin gerçek boyutu veya bilinmeyen için-1 olabilir.</span><span class="sxs-lookup"><span data-stu-id="06449-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="06449-156">Veri alma örneği</span><span class="sxs-lookup"><span data-stu-id="06449-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="06449-157">Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06449-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="06449-158">`connectionString` değişkeni, SQL Server veritabanına geçerli bir bağlantı olduğunu varsayar ve `commandString` değişkeni önce listelenen birincil anahtar sütunuyla geçerli bir SELECT ifadesine sahip olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="06449-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="06449-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06449-159">See also</span></span>

- [<span data-ttu-id="06449-160">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="06449-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="06449-161">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="06449-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="06449-162">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="06449-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="06449-163">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="06449-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="06449-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06449-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
