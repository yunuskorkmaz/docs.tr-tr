---
title: System.Xml sınıflardaki türü desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569700"
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml sınıflardaki türü desteği
.NET Framework sürüm 2. 0'da, temel XML sınıfları türü destek özellikleri içerecek şekilde geliştirilmiştir. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları XML Şeması türleri ve ortak dil çalışma zamanı (CLR) türler arasında dönüştürme yeteneği dahil olmak üzere türü destek özellikleri içerir.  
  
 .NET Framework sürüm 2.0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları türü destek özellikleri içerecek şekilde geliştirildi.  
  
-   <xref:System.Xml.XmlReader> Ve <xref:System.Xml.XPath.XPathNavigator> sınıflar her içeren bir **SchemaInfo** bir düğümde şema bilgileri döndüren özelliği.  
  
-   **ReadContentAs** ve **ReadElementContentAs** ve yöntemlere <xref:System.Xml.XmlReader> sınıfı bir metin değeri okuma ve tek yöntem çağrısı CLR değerinde dönüştürün.  
  
-   <xref:System.Xml.XmlWriter.WriteValue%2A> Yöntemi <xref:System.Xml.XmlWriter> sınıfı XML'yi yazılırken bu CLR türü bir XML Şeması türüne dönüştürür.  
  
-   **Değerlerini** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellikleri <xref:System.Xml.XPath.XPathNavigator> sınıfı bir düğüm değeri dönün ve tek yöntem çağrısı CLR değerinde dönüştürün.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 <xref:System.Xml.XmlConvert> sınıfı XML şeması ve CLR türleri arasında dönüştürme için gerekli.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Veri Türlerini CLR Türleriyle Eşleme](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 CLR türlerine XML veri türlerinin varsayılan eşlemeleri açıklar.  
  
 [XML Tür Desteği Uygulama Notları](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Tür destek uygulama ayrıntılarını bazıları açıklanır.  
  
 [XML Veri Türlerini Dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Nasıl kullanılacağını açıklar <xref:System.Xml.XmlConvert> XML şeması ve CLR türleri arasında dönüştürme için sınıf.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
