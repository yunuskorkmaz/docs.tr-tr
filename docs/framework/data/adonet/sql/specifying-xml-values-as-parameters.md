---
title: Parametre Olarak XML Değerleri Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: 8e57bfe23a80bf3913cd7fb8b96527870259e77a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780880"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="b7535-102">Parametre Olarak XML Değerleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="b7535-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="b7535-103">Bir sorgu, değeri bir XML dizesi olan bir parametre gerektiriyorsa, geliştiriciler bu değeri **sqlxml** veri türünün bir örneğini kullanarak sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b7535-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="b7535-104">Gerçekten bir püf noktası yoktur; SQL Server XML sütunları, parametre değerlerini diğer veri türleriyle tamamen aynı şekilde kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b7535-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7535-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7535-105">Example</span></span>  
 <span data-ttu-id="b7535-106">Aşağıdaki konsol uygulaması **AdventureWorks** veritabanında yeni bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7535-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="b7535-107">Yeni tablo **SalesId** adlı bir sütun ve **SALESıNFO**adlı bir xml sütunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b7535-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7535-108">SQL Server yüklediğinizde **AdventureWorks** örnek veritabanı varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7535-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="b7535-109">SQL Server kurulumunu çalıştırarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7535-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="b7535-110">Örnek, yeni tabloya <xref:System.Data.SqlClient.SqlCommand> bir satır eklemek için bir nesne hazırlar.</span><span class="sxs-lookup"><span data-stu-id="b7535-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="b7535-111">Kayıtlı bir dosya, **SalesInfo** sütunu IÇIN gereken XML verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7535-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="b7535-112">Çalıştırmak üzere gereken dosyayı oluşturmak için, projenizle aynı klasörde yeni bir metin dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7535-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="b7535-113">Dosyayı MyTestStoreData. xml olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b7535-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="b7535-114">Dosyayı Not defteri 'nde açın ve aşağıdaki metni kopyalayıp yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="b7535-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a   
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7535-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7535-115">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="b7535-116">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="b7535-116">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="b7535-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b7535-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
