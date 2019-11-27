---
title: 'Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330954"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)

Çeşitli yöntemler kullanarak, [XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) oluşturabilir ve bunları bir dosya, dize veya akış gibi bir dış kaynaktaki içerikle doldurabilirsiniz. Bu yöntemler aşağıdaki örneklerde gösterilmiştir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Bir dosyadan XML yüklemek için

Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dosyadan doldurmak için `Load` metodunu kullanın. Bu yöntem, giriş olarak bir dosya yolu, metin akışı veya XML akışı alabilir.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XDocument> nesnesini bir metin dosyasından XML ile doldurmak için <xref:System.Xml.Linq.XDocument.Load%28System.String%29> yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Bir dizeden XML yüklemek için

Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dizeden doldurmak için `Parse` yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XDocument> nesnesini bir dizeden XML ile doldurmak için <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Akıştan XML yüklemek için

Bir akıştan <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit listesini doldurmak için `Load` yöntemini veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XDocument> nesnesini XML akışından XML ile doldurmak için <xref:System.Xml.Linq.XNode.ReadFrom%2A> yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic XML 'yi düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
