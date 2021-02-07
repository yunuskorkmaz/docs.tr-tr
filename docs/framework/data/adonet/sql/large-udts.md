---
description: 'Daha fazla bilgi edinin: büyük UDTs'
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: e1a40330bb48d6320dc96533e764f1b856e0f410
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663189"
---
# <a name="large-udts"></a><span data-ttu-id="565b7-103">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="565b7-103">Large UDTs</span></span>

<span data-ttu-id="565b7-104">Kullanıcı tanımlı türler (UDTs), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skalar tür sistemini genişletmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="565b7-104">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="565b7-105">UDTs birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinden farklı olarak davranışları olabilir.</span><span class="sxs-lookup"><span data-stu-id="565b7-105">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="565b7-106">Büyük UDTs için gelişmiş SqlClient desteğinin avantajlarından yararlanabilmek için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="565b7-106">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="565b7-107">Daha önce, UDTs, 8 kilobayt olan en büyük boyutla sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="565b7-107">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="565b7-108">SQL Server 2008 ' de, bu kısıtlama biçiminde olan UDTs 'ler için kaldırılmıştır <xref:Microsoft.SqlServer.Server.Format.UserDefined> .</span><span class="sxs-lookup"><span data-stu-id="565b7-108">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="565b7-109">Kullanıcı tanımlı türlerin tam belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="565b7-109">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="565b7-110">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="565b7-110">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="565b7-111">Kullanıcı Tanımlı CLR Türleri</span><span class="sxs-lookup"><span data-stu-id="565b7-111">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="565b7-112">GetSchema kullanarak UDT şemaları alma</span><span class="sxs-lookup"><span data-stu-id="565b7-112">Retrieving UDT Schemas Using GetSchema</span></span>  

 <span data-ttu-id="565b7-113"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>Yöntemi, <xref:System.Data.SqlClient.SqlConnection> içindeki veritabanı şeması bilgilerini döndürür <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="565b7-113">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="565b7-114">Daha fazla bilgi için bkz. [SQL Server şema koleksiyonları](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="565b7-114">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="565b7-115">UDTs için GetSchemaTable sütun değerleri</span><span class="sxs-lookup"><span data-stu-id="565b7-115">GetSchemaTable Column Values for UDTs</span></span>  

 <span data-ttu-id="565b7-116"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>Bir öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.DataTable> sütun meta verilerini açıklayan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="565b7-116">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="565b7-117">Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasındaki büyük UDTs için sütun meta verilerindeki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="565b7-117">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="565b7-118">SqlDataReader sütunu</span><span class="sxs-lookup"><span data-stu-id="565b7-118">SqlDataReader column</span></span>|<span data-ttu-id="565b7-119">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="565b7-119">SQL Server 2005</span></span>|<span data-ttu-id="565b7-120">SQL Server 2008 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="565b7-120">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="565b7-121">Değişir</span><span class="sxs-lookup"><span data-stu-id="565b7-121">Varies</span></span>|<span data-ttu-id="565b7-122">Değişir</span><span class="sxs-lookup"><span data-stu-id="565b7-122">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="565b7-123">255</span><span class="sxs-lookup"><span data-stu-id="565b7-123">255</span></span>|<span data-ttu-id="565b7-124">255</span><span class="sxs-lookup"><span data-stu-id="565b7-124">255</span></span>|  
|`NumericScale`|<span data-ttu-id="565b7-125">255</span><span class="sxs-lookup"><span data-stu-id="565b7-125">255</span></span>|<span data-ttu-id="565b7-126">255</span><span class="sxs-lookup"><span data-stu-id="565b7-126">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="565b7-127">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="565b7-127">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="565b7-128">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="565b7-128">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="565b7-129">21 ( `SqlDbType.VarBinary` )</span><span class="sxs-lookup"><span data-stu-id="565b7-129">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="565b7-130">29 ( `SqlDbType.Udt` )</span><span class="sxs-lookup"><span data-stu-id="565b7-130">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="565b7-131">29 ( `SqlDbType.Udt` )</span><span class="sxs-lookup"><span data-stu-id="565b7-131">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="565b7-132">29 ( `SqlDbType.Udt` )</span><span class="sxs-lookup"><span data-stu-id="565b7-132">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="565b7-133">*Database. SchemaName. TypeName* olarak belirtilen üç bölüm adı.</span><span class="sxs-lookup"><span data-stu-id="565b7-133">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="565b7-134">Değişir</span><span class="sxs-lookup"><span data-stu-id="565b7-134">Varies</span></span>|<span data-ttu-id="565b7-135">Değişir</span><span class="sxs-lookup"><span data-stu-id="565b7-135">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="565b7-136">SqlDataReader konuları</span><span class="sxs-lookup"><span data-stu-id="565b7-136">SqlDataReader Considerations</span></span>  

 <span data-ttu-id="565b7-137">, <xref:System.Data.SqlClient.SqlDataReader> Büyük udt değerlerini almayı desteklemek için SQL Server 2008 ' den başlayarak genişletildi.</span><span class="sxs-lookup"><span data-stu-id="565b7-137">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="565b7-138">Büyük UDT değerlerinin bir tarafından nasıl işlendiği <xref:System.Data.SqlClient.SqlDataReader> , kullandığınız SQL Server sürümüne ve ayrıca `Type System Version` bağlantı dizesinde belirtilen sürüme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="565b7-138">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="565b7-139">Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="565b7-139">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="565b7-140">Aşağıdaki yöntemleri <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlTypes.SqlBinary> , `Type System Version` SQL Server 2005 olarak ayarlandığında UDT yerine bir udt döndürür:</span><span class="sxs-lookup"><span data-stu-id="565b7-140">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="565b7-141">Aşağıdaki yöntemler `Byte[]` , `Type System Version` SQL Server 2005 olarak AYARLANDıĞıNDA bir udt yerine bir dizisi döndürür:</span><span class="sxs-lookup"><span data-stu-id="565b7-141">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="565b7-142">Geçerli ADO.NET sürümü için hiçbir dönüştürme yapılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="565b7-142">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="565b7-143">SqlParameters belirtme</span><span class="sxs-lookup"><span data-stu-id="565b7-143">Specifying SqlParameters</span></span>  

 <span data-ttu-id="565b7-144">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> Özellikler, büyük UDTs ile çalışacak şekilde genişletildi.</span><span class="sxs-lookup"><span data-stu-id="565b7-144">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="565b7-145">SqlParameter özelliği</span><span class="sxs-lookup"><span data-stu-id="565b7-145">SqlParameter Property</span></span>|<span data-ttu-id="565b7-146">Description</span><span class="sxs-lookup"><span data-stu-id="565b7-146">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="565b7-147">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="565b7-147">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="565b7-148">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="565b7-148">The default is null.</span></span> <span data-ttu-id="565b7-149">Özelliği `SqlBinary` , `Byte[]` veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="565b7-149">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="565b7-150">Parametresinin değerini temsil eden bir nesne alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="565b7-150">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="565b7-151">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="565b7-151">The default is null.</span></span> <span data-ttu-id="565b7-152">Özelliği `SqlBinary` , `Byte[]` veya yönetilen bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="565b7-152">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="565b7-153">Çözülecek parametre değerinin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="565b7-153">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="565b7-154">Varsayılan değer 0’dır.</span><span class="sxs-lookup"><span data-stu-id="565b7-154">The default value is 0.</span></span> <span data-ttu-id="565b7-155">Özelliği parametre değerinin boyutunu temsil eden bir tamsayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="565b7-155">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="565b7-156">Büyük UDTs 'ler için, UDT 'nin gerçek boyutu veya bilinmeyen için-1 olabilir.</span><span class="sxs-lookup"><span data-stu-id="565b7-156">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="565b7-157">Veri alma örneği</span><span class="sxs-lookup"><span data-stu-id="565b7-157">Retrieving Data Example</span></span>  

 <span data-ttu-id="565b7-158">Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="565b7-158">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="565b7-159">`connectionString`Değişken, SQL Server veritabanına geçerli bir bağlantı olduğunu varsayar ve `commandString` değişken önce listelenen birincil anahtar sütunu ile GEÇERLI bir SELECT ifadesini varsayar.</span><span class="sxs-lookup"><span data-stu-id="565b7-159">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="565b7-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="565b7-160">See also</span></span>

- [<span data-ttu-id="565b7-161">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="565b7-161">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="565b7-162">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="565b7-162">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="565b7-163">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="565b7-163">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="565b7-164">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="565b7-164">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="565b7-165">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="565b7-165">ADO.NET Overview</span></span>](../ado-net-overview.md)
