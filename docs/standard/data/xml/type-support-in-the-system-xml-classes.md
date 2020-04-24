---
title: System.Xml Sınıflarında Tür Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710108"
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml Sınıflarında Tür Desteği
.NET Framework sürüm 2,0 ' de, çekirdek XML sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları, XML şema türleri ve ortak dil çalışma zamanı (CLR) türleri arasında dönüştürme özelliği de dahil olmak üzere tür desteği özelliklerini içerir.  
  
 .NET Framework sürüm 2,0 ' <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>de,, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir.  
  
- Ve <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> sınıfları, bir düğümdeki şema bilgilerini döndüren bir **fermainınfo** özelliği içerir.  
  
- **ReadContentAs** ve **ReadElementContentAs** ve <xref:System.Xml.XmlReader> sınıfındaki Yöntemler bir metin değerini okur ve tek bir yöntem çağrısında bir CLR değerine dönüştürür.  
  
- <xref:System.Xml.XmlWriter> Sınıfındaki YÖNTEMI, <xref:System.Xml.XmlWriter.WriteValue%2A> XML 'yi yazarken BIR clr türünü bir XML şema türüne dönüştürür.  
  
- <xref:System.Xml.XPath.XPathNavigator> Sınıftaki **ValueAs** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> Özellikler bir düğüm değeri döndürür ve tek bir yöntem çağrısında bir CLR değerine dönüştürür.  
  
> [!NOTE]
> .NET Framework sürüm 1,0 ' de, <xref:System.Xml.XmlConvert> XML ŞEMASı ve clr türleri arasında dönüştürme yapmak için sınıf gerekiyordu.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Veri Türlerini CLR Türleriyle Eşleme](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 XML veri türlerinin CLR türlerine varsayılan eşlemelerini açıklar.  
  
 [XML Tür Desteği Uygulama Notları](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Bazı tür destek uygulama ayrıntılarını açıklar.  
  
 [XML Veri Türlerini Dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 XML şeması ve CLR türleri <xref:System.Xml.XmlConvert> arasında dönüştürme yapmak için sınıfının nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
