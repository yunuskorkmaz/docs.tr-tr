---
title: XPath Veri Modelini Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: d449fe19640b19b1417c41b3a1ac7bd3a4de907a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291298"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>XPath Veri Modelini Kullanarak XML Verilerini İşleme
<xref:System.Xml?displayProperty=nameWithType>Ad alanı, veya sınıfları kullanarak XML belgelerinin, parçaların, düğümlerin veya düğüm kümesinin bellek içinde programlı bir gösterimini sağlar <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> .  
  
 <xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini kullanarak BIR XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar. <xref:System.Xml.XmlDocument>Sınıfı, W3C belge nesne modeli (DOM) düzey 1 Core ve çekırdek DOM düzeyi 2 uygulayan BIR XML belgesinin düzenlenebilir bellek içi gösterimini sağlar. Her iki sınıf de <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular ve <xref:System.Xml.XPath.XPathNavigator> seçim yapmak, değerlendirmek, gezinmek ve bazı durumlarda, temel alınan XML verilerini düzenlemek için kullanılan bir nesne döndürür.  
  
 Aşağıdaki bölümlerde, <xref:System.Xml.XPath.XPathNavigator> döndüren sınıfına göre sınıfının işlevleri açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Bir <xref:System.Xml.XPath.XPathDocument> XML belgesini okumak ve <xref:System.Xml.XmlDocument> bir XML belgesini okumak ve düzenlemek için bir salt okunurdur ve düzenlenebilir sınıf nesnesi oluşturmayı açıklar. Bu konu ayrıca <xref:System.Xml.XPath.XPathNavigator> BIR XML belgesini gezinmek ve düzenlemek için her sınıftan bir nesne döndürme işlemini açıklar.  
  
 [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> XPath sorgusu kullanarak bir veya nesnesindeki düğümleri seçmek, bir XPath ifadesinin sonuçlarını değerlendirmek ve INCELEMEK ve bir XML belgesindeki bir düğümün belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için kullanılan sınıfının yöntemlerini açıklar.  
  
 [XPathNavigator Kullanarak XML Verilerine Erişme](accessing-xml-data-using-xpathnavigator.md)  
 <xref:System.Xml.XPath.XPathNavigator>Düğümlerde gezinmek, XML verilerini ayıklamak ve bir veya nesnesinde kesin olarak BELIRLENMIŞ XML verilerine erişmek için kullanılan sınıfının yöntemlerini açıklar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .  
  
 [XPathNavigator Kullanarak XML Verilerini Düzenleme](editing-xml-data-using-xpathnavigator.md)  
 <xref:System.Xml.XPath.XPathNavigator>Bir nesne içindeki BIR XML belgesinden düğümleri ve değerleri eklemek, değiştirmek ve kaldırmak için kullanılan sınıfının yöntemlerini açıklar <xref:System.Xml.XmlDocument> .  
  
 [XPathNavigator Kullanarak Şema Doğrulama](schema-validation-using-xpathnavigator.md)  
 Bir veya nesnesinde bulunan XML içeriğini doğrulamaya yönelik yolları açıklar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [DOM Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-dom-model.md)
