---
title: XSLT Parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: cc412042e69a43bbecec9dbe68618e2d307ca793
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709705"
---
# <a name="xslt-parameters"></a>XSLT Parametreleri
XSLT parametreleri, <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi kullanılarak eklenir. Tam ad ve ad alanı URI 'SI parametre nesnesiyle ilişkili zamanda ilişkilendirilir.  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresi kullanmak için  
  
1. <xref:System.Xml.Xsl.XsltArgumentList> nesnesi oluşturun ve <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi kullanarak parametreyi ekleyin.  
  
2. Stil sayfasından parametresini çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.  
  
## <a name="parameter-types"></a>Parametre Türleri  
 Parameter nesnesi bir W3C türüne karşılık gelmelidir. Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer Microsoft .NET sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.  
  
|W3C türü|Eşdeğer .NET sınıfı (tür)|XPath veya XSLT türü|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator []**|{1&gt;XPath&lt;1}|  
  
 \* Bu, tek bir düğüm içeren bir düğüm kümesine eşdeğerdir.  
  
 Parametre nesnesi yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür. Ortak dil çalışma zamanı (CLR) sayısal türleri <xref:System.Double>dönüştürülür. <xref:System.DateTime> türü <xref:System.String>dönüştürülür. <xref:System.Xml.XPath.IXPathNavigable> türler <xref:System.Xml.XPath.XPathNavigator>dönüştürülür. **XPathNavigator []** <xref:System.Xml.XPath.XPathNodeIterator>dönüştürüldü.  
  
 Diğer tüm türler bir hata oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hesaplanan indirim tarihini tutacak bir parametre oluşturmak için <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemini kullanır. İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Giriş  
  
##### <a name="orderxml"></a>Order. xml  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>Discount. Xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Çıkış  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
