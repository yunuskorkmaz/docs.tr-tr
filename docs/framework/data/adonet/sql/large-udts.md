---
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148562"
---
# <a name="large-udts"></a><span data-ttu-id="561a0-102">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="561a0-102">Large UDTs</span></span>
<span data-ttu-id="561a0-103">Kullanıcı tanımlı türleri (UDT'ler), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skaler tür sistemini genişletmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="561a0-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="561a0-104">UDT'ler birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinin aksine davranışlar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="561a0-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="561a0-105">Büyük UDT'ler için geliştirilmiş SqlClient desteğinden yararlanmak için .NET Framework 3.5 SP1 (veya sonraki) yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="561a0-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="561a0-106">Daha önce, UDTs 8 kilobayt maksimum boyutu ile sınırlı idi.</span><span class="sxs-lookup"><span data-stu-id="561a0-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="561a0-107">SQL Server 2008'de, bu kısıtlama , <xref:Microsoft.SqlServer.Server.Format.UserDefined>biçimi ne olan UDT'ler için kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="561a0-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="561a0-108">Kullanıcı tanımlı türler için tam belgeler için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="561a0-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="561a0-109">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="561a0-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="561a0-110">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="561a0-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="561a0-111">GetSchema kullanarak UDT Şema alma</span><span class="sxs-lookup"><span data-stu-id="561a0-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="561a0-112">Veritabanı şema bilgilerini bir <xref:System.Data.DataTable>. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection></span><span class="sxs-lookup"><span data-stu-id="561a0-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="561a0-113">Daha fazla bilgi için [SQL Server Schema Collections'a](../sql-server-schema-collections.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="561a0-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="561a0-114">UD'ler için GetSchemaTable Sütun Değerleri</span><span class="sxs-lookup"><span data-stu-id="561a0-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="561a0-115">Sütun <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> meta <xref:System.Data.SqlClient.SqlDataReader> verilerini <xref:System.Data.DataTable> açıklayan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="561a0-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="561a0-116">Aşağıdaki tabloda, SQL Server 2005 ile SQL Server 2008 arasındaki büyük UDT'ler için sütun meta verilerindeki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="561a0-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="561a0-117">SqlDataReader sütunu</span><span class="sxs-lookup"><span data-stu-id="561a0-117">SqlDataReader column</span></span>|<span data-ttu-id="561a0-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="561a0-118">SQL Server 2005</span></span>|<span data-ttu-id="561a0-119">SQL Server 2008 ve sonrası</span><span class="sxs-lookup"><span data-stu-id="561a0-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="561a0-120">Değişir</span><span class="sxs-lookup"><span data-stu-id="561a0-120">Varies</span></span>|<span data-ttu-id="561a0-121">Değişir</span><span class="sxs-lookup"><span data-stu-id="561a0-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="561a0-122">255</span><span class="sxs-lookup"><span data-stu-id="561a0-122">255</span></span>|<span data-ttu-id="561a0-123">255</span><span class="sxs-lookup"><span data-stu-id="561a0-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="561a0-124">255</span><span class="sxs-lookup"><span data-stu-id="561a0-124">255</span></span>|<span data-ttu-id="561a0-125">255</span><span class="sxs-lookup"><span data-stu-id="561a0-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="561a0-126">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="561a0-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="561a0-127">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="561a0-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="561a0-128">21`SqlDbType.VarBinary`( ) ( )</span><span class="sxs-lookup"><span data-stu-id="561a0-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="561a0-129">29`SqlDbType.Udt`( ) ( )</span><span class="sxs-lookup"><span data-stu-id="561a0-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="561a0-130">29`SqlDbType.Udt`( ) ( )</span><span class="sxs-lookup"><span data-stu-id="561a0-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="561a0-131">29`SqlDbType.Udt`( ) ( )</span><span class="sxs-lookup"><span data-stu-id="561a0-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="561a0-132">*Database.SchemaName.TypeName*olarak belirtilen üç bölümadı.</span><span class="sxs-lookup"><span data-stu-id="561a0-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="561a0-133">Değişir</span><span class="sxs-lookup"><span data-stu-id="561a0-133">Varies</span></span>|<span data-ttu-id="561a0-134">Değişir</span><span class="sxs-lookup"><span data-stu-id="561a0-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="561a0-135">SqlDataReader Hususlar</span><span class="sxs-lookup"><span data-stu-id="561a0-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="561a0-136">Büyük <xref:System.Data.SqlClient.SqlDataReader> UDT değerlerinin alınmasını desteklemek için SQL Server 2008'den itibaren genişletildi.</span><span class="sxs-lookup"><span data-stu-id="561a0-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="561a0-137">UdT değerlerinin ne kadar <xref:System.Data.SqlClient.SqlDataReader> büyük bir değer tarafından işlendiği, kullandığınız SQL Server `Type System Version` sürümüne ve bağlantı dizesinde belirtilene bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="561a0-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="561a0-138">Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="561a0-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="561a0-139">SQL Server <xref:System.Data.SqlClient.SqlDataReader> 2005 olarak <xref:System.Data.SqlTypes.SqlBinary> ayarlandığında, `Type System Version` aşağıdaki yöntemler udt yerine bir döndürme yöntemi:</span><span class="sxs-lookup"><span data-stu-id="561a0-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="561a0-140">Aşağıdaki yöntemler, SQL Server `Byte[]` 2005 olarak `Type System Version` ayarlandığında UDT yerine bir dizi döndürecektir:</span><span class="sxs-lookup"><span data-stu-id="561a0-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="561a0-141">ADO.NET geçerli sürümü için dönüşüm yapılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="561a0-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="561a0-142">SqlParametrelerinin Belirtilmesi</span><span class="sxs-lookup"><span data-stu-id="561a0-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="561a0-143">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> özellikler büyük UDT'lerle çalışmak üzere genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="561a0-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="561a0-144">SqlParameter Özelliği</span><span class="sxs-lookup"><span data-stu-id="561a0-144">SqlParameter Property</span></span>|<span data-ttu-id="561a0-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="561a0-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="561a0-146">Parametrenin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="561a0-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="561a0-147">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="561a0-147">The default is null.</span></span> <span data-ttu-id="561a0-148">Özellik , `Byte[]` `SqlBinary`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="561a0-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="561a0-149">Parametrenin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="561a0-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="561a0-150">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="561a0-150">The default is null.</span></span> <span data-ttu-id="561a0-151">Özellik , `Byte[]` `SqlBinary`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="561a0-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="561a0-152">Çözülecek parametre değerinin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="561a0-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="561a0-153">Varsayılan değer 0’dır.</span><span class="sxs-lookup"><span data-stu-id="561a0-153">The default value is 0.</span></span> <span data-ttu-id="561a0-154">Özellik, parametre değerinin boyutunu temsil eden bir karşıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="561a0-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="561a0-155">Büyük UDT'ler için UDT'nin gerçek boyutu veya bilinmeyen için -1 olabilir.</span><span class="sxs-lookup"><span data-stu-id="561a0-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="561a0-156">Veri Alma Örneği</span><span class="sxs-lookup"><span data-stu-id="561a0-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="561a0-157">Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alındığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="561a0-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="561a0-158">Değişken, `connectionString` bir SQL Server veritabanına geçerli `commandString` bir bağlantı varsayar ve değişken ilk listelenen birincil anahtar sütunu ile geçerli bir SELECT deyimi varsayar.</span><span class="sxs-lookup"><span data-stu-id="561a0-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="561a0-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="561a0-159">See also</span></span>

- [<span data-ttu-id="561a0-160">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="561a0-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="561a0-161">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="561a0-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="561a0-162">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="561a0-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="561a0-163">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="561a0-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="561a0-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="561a0-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
