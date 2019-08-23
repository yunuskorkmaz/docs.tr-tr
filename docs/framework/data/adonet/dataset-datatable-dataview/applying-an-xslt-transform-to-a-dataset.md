---
title: DataSet’e XSLT Dönüşümü Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 56f6e13763b5230e046c0838892393b3672a54be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937037"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>DataSet’e XSLT Dönüşümü Uygulama
Öğesinin<xref:System.Data.DataSet> **WriteXml** yöntemi, bir **veri kümesinin** içeriğini XML verisi olarak yazmanızı sağlar. Ortak bir görev daha sonra söz konusu XML 'i XSL dönüşümleri (XSLT) kullanarak başka bir biçime dönüştürmeye yönelik olur. Ancak, bir **veri kümesini** ile <xref:System.Xml.XmlDataDocument> eşitleme, ilk olarak **veri** kümesinin içeriğini **WriteXml**kullanarak XML verileri olarak yazmak zorunda kalmadan bir **veri kümesinin** içeriğine bir XSLT stil sayfası uygulamanıza olanak sağlar.  
  
 Aşağıdaki örnek bir **veri kümesini** tablolar ve ilişkiler ile doldurur, **veri kümesini** bir **XmlDataDocument**ile eşitler ve XSLT stil sayfasını kullanarak bir HTML dosyası olarak **veri kümesinin** bir kısmını yazar. XSLT stil sayfasının içerikleri aşağıda verilmiştir.  
  
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
  
 Aşağıdaki kod, **veri kümesini** doldurur ve XSLT stil sayfasını uygular.  
  
> [!NOTE]
> İlişki içeren bir **veri kümesine** XSLT stil sayfası uyguluyorsanız, iç içe geçmiş her ilişki için ' ın **iç içe** <xref:System.Data.DataRelation> özelliğini **true** olarak ayarlarsanız en iyi performansı elde edersiniz. Bu, hiyerarşide gezinmek ve verileri dönüştürmek için doğal yukarıdan aşağı işleme uygulayan XSLT stil sayfalarını kullanmanıza olanak tanır (örneğin, önceki eşdüzey ve aşağıdaki-eşdüzey stili). sayfa düğümü test ifadeleri) bölümüne gidin. İç içe geçmiş ilişkiler hakkında daha fazla bilgi için bkz. [Iç Içe geçme istekleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet ve XmlDataDocument Eşitlemesi](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
