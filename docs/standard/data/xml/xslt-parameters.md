---
title: XSLT parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63a394bd30b3586f084dc1a2320fa9133da19b64
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075442"
---
# <a name="xslt-parameters"></a>XSLT parametreleri
XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi. Bir tam adı ve ad alanı URI o anda parametresi nesnesi ile ilişkilendirilmiş.  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresini kullanma  
  
1.  Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve parametresini kullanarak ekleme <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.  
  
2.  Parametresi, stil sayfası içinden çağırın.  
  
3.  Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="parameter-types"></a>Parametre türleri  
 Parametre nesnesine W3C türüne karşılık gelmelidir. Eşdeğer Microsoft .NET sınıfları (tür), aşağıdaki tablo W3C türleri karşılık gelen gösterir ve W3C türün bir XPath türü veya XSLT türü olup.  
  
|W3C türü|Eşdeğeri .NET sınıfı (tür)|XPath veya XSLT türü|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator]**|XPath|  
  
 * Bu, tek bir düğüm içeren bir düğüm kümesi olarak eşdeğerdir.  
  
 Parametre nesnesine yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür. Ortak dil çalışma zamanı (CLR) sayısal türleri dönüştürülür <xref:System.Double>. <xref:System.DateTime> Türüne dönüştürülür <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> türleri dönüştürülür <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Diğer tüm türlerin bir hata atar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan tutmak için bir parametre yöntemini indirim tarih. İndirimi tarihini, sipariş tarihi 20 gün olarak hesaplanır.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Giriş  
  
##### <a name="orderxml"></a>Order.XML  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>discount.xsl  
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
