---
title: 'Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 47ce0d951df39c7b60aa2a543baf845f5471de6c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460311"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama
## <a name="example"></a>Örnek
 Bu örnek, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] bağlama kaynağınızda belirtilen ad alanlarının nasıl işleneceğini gösterir.

 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileriniz aşağıdaki [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı tanımına sahipse:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Aşağıdaki örnekte olduğu gibi, ad alanını bir <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>eşlemek için <xref:System.Windows.Data.XmlNamespaceMapping> öğesini kullanabilirsiniz. Daha sonra, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanına başvurmak için <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> kullanabilirsiniz. Bu örnekteki <xref:System.Windows.Controls.ListBox> *başlık* ve *DC:* her *öğenin*tarihini görüntüler.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Belirttiğiniz <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynağında kullanılan ile eşleşmesi gerekmez; önek [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynak üzerinde değişirse eşlemenin hala işe yarar.

 Bu örnekte, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri bir Web hizmetinden gelir, ancak <xref:System.Windows.Data.XmlNamespaceMapping> öğesi, gömülü bir dosyadaki satır içi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veya [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerle de birlikte da geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
