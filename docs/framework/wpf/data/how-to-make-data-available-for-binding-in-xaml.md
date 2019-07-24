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
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401497"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu konuda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], uygulamanızın gereksinimlerine bağlı olarak verileri bağlama için kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar ele alınmaktadır.  
  
## <a name="example"></a>Örnek  
 ' Den [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bağlamak istediğiniz ortak dil çalışma zamanı (CLR) nesneniz varsa, nesneyi bağlama için kullanılabilir hale getirmenin bir yolu kaynak olarak tanımlamak ve `x:Key`ona vermektir. Aşağıdaki örnekte, bir String özelliği adlı `Person` `PersonName`bir nesneniz vardır. Nesnesi ( `<src>` öğesi içeren vurgulanmış olan satırdaki) adlı `SDKSample`ad alanında tanımlanır. `Person`  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Daha sonra, <xref:System.Windows.Controls.TextBlock> `<TextBlock>` öğeyi içeren vurgulanan çizgi gösterildiği gibi denetimi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]içindeki nesnesine bağlayabilirsiniz. 
  
 Alternatif olarak, aşağıdaki örnekte olduğu <xref:System.Windows.Data.ObjectDataProvider> gibi sınıfını kullanabilirsiniz:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Bağlamayı, `<TextBlock>` öğeyi içeren vurgulanmış çizgi ile aynı şekilde tanımlarsınız.  
  
 Bu örnekte, sonuç aynıdır: metin içeriğine <xref:System.Windows.Controls.TextBlock> `Joe`sahip olduğunuz bir. <xref:System.Windows.Data.ObjectDataProvider> Ancak sınıfı, bir yöntemin sonucuna bağlama özelliği gibi işlevler sağlar. Sınıfının sağladığı işlevselliğe gereksinim duyuyorsanız, <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanmayı tercih edebilirsiniz.  
  
 Ancak, zaten oluşturulmuş bir nesneye bağlıyorsanız, aşağıdaki örnekte olduğu gibi kodu olarak ayarlamanız `DataContext` gerekir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Sınıfını kullanarak bağlama için verilere erişmek [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] üzere bkz. [XmlDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama.](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md) <xref:System.Windows.Data.XmlDataProvider> Sınıfını kullanarak bağlama için verilere erişmek [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] üzere, bkz. [XML sorgu sonuçları için XDocument, XElement veya LINQ 'a bağlama.](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md) <xref:System.Windows.Data.ObjectDataProvider>  
  
 Bağladığınız verileri belirtebileceğiniz birçok yol hakkında daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md). Bağlayacağınız veri türleri veya bağlama için kendi ortak dil çalışma zamanı (CLR) nesnelerinizi uygulama hakkında daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
