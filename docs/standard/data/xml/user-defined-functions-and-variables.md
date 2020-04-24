---
title: Kullanıcı Tanımlı İşlevler ve Değişkenler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: 7040c2ccf6e3bfc6efcbec3505c633c6c3c6508f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710069"
---
# <a name="user-defined-functions-and-variables"></a>Kullanıcı Tanımlı İşlevler ve Değişkenler
Sınıfı <xref:System.Xml.XPath.XPathNavigator> , <xref:System.Xml.XPath.XPathDocument> verilerle etkileşim kurmak için kullanılan bir yöntemler kümesi sağlar. XPath sorgu ifadeleri tarafından kullanılmak üzere uzantı işlevleri ve değişkenler uygulayarak standart XPath işlevlerini tamamlayabilirsiniz. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Yöntemi öğesinden <xref:System.Xml.Xsl.XsltContext>türetilmiş Kullanıcı tanımlı bir bağlamı kabul edebilir. Kullanıcı tanımlı işlevler özel bağlam tarafından çözümlenir.  
  
 Uzantı işlevleri ve değişkenler, XML ekleme saldırılarını önlemeye yardımcı olabilir. Bu senaryolarda, Kullanıcı girişi özel değişkenlere atanır ve işlem yönergeleriyle birleştirilmiş ham giriş olarak değil uzantı işlevleri tarafından işlenir. Uzantı işlevleri ve değişkenler, yalnızca tasarımcı tarafından amaçlanan XML verilerinde davranması için Kullanıcı girişi içerir.  
  
 Uzantıları kullanmak için, arabirimler <xref:System.Xml.Xsl.XsltContext> <xref:System.Xml.Xsl.IXsltContextFunction> ile birlikte özel bir sınıf uygulayın ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantı işlevlerini ve değişkenlerini destekleyebilirsiniz. , <xref:System.Xml.XPath.XPathExpression> Kendi <xref:System.Xml.Xsl.XsltArgumentList> özel <xref:System.Xml.Xsl.XsltContext>öğesine sahip kullanıcı girişi ekler.  
  
 , <xref:System.Xml.XPath.XPathExpression> İfadesi tarafından tanımlanan düğümleri bulmak <xref:System.Xml.XPath.XPathNavigator> ve işlemek için kullanılan bir derlenmiş sorguyu temsil eder.  
  
 Aşağıdaki örnek, öğesinden <xref:System.Xml.Xsl.XsltContext>türetilmiş özel bir bağlam sınıfının uygulamasını gösterir. Koddaki açıklamalar sınıf üyelerini ve bunların özel işlevlerde kullanımını anlatmaktadır. İşlev ve değişken uygulamaları ve bu uygulamaları kullanan bir örnek uygulama bu kod segmentini izler.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextFunction>. Uygulayan <xref:System.Xml.Xsl.IXsltContextFunction> sınıf, Kullanıcı tanımlı işlevleri çözer ve yürütür. Bu örnek, bildirimi tarafından tanımlanan işlevi kullanır: `private int CountChar(string title, char charTocount)`.  
  
 Kod açıklamaları sınıf üyelerini anlatmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextVariable>. Bu sınıf, çalışma zamanında XPath sorgu ifadelerinde Kullanıcı tanımlı değişkenlere yapılan başvuruları çözümler. Bu sınıfın bir örneği oluşturulur ve özel <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> <xref:System.Xml.Xsl.XsltContext> sınıfın geçersiz kılınan yöntemiyle döndürülür.  
  
 Kod açıklamaları sınıf üyelerini anlatmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Kapsamdaki önceki sınıf tanımlarıyla aşağıdaki kod, `Tasks.xml` belgenin öğelerindeki karakterleri saymak için özel fonksiyonunu kullanır. Koddaki açıklamalar, özel işlevi derleyen ve `Tasks.xml` belgeye karşı çalışan kodu anlatmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Bu örnek, aşağıdaki XML verilerini kullanır.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
