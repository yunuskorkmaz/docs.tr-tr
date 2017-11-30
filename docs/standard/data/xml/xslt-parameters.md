---
title: XSLT parametreleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e66d98501bb0bd3a5d5cd5eacc0b09405c158522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-parameters"></a>XSLT parametreleri
XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi. Bir tam adı ve ad alanı URI'si o anda parametre nesnesi ile ilişkilendirilmiş.  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresini kullanma  
  
1.  Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve parametresini kullanarak eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.  
  
2.  Parametresi, stil sayfası içinden çağırın.  
  
3.  Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="parameter-types"></a>Parametre türleri  
 Parametre nesnesi W3C türüne karşılık gelmelidir. W3C türü bir XPath türü veya XSLT türü olup ve eşdeğer Microsoft .NET sınıfları (yazın) karşılık gelen W3C türleri aşağıdaki tabloda gösterir.  
  
|W3C türü|Eşdeğer .NET sınıfı (tür)|XPath veya XSLT türü|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator]**|XPath|  
  
 * Bu, tek bir düğüm içeren düğüm kümesi eşdeğerdir.  
  
 Parametre nesnesi yukarıdaki sınıflarından biri değilse, aşağıdaki kurallara göre dönüştürülür. Ortak dil çalışma zamanı (CLR) sayısal türler dönüştürülür <xref:System.Double>. <xref:System.DateTime> Türü için dönüştürülür <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable>türlerine dönüştürülür <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Tüm diğer türleri hata atar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan tutmak için bir parametre oluşturmak için yöntemi indirim tarih. İndirim tarih sırası 20 gün olarak hesaplanır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT dönüştürmeleri](../../../../docs/standard/data/xml/xslt-transformations.md)
