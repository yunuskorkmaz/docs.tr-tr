---
title: Bir veri kümesine bir XSLT dönüşümü uygulanarak
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 05894431f819b968877a4a971027850efe37126a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>Bir veri kümesine bir XSLT dönüşümü uygulanarak
**WriteXml** yöntemi <xref:System.Data.DataSet> içeriğini yazmanızı sağlayan bir **DataSet** XML verileri olarak. Bu XML XSL Dönüşümleri (XSLT) kullanarak başka bir biçime Dönüştür ortak bir görevdir. Ancak, eşitleme bir **DataSet** ile bir <xref:System.Xml.XmlDataDocument> XSLT stil sayfası içeriği için uygulamanızı sağlar bir **DataSet** ilk içeriğini yazmak zorunda kalmadan  **Veri kümesi** XML verileri kullanarak olarak **WriteXml**.  
  
 Aşağıdaki örnek dolduran bir **DataSet** tabloları ve ilişkileri ile eşitler **DataSet** ile bir **XmlDataDocument**ve bir kısmı Yazar **Veri kümesi** bir HTML olarak dosya XSLT stil kullanarak. XSLT stil içeriğini aşağıda verilmiştir.  
  
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
  
 Aşağıdaki kod dolgular **DataSet** ve XSLT stil sayfası uygular.  
  
> [!NOTE]
>  XSLT stil sayfası uyguluyorsanız bir **DataSet** ilişkileri içeren, ayarladığınız varsa, en iyi performansı elde **iç içe** özelliği <xref:System.Data.DataRelation> için **true**her biri için ilişkisi iç içe geçmiş. Bu hiyerarşi gidin ve performansı yoğun XPath konumu eksen (örneğin, önceki eşdüzey ve aşağıdaki eşdüzey stilde kullanılarak verileri dönüştürmek bu uygulama doğal yukarıdan aşağı işleme, XSLT stil sayfaları kullanmanıza olanak sağlar Bunu gitmek için sayfa düğüm test ifadeleri). İç içe geçmiş ilişkileri hakkında daha fazla bilgi için bkz: [iç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet ve XmlDataDocument Eşitlemesi](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
