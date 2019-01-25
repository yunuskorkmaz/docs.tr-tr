---
title: 'Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: bd2a156920057dc197fabbaa46e3a2d886a1b322
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600355"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Nasıl yapılır: XML Ad Alanlarını Kullanarak Veri Bağlama
## <a name="example"></a>Örnek  
 Bu örnek belirtilen ad alanlarını nasıl ele alınacağını gösterir, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] bağlama kaynağı.  
  
 Varsa, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri içeren aşağıdaki [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı tanımı:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Kullanabileceğiniz <xref:System.Windows.Data.XmlNamespaceMapping> öğesi ad alanına eşlemek için bir <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, aşağıdaki örnekte olduğu gibi. Ardından <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> başvurmak için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı. <xref:System.Windows.Controls.ListBox> Bu örnekte görüntüler *başlık* ve *dc:date* her *öğesi*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Unutmayın <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> belirtmeniz gerekmez kullanılanla eşleşen [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] önek değişirse; kaynak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynak eşleştirme hala çalışıyor.  
  
 Bu örnekte, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veriler bir web hizmetinden gelir ancak <xref:System.Windows.Data.XmlNamespaceMapping> öğesi, satır içi ile de çalışır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veya [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] katıştırılmış dosyasındaki verileri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
