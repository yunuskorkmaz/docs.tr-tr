---
title: XPath Veri Modelini Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: f964864577cf08eb074bdfb9af7f7daf3ffb37b9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710446"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>XPath Veri Modelini Kullanarak XML Verilerini İşleme
<xref:System.Xml?displayProperty=nameWithType> Ad alanı, <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> sınıfları kullanarak XML belgelerinin, parçaların, düğümlerin veya düğüm kümesinin bellek içinde programlı bir gösterimini sağlar.  
  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, XPath veri modelini kullanarak bir XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. Sınıfı <xref:System.Xml.XmlDocument> , W3C belge nesne MODELI (DOM) düzey 1 Core ve çekirdek DOM düzeyi 2 uygulayan bir XML belgesinin düzenlenebilir bellek içi gösterimini sağlar. Her iki sınıf de <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular ve seçim <xref:System.Xml.XPath.XPathNavigator> yapmak, değerlendirmek, gezinmek ve bazı durumlarda, temel alınan XML verilerini düzenlemek için kullanılan bir nesne döndürür.  
  
 Aşağıdaki bölümlerde, döndüren sınıfına göre <xref:System.Xml.XPath.XPathNavigator> sınıfının işlevleri açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Bir XML belgesini okumak ve bir XML belgesini <xref:System.Xml.XPath.XPathDocument> okumak ve düzenlemek için bir salt okunurdur ve düzenlenebilir <xref:System.Xml.XmlDocument> sınıf nesnesi oluşturmayı açıklar. Bu konu ayrıca bir XML belgesini gezinmek <xref:System.Xml.XPath.XPathNavigator> ve düzenlemek için her sınıftan bir nesne döndürme işlemini açıklar.  
  
 [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Bir XPath sorgusu kullanarak bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğümleri seçmek, bir XPath ifadesinin SONUÇLARıNı değerlendirmek ve incelemek ve bir XML belgesindeki bir düğümün belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için kullanılan sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Düğümlerde gezinmek, XML verilerini <xref:System.Xml.XPath.XPathNavigator> ayıklamak ve bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesinde kesin olarak belirlenmiş XML verilerine erişmek için kullanılan sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XmlDocument> nesne IÇINDEKI bir XML <xref:System.Xml.XPath.XPathNavigator> belgesinden düğümleri ve değerleri eklemek, değiştirmek ve kaldırmak için kullanılan sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesinde bulunan XML içeriğini doğrulamaya yönelik yolları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
