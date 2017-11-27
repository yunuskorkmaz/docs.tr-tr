---
title: "Büyük atama"
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
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1133db68d233032b64d113a09e367781cf73321e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="large-udts"></a><span data-ttu-id="4b604-102">Büyük atama</span><span class="sxs-lookup"><span data-stu-id="4b604-102">Large UDTs</span></span>
<span data-ttu-id="4b604-103">Kullanıcı tanımlı türler (atama) ortak dil çalışma zamanı (CLR) nesneleri bir SQL Server veritabanında depolayarak sunucunun skaler tür sistemini genişletmek Geliştirici izin verin.</span><span class="sxs-lookup"><span data-stu-id="4b604-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="4b604-104">Atama birden çok öğe içerebilir ve tek bir SQL Server sistem veri türü oluşur geleneksel diğer veri türleri farklı davranışlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b604-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b604-105">.NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) büyük atama için Gelişmiş SqlClient destek yararlanmak için.</span><span class="sxs-lookup"><span data-stu-id="4b604-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="4b604-106">Daha önce atama en büyük boyutunu 8 kilobayt için kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="4b604-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="4b604-107">Bu kısıtlama bir biçimine sahip atama için SQL Server 2008'de kaldırılmıştır <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="4b604-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="4b604-108">Kullanıcı tanımlı türler için kapsamlı belgeler için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="4b604-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="4b604-109">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="4b604-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="4b604-110">CLR kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="4b604-110">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="4b604-111">GetSchema kullanarak UDT şemaları alma</span><span class="sxs-lookup"><span data-stu-id="4b604-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="4b604-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Yöntemi <xref:System.Data.SqlClient.SqlConnection> döndürür veritabanı şema bilgileri bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4b604-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="4b604-113">Daha fazla bilgi için bkz: [SQL Server şeması koleksiyonları](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="4b604-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="4b604-114">GetSchemaTable sütun değerlerini atama</span><span class="sxs-lookup"><span data-stu-id="4b604-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="4b604-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> döndüren bir <xref:System.Data.DataTable> sütun meta verileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b604-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="4b604-116">Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasında büyük atama için sütun meta verileri farklılıkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b604-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="4b604-117">SqlDataReader sütun</span><span class="sxs-lookup"><span data-stu-id="4b604-117">SqlDataReader column</span></span>|<span data-ttu-id="4b604-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="4b604-118">SQL Server 2005</span></span>|<span data-ttu-id="4b604-119">SQL Server 2008 ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="4b604-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="4b604-120">Değişir</span><span class="sxs-lookup"><span data-stu-id="4b604-120">Varies</span></span>|<span data-ttu-id="4b604-121">Değişir</span><span class="sxs-lookup"><span data-stu-id="4b604-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="4b604-122">255</span><span class="sxs-lookup"><span data-stu-id="4b604-122">255</span></span>|<span data-ttu-id="4b604-123">255</span><span class="sxs-lookup"><span data-stu-id="4b604-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="4b604-124">255</span><span class="sxs-lookup"><span data-stu-id="4b604-124">255</span></span>|<span data-ttu-id="4b604-125">255</span><span class="sxs-lookup"><span data-stu-id="4b604-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="4b604-126">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="4b604-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="4b604-127">UDT örneği</span><span class="sxs-lookup"><span data-stu-id="4b604-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="4b604-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="4b604-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="4b604-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="4b604-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="4b604-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="4b604-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="4b604-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="4b604-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="4b604-132">Üç parçası olarak belirtilen adı *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="4b604-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="4b604-133">Değişir</span><span class="sxs-lookup"><span data-stu-id="4b604-133">Varies</span></span>|<span data-ttu-id="4b604-134">Değişir</span><span class="sxs-lookup"><span data-stu-id="4b604-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="4b604-135">SqlDataReader konuları</span><span class="sxs-lookup"><span data-stu-id="4b604-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="4b604-136"><xref:System.Data.SqlClient.SqlDataReader> Büyük UDT değerlerini alma desteklemek için SQL Server 2008'den itibaren genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4b604-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="4b604-137">Büyük UDT değer tarafından işlenen nasıl bir <xref:System.Data.SqlClient.SqlDataReader> kullanıyorsanız, üzerinde de olarak SQL Server sürümüne bağlıdır `Type System Version` bağlantı dizesinde belirtilen.</span><span class="sxs-lookup"><span data-stu-id="4b604-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="4b604-138">Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b604-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="4b604-139">Aşağıdaki yöntemlerden birini <xref:System.Data.SqlClient.SqlDataReader> döndürülecek bir <xref:System.Data.SqlTypes.SqlBinary> UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4b604-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="4b604-140">Aşağıdaki yöntemlerden bir dizi döndürür `Byte[]` UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4b604-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="4b604-141">Hiçbir dönüştürme ADO.NET geçerli sürümü için yapılan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4b604-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="4b604-142">SqlParameters belirtme</span><span class="sxs-lookup"><span data-stu-id="4b604-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="4b604-143">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> genişletilmiş özellikler büyük atama ile çalışmak için.</span><span class="sxs-lookup"><span data-stu-id="4b604-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="4b604-144">SqlParameter özelliği</span><span class="sxs-lookup"><span data-stu-id="4b604-144">SqlParameter Property</span></span>|<span data-ttu-id="4b604-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b604-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="4b604-146">Alır veya ayarlar parametresinin değerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="4b604-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="4b604-147">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="4b604-147">The default is null.</span></span> <span data-ttu-id="4b604-148">Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="4b604-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="4b604-149">Alır veya ayarlar parametresinin değerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="4b604-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="4b604-150">Varsayılan olarak null'dur.</span><span class="sxs-lookup"><span data-stu-id="4b604-150">The default is null.</span></span> <span data-ttu-id="4b604-151">Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.</span><span class="sxs-lookup"><span data-stu-id="4b604-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="4b604-152">Alır veya gidermek için parametre değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4b604-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="4b604-153">Varsayılan değer 0’dır.</span><span class="sxs-lookup"><span data-stu-id="4b604-153">The default value is 0.</span></span> <span data-ttu-id="4b604-154">Parametre değeri boyutunu temsil eden bir tamsayı özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b604-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="4b604-155">Büyük atama için UDT veya -1 bilinmeyen için gerçek boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b604-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="4b604-156">Veri örneği alınıyor</span><span class="sxs-lookup"><span data-stu-id="4b604-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="4b604-157">Aşağıdaki kod parçası, büyük UDT veri almayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b604-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="4b604-158">`connectionString` Değişkeni geçerli bir SQL Server veritabanı bağlantısının varsayar ve `commandString` değişkeni, ilk listelenen birincil anahtar sütunu geçerli bir SELECT deyimi varsayar.</span><span class="sxs-lookup"><span data-stu-id="4b604-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b604-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b604-159">See Also</span></span>  
 [<span data-ttu-id="4b604-160">Yapılandırma parametreleri ve parametre veri türleri</span><span class="sxs-lookup"><span data-stu-id="4b604-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="4b604-161">Veritabanı şema bilgileri alınıyor</span><span class="sxs-lookup"><span data-stu-id="4b604-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="4b604-162">SQL Server veri türü eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="4b604-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="4b604-163">SQL Server ikili ve değeri büyük veri</span><span class="sxs-lookup"><span data-stu-id="4b604-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="4b604-164">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="4b604-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
