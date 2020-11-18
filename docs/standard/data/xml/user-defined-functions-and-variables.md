---
title: Kullanıcı Tanımlı İşlevler ve Değişkenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: d4936ec32d54a465803d493048cba2b70ed50db6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818511"
---
# <a name="user-defined-functions-and-variables"></a>Kullanıcı Tanımlı İşlevler ve Değişkenler
<xref:System.Xml.XPath.XPathNavigator>Sınıfı, verilerle etkileşim kurmak için kullanılan bir yöntemler kümesi sağlar <xref:System.Xml.XPath.XPathDocument> . XPath sorgu ifadeleri tarafından kullanılmak üzere uzantı işlevleri ve değişkenler uygulayarak standart XPath işlevlerini tamamlayabilirsiniz. <xref:System.Xml.XPath.XPathExpression.SetContext%2A>Yöntemi öğesinden türetilmiş Kullanıcı tanımlı bir bağlamı kabul edebilir <xref:System.Xml.Xsl.XsltContext> . Kullanıcı tanımlı işlevler özel bağlam tarafından çözümlenir.  
  
 Uzantı işlevleri ve değişkenler, XML ekleme saldırılarını önlemeye yardımcı olabilir. Bu senaryolarda, Kullanıcı girişi özel değişkenlere atanır ve işlem yönergeleriyle birleştirilmiş ham giriş olarak değil uzantı işlevleri tarafından işlenir. Uzantı işlevleri ve değişkenler, yalnızca tasarımcı tarafından amaçlanan XML verilerinde davranması için Kullanıcı girişi içerir.  
  
 Uzantıları kullanmak için <xref:System.Xml.Xsl.XsltContext> , arabirimler ile birlikte özel bir sınıf uygulayın <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantı işlevlerini ve değişkenlerini destekleyebilirsiniz. , <xref:System.Xml.XPath.XPathExpression> Kendi özel öğesine sahip kullanıcı girişi ekler <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltContext> .  
  
 , <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathNavigator> İfadesi tarafından tanımlanan düğümleri bulmak ve işlemek için kullanılan bir derlenmiş sorguyu temsil eder.  
  
 Aşağıdaki örnek, öğesinden türetilmiş özel bir bağlam sınıfının uygulamasını gösterir <xref:System.Xml.Xsl.XsltContext> . Koddaki açıklamalar sınıf üyelerini ve bunların özel işlevlerde kullanımını anlatmaktadır. İşlev ve değişken uygulamaları ve bu uygulamaları kullanan bir örnek uygulama bu kod segmentini izler.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextFunction> . Uygulayan sınıf, <xref:System.Xml.Xsl.IXsltContextFunction> Kullanıcı tanımlı işlevleri çözer ve yürütür. Bu örnek, bildirimi tarafından tanımlanan işlevi kullanır: `private int CountChar(string title, char charTocount)` .  
  
 Kod açıklamaları sınıf üyelerini anlatmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Aşağıdaki kod uygular <xref:System.Xml.Xsl.IXsltContextVariable> . Bu sınıf, çalışma zamanında XPath sorgu ifadelerinde Kullanıcı tanımlı değişkenlere yapılan başvuruları çözümler. Bu sınıfın bir örneği oluşturulur ve özel sınıfın geçersiz kılınan yöntemiyle döndürülür <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> <xref:System.Xml.Xsl.XsltContext> .  
  
 Kod açıklamaları sınıf üyelerini anlatmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Kapsamdaki önceki sınıf tanımlarıyla aşağıdaki kod, belgenin öğelerindeki karakterleri saymak için özel fonksiyonunu kullanır `Tasks.xml` . Koddaki açıklamalar, özel işlevi derleyen ve belgeye karşı çalışan kodu anlatmaktadır `Tasks.xml` .  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Bu örnek, aşağıdaki XML verilerini kullanır.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
