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
<xref:System.Xml?displayProperty=nameWithType> ad alanı, <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> sınıfları kullanarak XML belgelerinin, parçaların, düğümlerin veya düğüm kümesinin bellek içinde programlı bir gösterimini sağlar.  
  
 <xref:System.Xml.XPath.XPathDocument> sınıfı, XPath veri modelini kullanarak bir XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. <xref:System.Xml.XmlDocument> sınıfı, W3C Belge Nesne Modeli (DOM) düzey 1 Core ve çekirdek DOM düzeyi 2 uygulayan bir XML belgesinin düzenlenebilir bellek içi gösterimini sağlar. Her iki sınıf de <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular ve bazı durumlarda seçmek, değerlendirmek, gezinmek ve bazı durumlarda kullanılan bir <xref:System.Xml.XPath.XPathNavigator> nesnesi döndürür, temel alınan XML verilerini düzenler.  
  
 Aşağıdaki bölümlerde, döndüren sınıfına göre <xref:System.Xml.XPath.XPathNavigator> sınıfının işlevleri açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Bir <xref:System.Xml.XmlDocument> XML belgesini okumak ve bir XML belgesini okumak ve düzenlemek için bir salt okunurdur <xref:System.Xml.XPath.XPathDocument> sınıf nesnesinin nasıl oluşturulduğunu açıklar. Bu konu ayrıca, bir XML belgesini gezinmek ve düzenlemek için her bir sınıftan bir <xref:System.Xml.XPath.XPathNavigator> nesne döndürme işlemini açıklar.  
  
 [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğümleri XPath sorgusu kullanarak seçmek, bir XPath ifadesinin sonuçlarını değerlendirmek ve incelemek ve bir XML belgesindeki bir düğümün belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için kullanılan <xref:System.Xml.XPath.XPathNavigator> sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Düğümlerde gezinmek, XML verilerini ayıklamak ve bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesinde kesin türü belirtilmiş XML verilerine erişmek için kullanılan <xref:System.Xml.XPath.XPathNavigator> sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak XML Verilerini Düzenleme](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XmlDocument> nesnesinde bulunan bir XML belgesinden düğüm ve değer eklemek, değiştirmek ve kaldırmak için kullanılan <xref:System.Xml.XPath.XPathNavigator> sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak Şema Doğrulama](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesinde bulunan XML içeriğini doğrulamaya yönelik yolları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
