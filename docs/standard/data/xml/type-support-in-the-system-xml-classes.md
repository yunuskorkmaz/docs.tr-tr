---
title: "System.Xml sınıflardaki türü desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [CLR türlerine XML veri türleri eşleme](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 CLR türlerine XML veri türlerinin varsayılan eşlemeleri açıklar.  
  
 [XML türü destek uygulama notları](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Tür destek uygulama ayrıntılarını bazıları açıklanır.  
  
 [XML veri türlerini dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Nasıl kullanılacağını açıklar <xref:System.Xml.XmlConvert> XML şeması ve CLR türleri arasında dönüştürme için sınıf.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
