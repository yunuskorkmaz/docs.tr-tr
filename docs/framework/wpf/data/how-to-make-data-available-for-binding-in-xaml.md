---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 09a6fca48c06efca6f06b9e0617de9095197bd17
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399001"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu konuda çeşitli şekillerde yapabilirsiniz verileri için kullanılabilir bağlama anlatılmaktadır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], uygulamanızın ihtiyaçlarına bağlı olarak.  
  
## <a name="example"></a>Örnek  
 Varsa bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] gelen bağlamak istediğiniz nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yapabilirsiniz nesne kullanılabilir bir kaynak olarak tanımlayan ve bu bağlama için tek yolu bir `x:Key`. Aşağıdaki örnekte bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`. `Person` Nesne (vurgulanan gösterilen satırda içeren `<src>` öğesi) adı verilen ad alanında tanımlanan `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Ardından bağlayabilirsiniz <xref:System.Windows.Controls.TextBlock> denetimi nesneye [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vurgulanan satır gibi içeren `<TextBlock>` öğesi gösterir. 
  
 Alternatif olarak, <xref:System.Windows.Data.ObjectDataProvider> aşağıdaki örnekteki gibi bir sınıfı:  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Bağlama tanımlar içeren vurgulanan satırın aynı şekilde `<TextBlock>` öğesi gösterir.  
  
 Bu örnekte sonuç aynıdır: sahip olduğunuz bir <xref:System.Windows.Controls.TextBlock> metin içerikli `Joe`. Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıf özelliği bir yöntemin sonucu için bağlama gibi işlevler sağlar. Kullanmayı da tercih edebilirsiniz <xref:System.Windows.Data.ObjectDataProvider> sağladığı işlevsellik gerekiyorsa sınıfı.  
  
 Önceden oluşturulmuş bir nesne için bağlıyorsanız, ancak ayarlamanız gerekir `DataContext` kodda, aşağıdaki örnekte olduğu gibi.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri bağlamasını kullanma <xref:System.Windows.Data.XmlDataProvider> sınıfı [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri bağlamasını kullanma <xref:System.Windows.Data.ObjectDataProvider> sınıfı [XML sorgu sonuçları için XDocument, XElement veya LINQ'ya bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Dosyalar bağladığınız veri birçok yolu hakkında bilgi için bkz. [bağlama kaynağı belirtme](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Hangi veri türlerini adlarınıza bağlayabileceğiniz veya kendi uygulama hakkında bilgi için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağlama nesnelerini görmek [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
