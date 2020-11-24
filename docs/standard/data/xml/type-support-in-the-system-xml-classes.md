---
title: System.Xml Sınıflarında Tür Desteği
ms.date: 03/30/2017
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: 6fe55c64bc9bd17d5416eebf77060f2be27b81bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675665"
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml Sınıflarında Tür Desteği

.NET Framework sürüm 2,0 ' de, çekirdek XML sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> Ve SıNıFLARı, <xref:System.Xml.XPath.XPathNavigator> XML şema türleri ve ortak dil çalışma zamanı (CLR) türleri arasında dönüştürme özelliği de dahil olmak üzere tür desteği özelliklerini içerir.  
  
 .NET Framework sürüm 2,0 ' de,, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> ve <xref:System.Xml.XPath.XPathNavigator> sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir.  
  
- <xref:System.Xml.XmlReader>Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları, bir düğümdeki şema bilgilerini döndüren bir **fermainınfo** özelliği içerir.  
  
- **ReadContentAs** ve **ReadElementContentAs** ve <xref:System.Xml.XmlReader> sınıfındaki Yöntemler bir metin değerini okur ve tek bir yöntem çağrısında bir CLR değerine dönüştürür.  
  
- <xref:System.Xml.XmlWriter.WriteValue%2A>Sınıfındaki yöntemi, <xref:System.Xml.XmlWriter> XML 'yi yazarken bir clr türünü bir XML şema türüne dönüştürür.  
  
- Sınıftaki **ValueAs** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> Özellikler <xref:System.Xml.XPath.XPathNavigator> bir düğüm değeri döndürür ve tek BIR yöntem çağrısında bir CLR değerine dönüştürür.  
  
> [!NOTE]
> .NET Framework sürüm 1,0 ' de, <xref:System.Xml.XmlConvert> XML şeması ve clr türleri arasında dönüştürme yapmak için sınıf gerekiyordu.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [XML Veri Türlerini CLR Türleriyle Eşleme](mapping-xml-data-types-to-clr-types.md)  
 XML veri türlerinin CLR türlerine varsayılan eşlemelerini açıklar.  
  
 [XML Tür Desteği Uygulama Notları](xml-type-support-implementation-notes.md)  
 Bazı tür destek uygulama ayrıntılarını açıklar.  
  
 [XML Veri Türlerini Dönüştürme](conversion-of-xml-data-types.md)  
 <xref:System.Xml.XmlConvert>XML şeması ve clr türleri arasında dönüştürme yapmak için sınıfının nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
