---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 37089649c66c964f8a912c5a227a5281f6c0dfb7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189155"
---
# <a name="oracletypes"></a><span data-ttu-id="9310d-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="9310d-102">OracleTypes</span></span>

<span data-ttu-id="9310d-103">Oracle için .NET Framework Veri Sağlayıcısı, Oracle veri türleriyle çalışmak için kullanabileceğiniz çeşitli yapılar içerir.</span><span class="sxs-lookup"><span data-stu-id="9310d-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="9310d-104">Bunlar <xref:System.Data.OracleClient.OracleNumber> ve içerir <xref:System.Data.OracleClient.OracleString> .</span><span class="sxs-lookup"><span data-stu-id="9310d-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9310d-105">Bu yapıların tüm listesi için bkz <xref:System.Data.OracleClient> ..</span><span class="sxs-lookup"><span data-stu-id="9310d-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="9310d-106">Aşağıdaki C# örnekleri:</span><span class="sxs-lookup"><span data-stu-id="9310d-106">The following C# examples:</span></span>  
  
- <span data-ttu-id="9310d-107">Oracle tablosu oluşturun ve verilerle yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9310d-107">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="9310d-108"><xref:System.Data.OracleClient.OracleDataReader>Verilere erişmek için bir kullanın ve <xref:System.Data.OracleClient.OracleType> verileri göstermek için çeşitli yapılar kullanın.</span><span class="sxs-lookup"><span data-stu-id="9310d-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="9310d-109">Oracle tablosu oluşturma</span><span class="sxs-lookup"><span data-stu-id="9310d-109">Creating an Oracle Table</span></span>  

 <span data-ttu-id="9310d-110">Bu örnek bir Oracle tablosu oluşturur ve verileri verilerle yükler.</span><span class="sxs-lookup"><span data-stu-id="9310d-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="9310d-111">Sonraki örneği çalıştırmadan önce bu örneği çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9310d-111">You must run this example before running the next example.</span></span>  
  
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
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="9310d-112">Oracle tablosundan veri alma</span><span class="sxs-lookup"><span data-stu-id="9310d-112">Retrieving Data from the Oracle Table</span></span>  

 <span data-ttu-id="9310d-113">Bu örnek, verilere erişmek için bir **OracleDataReader** kullanır ve verileri göstermek Için çeşitli **OracleType** yapılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9310d-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9310d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9310d-114">See also</span></span>

- [<span data-ttu-id="9310d-115">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9310d-115">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="9310d-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9310d-116">ADO.NET Overview</span></span>](ado-net-overview.md)
