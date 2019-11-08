---
title: 'Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740581"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama
## <a name="example"></a>Örnek
 Bu örnek, XML bağlama kaynağınızda belirtilen ad alanlarının nasıl işleneceğini gösterir.

 XML verilerinizde aşağıdaki XML ad alanı tanımı varsa:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Aşağıdaki örnekte olduğu gibi, ad alanını bir <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>eşlemek için <xref:System.Windows.Data.XmlNamespaceMapping> öğesini kullanabilirsiniz. Ardından, XML ad alanına başvurmak için <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> kullanabilirsiniz. Bu örnekteki <xref:System.Windows.Controls.ListBox> *başlık* ve *DC:* her *öğenin*tarihini görüntüler.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Belirttiğiniz <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> XML kaynağında kullanılan ile eşleşmesi gerekmez; ön ek XML kaynağındaki önek değişirse eşlemenin hala işe yarar.

 Bu örnekte, XML verileri bir Web hizmetinden gelir, ancak <xref:System.Windows.Data.XmlNamespaceMapping> öğesi, gömülü bir dosyadaki satır içi XML veya XML verileriyle de birlikte kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
