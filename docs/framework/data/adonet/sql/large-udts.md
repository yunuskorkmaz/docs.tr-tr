---
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 33f4263c747ac2590234493ec7cb9e6048ed2b96
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794019"
---
# <a name="large-udts"></a><span data-ttu-id="3b896-102">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="3b896-102">Large UDTs</span></span>
<span data-ttu-id="3b896-103">Kullanıcı tanımlı türler (UDTs), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skalar tür sistemini genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b896-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="3b896-104">UDTs birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinden farklı olarak davranışları olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b896-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b896-105">Büyük UDTs için gelişmiş SqlClient desteğinin avantajlarından yararlanabilmek için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3b896-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="3b896-106">Daha önce, UDTs, 8 kilobayt olan en büyük boyutla sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3b896-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="3b896-107">SQL Server 2008 ' de, bu kısıtlama biçiminde <xref:Microsoft.SqlServer.Server.Format.UserDefined>olan UDTs 'ler için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3b896-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="3b896-108">Kullanıcı tanımlı türlerin tam belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b896-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="3b896-109">**Books Online SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3b896-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="3b896-110">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="3b896-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="3b896-111">GetSchema kullanarak UDT şemaları alma</span><span class="sxs-lookup"><span data-stu-id="3b896-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="3b896-112">Yöntemi, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> içindeki veritabanışemasıbilgilerinidöndürür.<xref:System.Data.DataTable> <xref:System.Data.SqlClient.SqlConnection></span><span class="sxs-lookup"><span data-stu-id="3b896-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3b896-113">Daha fazla bilgi için bkz. [SQL Server şema koleksiyonları](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="3b896-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="3b896-114">UDTs için GetSchemaTable sütun değerleri</span><span class="sxs-lookup"><span data-stu-id="3b896-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="3b896-115"><xref:System.Data.DataTable> Bir <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> öğesininyöntemi,sütunmetaverilerini<xref:System.Data.SqlClient.SqlDataReader> açıklayan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b896-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="3b896-116">Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasındaki büyük UDTs için sütun meta verilerindeki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b896-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="3b896-117">SqlDataReader sütunu</span><span class="sxs-lookup"><span data-stu-id="3b896-117">SqlDataReader column</span></span>|<span data-ttu-id="3b896-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="3b896-118">SQL Server 2005</span></span>|<span data-ttu-id="3b896-119">SQL Server 2008 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="3b896-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="3b896-120">Varies</span><span class="sxs-lookup"><span data-stu-id="3b896-120">Varies</span></span>|<span data-ttu-id="3b896-121">Varies</span><span class="sxs-lookup"><span data-stu-id="3b896-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="3b896-122">255</span><span class="sxs-lookup"><span data-stu-id="3b896-122">255</span></span>|<span data-ttu-id="3b896-123">255</span><span class="sxs-lookup"><span data-stu-id="3b896-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="3b896-124">255</span><span class="sxs-lookup"><span data-stu-id="3b896-124">255</span></span>|<span data-ttu-id="3b896-125">255</span><span class="sxs-lookup"><span data-stu-id="3b896-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="3b896-126">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="3b896-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="3b896-127">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="3b896-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="3b896-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="3b896-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="3b896-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3b896-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="3b896-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3b896-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="3b896-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="3b896-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="3b896-132">*Database. SchemaName. TypeName*olarak belirtilen üç bölüm adı.</span><span class="sxs-lookup"><span data-stu-id="3b896-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="3b896-133">Varies</span><span class="sxs-lookup"><span data-stu-id="3b896-133">Varies</span></span>|<span data-ttu-id="3b896-134">Varies</span><span class="sxs-lookup"><span data-stu-id="3b896-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="3b896-135">SqlDataReader konuları</span><span class="sxs-lookup"><span data-stu-id="3b896-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="3b896-136">, <xref:System.Data.SqlClient.SqlDataReader> Büyük udt değerlerini almayı desteklemek için SQL Server 2008 ' den başlayarak genişletildi.</span><span class="sxs-lookup"><span data-stu-id="3b896-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="3b896-137">Büyük udt değerlerinin bir <xref:System.Data.SqlClient.SqlDataReader> tarafından nasıl işlendiği, kullandığınız SQL Server sürümüne ve ayrıca `Type System Version` bağlantı dizesinde belirtilen sürüme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b896-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="3b896-138">Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b896-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="3b896-139">Aşağıdaki yöntemleri <xref:System.Data.SqlClient.SqlDataReader> , <xref:System.Data.SqlTypes.SqlBinary> SQLServer2005olarakayarlandığındaudtyerine`Type System Version` bir udt döndürür:</span><span class="sxs-lookup"><span data-stu-id="3b896-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="3b896-140">Aşağıdaki yöntemler, `Type System Version` SQL Server 2005 olarak ayarlandığında bir `Byte[]` udt yerine bir dizisi döndürür:</span><span class="sxs-lookup"><span data-stu-id="3b896-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="3b896-141">Geçerli ADO.NET sürümü için hiçbir dönüştürme yapılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b896-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="3b896-142">SqlParameters belirtme</span><span class="sxs-lookup"><span data-stu-id="3b896-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="3b896-143">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> özellikler, büyük UDTs ile çalışacak şekilde genişletildi.</span><span class="sxs-lookup"><span data-stu-id="3b896-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="3b896-144">SqlParameter özelliği</span><span class="sxs-lookup"><span data-stu-id="3b896-144">SqlParameter Property</span></span>|<span data-ttu-id="3b896-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b896-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="3b896-146">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b896-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="3b896-147">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="3b896-147">The default is null.</span></span> <span data-ttu-id="3b896-148">Özelliği `SqlBinary` ,`Byte[]`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b896-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="3b896-149">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b896-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="3b896-150">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="3b896-150">The default is null.</span></span> <span data-ttu-id="3b896-151">Özelliği `SqlBinary` ,`Byte[]`veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b896-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="3b896-152">Çözülecek parametre değerinin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b896-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="3b896-153">Varsayılan değer 0’dır.</span><span class="sxs-lookup"><span data-stu-id="3b896-153">The default value is 0.</span></span> <span data-ttu-id="3b896-154">Özelliği parametre değerinin boyutunu temsil eden bir tamsayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b896-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="3b896-155">Büyük UDTs 'ler için, UDT 'nin gerçek boyutu veya bilinmeyen için-1 olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b896-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="3b896-156">Veri alma örneği</span><span class="sxs-lookup"><span data-stu-id="3b896-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="3b896-157">Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b896-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="3b896-158">Değişken `connectionString` , SQL Server veritabanına geçerli bir bağlantı olduğunu varsayar `commandString` ve değişken önce listelenen birincil anahtar sütunu ile geçerli bir SELECT ifadesini varsayar.</span><span class="sxs-lookup"><span data-stu-id="3b896-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b896-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b896-159">See also</span></span>

- [<span data-ttu-id="3b896-160">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3b896-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="3b896-161">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="3b896-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="3b896-162">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="3b896-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="3b896-163">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="3b896-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="3b896-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b896-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
