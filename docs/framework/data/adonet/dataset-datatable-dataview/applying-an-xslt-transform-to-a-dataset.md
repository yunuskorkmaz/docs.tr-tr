---
title: DataSet’e XSLT Dönüşümü Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 3f066f29b99ade6e92a263110fed8079208567b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151500"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="d503d-102">DataSet’e XSLT Dönüşümü Uygulama</span><span class="sxs-lookup"><span data-stu-id="d503d-102">Applying an XSLT Transform to a DataSet</span></span>

<span data-ttu-id="d503d-103">**WriteXml** yöntemi, <xref:System.Data.DataSet> **Bir DataSet'in** içeriğini XML verisi olarak yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d503d-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="d503d-104">Yaygın bir görev daha sonra XSL dönüşümleri (XSLT) kullanarak başka bir biçime xml dönüştürmektir.</span><span class="sxs-lookup"><span data-stu-id="d503d-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="d503d-105">Ancak, bir **DataSet** ile <xref:System.Xml.XmlDataDocument> senkronize bir XSLT stylesheet ilk **WriteXml**kullanarak XML veri olarak **DataSet** içeriğini yazmak zorunda kalmadan bir **DataSet** içeriğine bir XSLT stylesheet uygulamak için olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d503d-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="d503d-106">Aşağıdaki örnek, bir **DataSet'i** tablolar ve ilişkilerle doldurur, **DataSet'i** **XmlDataDocument**ile eşitler ve **DataSet'in** bir bölümünü XSLT stil sayfası kullanarak HTML dosyası olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="d503d-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="d503d-107">XSLT stil sayfasının içeriği şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d503d-107">The following are the contents of the XSLT stylesheet:</span></span>
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="d503d-108">Aşağıdaki kod **DataSet'i** doldurur ve XSLT stil sayfasını uygular.</span><span class="sxs-lookup"><span data-stu-id="d503d-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d503d-109">İlişkiler içeren bir **DataSet'e** Bir XSLT stil sayfası uyguluyorsanız, iç **içe** geçen her <xref:System.Data.DataRelation> ilişki için **yuvalanmış** özelliğini ayarlarsanız en iyi performansı elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d503d-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="d503d-110">Bu, performans yoğun XPath konum eksenlerini (örneğin, önceki kardeş ve aşağıdaki kardeş stilinde) kullanmanın aksine, hiyerarşide gezinmek ve verileri dönüştürmek için doğal yukarıdan aşağıya işleme uygulayan XSLT stil sayfalarını kullanmanıza olanak tanır sayfa düğümü test ifadeleri) gezinmek için.</span><span class="sxs-lookup"><span data-stu-id="d503d-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="d503d-111">İç içe geçen ilişkiler hakkında daha fazla bilgi için İç [Içe Veri İlişkileri'ne](nesting-datarelations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d503d-111">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d503d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d503d-112">See also</span></span>

- [<span data-ttu-id="d503d-113">DataSet ve XmlDataDocument Eşitlemesi</span><span class="sxs-lookup"><span data-stu-id="d503d-113">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="d503d-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d503d-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
