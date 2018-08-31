---
title: 'Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258410"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)
Oluşturabileceğiniz [XML sabit değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) ve bunları bir dosyaya, bir dize veya bir akışa gibi bir dış kaynaktan içeriğiyle çeşitli yöntemler kullanarak doldurabilirsiniz. Bu yöntemler aşağıdaki örneklerde gösterilmiştir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>Bir dosyadan XML yüklenmedi  
  
-   XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> dosyadan, kullanım nesne `Load` yöntemi. Bu yöntem, giriş olarak bir dosya yolu, metin akışına veya XML akışı alabilir.  
  
     Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XDocument.Load%28System.String%29> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir metin dosyasındaki XML nesne.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>Bir dizedeki XML yüklenmedi  
  
-   XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir dizeden nesne `Parse` yöntemi.  
  
     Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> XML ile nesneden bir dize.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>Bir akıştan XML yükleme için  
  
-   XML değişmez değer gibi doldurmak için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> kullanabileceğiniz bir akıştan nesne `Load` yöntemi veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki kod örneği, kullanımını gösterir <xref:System.Xml.Linq.XNode.ReadFrom%2A> doldurmak için yöntemi bir <xref:System.Xml.Linq.XDocument> bir XML akışı XML'den nesne.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Visual Basic'de XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
