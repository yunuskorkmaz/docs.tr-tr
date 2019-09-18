---
title: 'Nasıl yapılır: Bir dosya, dize veya akıştan XML yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054174"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Nasıl yapılır: Bir dosya, dize veya akıştan XML yükleme (Visual Basic)

Çeşitli yöntemler kullanarak, [XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) oluşturabilir ve bunları bir dosya, dize veya akış gibi bir dış kaynaktaki içerikle doldurabilirsiniz. Bu yöntemler aşağıdaki örneklerde gösterilmiştir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Bir dosyadan XML yüklemek için

Bir <xref:System.Xml.Linq.XElement> `Load` veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dosyadan doldurmak için yöntemini kullanın. Bu yöntem, giriş olarak bir dosya yolu, metin akışı veya XML akışı alabilir.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XDocument.Load%28System.String%29> <xref:System.Xml.Linq.XDocument> nesneyi bir metin dosyasından XML ile doldurmak için yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Bir dizeden XML yüklemek için

Bir <xref:System.Xml.Linq.XElement> `Parse` veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir dizeden doldurmak için yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği bir dizeden XML ile bir <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument> nesneyi doldurmak için yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Akıştan XML yüklemek için

Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi gibi bir XML sabit değerini bir akıştan doldurmak için `Load` yöntemini veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XNode.ReadFrom%2A> <xref:System.Xml.Linq.XDocument> nesneyi XML akışından XML ile doldurmak için yönteminin kullanımını gösterir.

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
