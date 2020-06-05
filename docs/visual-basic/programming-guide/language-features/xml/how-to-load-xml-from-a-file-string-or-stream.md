---
title: 'Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392294"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme (Visual Basic)

Çeşitli yöntemler kullanarak, [XML değişmez değerleri](../../../language-reference/xml-literals/index.md) oluşturabilir ve bunları bir dosya, dize veya akış gibi bir dış kaynaktaki içerikle doldurabilirsiniz. Bu yöntemler aşağıdaki örneklerde gösterilmiştir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Bir dosyadan XML yüklemek için

Bir veya nesnesi gibi bir XML sabit değerini bir dosyadan doldurmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> `Load` yöntemini kullanın. Bu yöntem, giriş olarak bir dosya yolu, metin akışı veya XML akışı alabilir.

Aşağıdaki kod örneği, <xref:System.Xml.Linq.XDocument.Load%28System.String%29> <xref:System.Xml.Linq.XDocument> bir nesneyi bir metın dosyasından XML ile doldurmak için yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Bir dizeden XML yüklemek için

Bir veya nesnesi gibi bir XML sabit değerini <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> bir dizeden doldurmak için `Parse` yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument> BIR dizeden XML ile bir nesneyi doldurmak için yönteminin kullanımını gösterir.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Akıştan XML yüklemek için

Bir veya nesnesi gibi bir XML sabit değerini bir akıştan doldurmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> `Load` yöntemini veya <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Aşağıdaki kod örneği, bir <xref:System.Xml.Linq.XNode.ReadFrom%2A> nesneyi XML AKıŞıNDAN XML ile doldurmak için yönteminin kullanımını gösterir <xref:System.Xml.Linq.XDocument> .

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML Değişmez Değerleri](../../../language-reference/xml-literals/index.md)
- [XML](index.md)
- [Visual Basic'de XML'i Düzenleme](manipulating-xml.md)
