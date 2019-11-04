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
ms.openlocfilehash: 2bfd9809a6ad487a7e706366dc6bce8fe951c940
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459753"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu konuda, uygulamanızın ihtiyaçlarına bağlı olarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]verileri bağlama için kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar ele alınmaktadır.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bağlamak istediğiniz ortak dil çalışma zamanı (CLR) nesneniz varsa, nesneyi bağlama için kullanılabilir hale getirmenin bir yolu kaynak olarak tanımlamak ve buna bir `x:Key`vermektir. Aşağıdaki örnekte, `PersonName`adlı dize özelliği olan bir `Person` nesneniz vardır. `Person` nesnesi (`<src>` öğesini içeren vurgulanan satırdaki), `SDKSample`adlı ad alanında tanımlanmıştır.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Daha sonra <xref:System.Windows.Controls.TextBlock> denetimini, `<TextBlock>` öğesi içeren vurgulanmış çizgi gibi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nesneye bağlayabilirsiniz. 
  
 Alternatif olarak, aşağıdaki örnekte olduğu gibi <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanabilirsiniz:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Bağlamayı, `<TextBlock>` öğesi içeren vurgulanmış çizgi ile aynı şekilde tanımlarsınız.  
  
 Bu örnekte, sonuç aynıdır: metin içeriğine sahip bir <xref:System.Windows.Controls.TextBlock> `Joe`. Ancak <xref:System.Windows.Data.ObjectDataProvider> sınıfı, bir yöntemin sonucuna bağlama özelliği gibi işlevler sağlar. Sağladığı işlevselliğe ihtiyacınız varsa <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanmayı seçebilirsiniz.  
  
 Ancak, zaten oluşturulmuş bir nesneye bağlıyorsanız, aşağıdaki örnekte olduğu gibi koddaki `DataContext` ayarlamanız gerekir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <xref:System.Windows.Data.XmlDataProvider> sınıfını kullanarak bağlama için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerine erişmek için bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanarak bağlama için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerine erişmek için bkz. [XML sorgu sonuçları Için XDocument, XElement veya LINQ 'A bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Bağladığınız verileri belirtebileceğiniz birçok yol hakkında daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md). Bağlayacağınız veri türleri veya bağlama için kendi ortak dil çalışma zamanı (CLR) nesnelerinizi uygulama hakkında daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
