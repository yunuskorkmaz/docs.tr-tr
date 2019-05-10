---
title: System.Xml Sınıflarında Tür Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 979975e993a84dfe5c5527291f8cfe650be80ee6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647830"
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml Sınıflarında Tür Desteği
.NET Framework sürüm 2. 0'da, çekirdek XML sınıfı türü destek özellikleri içerecek şekilde geliştirilmiştir. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları XML Şeması türleri ve ortak dil çalışma zamanı (CLR) türler arasında dönüştürme olanağı dahil olmak üzere türü desteği özelliklerini içerir.  
  
 .NET Framework sürüm 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları geliştirilmiş tür desteği özelliklerini dahil etmek için.  
  
- <xref:System.Xml.XmlReader> Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları her bir **adet Schemaınfo** şema bilgileri bir düğümde döndüren özellik.  
  
- **ReadContentAs** ve **ReadElementContentAs** ve yöntemlere <xref:System.Xml.XmlReader> sınıfı bir metin değerini okur ve tek bir yöntem çağrısı bir CLR değere Dönüştür.  
  
- <xref:System.Xml.XmlWriter.WriteValue%2A> Metodunda <xref:System.Xml.XmlWriter> sınıfı XML'yi yazarken bu CLR türü bir XML Şeması türüne dönüştürür.  
  
- **Değerlerini** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellikleri <xref:System.Xml.XPath.XPathNavigator> sınıfı bir düğüm değer döndürmez ve tek bir yöntem çağrısı bir CLR değere Dönüştür.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 <xref:System.Xml.XmlConvert> sınıfı, XML şema ve CLR türleri arasında dönüştürme yapmak gerekiyordu.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Veri Türlerini CLR Türleriyle Eşleme](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Varsayılan eşlemeleri CLR türlerine XML veri türlerini açıklar.  
  
 [XML Tür Desteği Uygulama Notları](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Tür desteği uygulama ayrıntılarının bazılarını açıklar.  
  
 [XML Veri Türlerini Dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Nasıl kullanılacağını açıklar <xref:System.Xml.XmlConvert> XML şeması ve CLR türleri arasında dönüştürme yapmak sınıfı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
