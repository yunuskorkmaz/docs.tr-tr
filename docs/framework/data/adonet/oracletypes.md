---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 95a1173dfbcc4cf49ded8c7b8a42d9764fee9aff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149407"
---
# <a name="oracletypes"></a><span data-ttu-id="b6cd7-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="b6cd7-102">OracleTypes</span></span>
<span data-ttu-id="b6cd7-103">Oracle için .NET Framework Veri Sağlayıcısı, Oracle veri türleri ile çalışmak için kullanabileceğiniz çeşitli yapılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="b6cd7-104">Bunlar <xref:System.Data.OracleClient.OracleNumber> arasında <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6cd7-105">Bu yapıların tam listesi için <xref:System.Data.OracleClient>bkz.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="b6cd7-106">Aşağıdaki C# örnekleri:</span><span class="sxs-lookup"><span data-stu-id="b6cd7-106">The following C# examples:</span></span>  
  
- <span data-ttu-id="b6cd7-107">Bir Oracle tablosu oluşturun ve verilerle yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-107">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="b6cd7-108">Verilere <xref:System.Data.OracleClient.OracleDataReader> erişmek için bir'i <xref:System.Data.OracleClient.OracleType> kullanın ve verileri görüntülemek için çeşitli yapılar kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="b6cd7-109">Oracle Tablosu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6cd7-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="b6cd7-110">Bu örnek bir Oracle tablosu oluşturur ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="b6cd7-111">Bir sonraki örneği çalıştırmadan önce bu örneği çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="b6cd7-112">Oracle Tablosundan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="b6cd7-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="b6cd7-113">Bu örnek, verilere erişmek için bir **OracleDataReader** kullanır ve verileri görüntülemek için birkaç **OracleType** yapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6cd7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6cd7-114">See also</span></span>

- [<span data-ttu-id="b6cd7-115">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6cd7-115">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="b6cd7-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b6cd7-116">ADO.NET Overview</span></span>](ado-net-overview.md)
