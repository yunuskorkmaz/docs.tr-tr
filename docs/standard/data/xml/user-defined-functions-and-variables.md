---
title: Kullanıcı Tanımlı İşlevler ve Değişkenler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2ce474dac44de1ac72811ecd3bc294ba57ce40a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952028"
---
# <a name="user-defined-functions-and-variables"></a>Kullanıcı Tanımlı İşlevler ve Değişkenler
<xref:System.Xml.XPath.XPathNavigator> Sınıfı ile etkileşim kurmak için kullanılan yöntemler kümesi sağlar <xref:System.Xml.XPath.XPathDocument> veri. Uzantı işlevleri ve değişkenler kullanmak için XPath sorgu ifadeleri tarafından uygulayarak standart XPath işlevleri destekleyebilirsiniz. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Yöntem türetilmiş bir kullanıcı tanımlı bağlam kabul <xref:System.Xml.Xsl.XsltContext>. Kullanıcı tanımlı işlevlerle özel bağlam tarafından çözümlenir.  
  
 Uzantı işlevleri ve değişkenler XML ekleme saldırılarını önleme yararlı olabilir. Bu senaryolarda kullanıcı girişi özel değişkenlere atanır ve işlem yönergeleri ile birleştirilmiş değil ham giriş olarak uzantı işlevleri tarafından işlenir. Böylece, yalnızca XML verileri tasarımcı tarafından hedeflenen işlevi görür kullanıcı girişi uzantı işlevleri ve değişkenler içerir.  
  
 Uzantıları kullanmak için özel bir uygulama <xref:System.Xml.Xsl.XsltContext> arabirimler sınıfıyla <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantı işlevleri ve değişkenler destekler. Bir <xref:System.Xml.XPath.XPathExpression> ile kullanıcı girişi ekler, <xref:System.Xml.Xsl.XsltArgumentList> özel <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Derlenmiş temsil sorgu <xref:System.Xml.XPath.XPathNavigator> bulmak ve ifade tarafından tanımlanan düğümleri işlemek için kullanır.  
  
 Aşağıdaki örnek, bir özel bağlamı sınıfının uygulaması türetilen gösterir <xref:System.Xml.Xsl.XsltContext>. Kod açıklamaları, sınıf üyeleri ve kullanımları özel işlevler açıklanmaktadır. Bu kod kesimi işlevde ve değişken uygulamaları ve bu uygulamaları kullanan örnek bir uygulama izleyin.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextFunction>. Uygulayan sınıfa <xref:System.Xml.Xsl.IXsltContextFunction> çözümler ve kullanıcı tanımlı işlevleri yürütür. Bu örnek bildirim tarafından tanıtılan işlevi kullanır: `private int CountChar(string title, char charTocount)`.  
  
 Kod açıklamaları sınıf üyelerini açıklar.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Aşağıdaki kod uygulayan <xref:System.Xml.Xsl.IXsltContextVariable>. Bu sınıf, çalışma zamanında kullanıcı tanımlı değişkenler XPath sorgu ifadelerinde başvuruları çözümleniyor. Bu sınıfın bir örneği oluşturulur ve geçersiz kılınan tarafından döndürülen <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> yöntemi özel <xref:System.Xml.Xsl.XsltContext> sınıfı.  
  
 Kod açıklamaları sınıf üyelerini açıklar.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Kapsamdaki önceki sınıfı tanımlarında olduğu aşağıdaki kod öğelerini karakter sayısı için özel işlevi kullanır `Tasks.xml` belge. Kod açıklamaları açıklayan özel işlev derler ve onu karşı çalışan kodu `Tasks.xml` belge.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Bu örnek aşağıdaki XML verileri kullanır.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
