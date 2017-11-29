---
title: "Kullanıcı tanımlı işlevler ve değişkenler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e1327ac2a3df7a84c157e4bf60d2ad63d69b1677
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions-and-variables"></a>Kullanıcı tanımlı işlevler ve değişkenler
<xref:System.Xml.XPath.XPathNavigator> Sınıfı ile etkileşim kurmak için kullanılan yöntemler kümesi sağlar <xref:System.Xml.XPath.XPathDocument> veri. XPath sorgusu ifadeleri tarafından uzantısı işlevleri ve değişkenler kullanmak için uygulayarak standart XPath işlevleri destekleyebilirsiniz. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Yöntemi türetilmiş bir kullanıcı tanımlı içerik kabul edebileceği <xref:System.Xml.Xsl.XsltContext>. Kullanıcı tanımlı işlevler özel bağlam tarafından çözümlenir.  
  
 Uzantı işlevleri ve değişkenler XML ekleme saldırıları önleme yararlı olabilir. Bu senaryolarda kullanıcı girişi özel değişkenleri için atanan ve işlem yönergeleri ile birleştirilmiş değil raw giriş olarak uzantısı işlevleri tarafından işlenebilir. Bunu yalnızca XML verileri üzerinde tasarımcı tarafından istendiği gibi üstlenebilir uzantı işlevleri ve değişkenler kullanıcı girişi içerir.  
  
 Uzantıları kullanmak için özel bir uygulama <xref:System.Xml.Xsl.XsltContext> arabirimler birlikte sınıfı <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantısı işlevleri ve değişkenler destekler. Bir <xref:System.Xml.XPath.XPathExpression> ile kullanıcı girişi ekler, <xref:System.Xml.Xsl.XsltArgumentList> özel <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Bir derlenmiş temsil eden sorgu <xref:System.Xml.XPath.XPathNavigator> bulmak ve ifade tarafından tanımlanan düğümleri işlemek için kullanır.  
  
 Aşağıdaki örnek, uygulama özel bağlamı sınıfının türetilen gösterir <xref:System.Xml.Xsl.XsltContext>. Kod açıklamaları sınıf üyeleri ve kullanımlarını özel işlevlerinde açıklanmaktadır. Bu kod kesimi işlevi ve değişken uygulamaları ve bu uygulamaları kullanan örnek bir uygulama izleyin.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextFunction>. Uygulayan sınıfa <xref:System.Xml.Xsl.IXsltContextFunction> çözümler ve kullanıcı tanımlı işlevler yürütür. Bu örnek bildirimi tarafından tanımlanan işlevi kullanır: `private int CountChar(string title, char charTocount)`.  
  
 Kod açıklamaları sınıf üyeleri açıklanmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextVariable>. Bu sınıf, çalışma zamanında kullanıcı tarafından tanımlanan değişkenler XPath sorgu ifadelerinde başvuru çözümler. Bu sınıfın bir örneği oluşturulur ve geçersiz kılınan tarafından döndürülen <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> yöntemi özel <xref:System.Xml.Xsl.XsltContext> sınıfı.  
  
 Kod açıklamaları sınıf üyeleri açıklanmaktadır.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Kapsamdaki önceki sınıf tanımlarını aşağıdaki kod öğelerini karakter sayısı için özel işlevi kullanır `Tasks.xml` belge. Kod açıklamaları açıklayan özel işlevi derler ve karşı çalışan kod `Tasks.xml` belge.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Bu örnekte aşağıdaki XML verileri kullanır.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
