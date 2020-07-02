---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
description: Windows Presentation Foundation (WPF) uygulamasındaki uygulamanızın gereksinimlerine göre verileri kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar bulun.
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620800"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu konuda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , uygulamanızın gereksinimlerine bağlı olarak verileri bağlama için kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar ele alınmaktadır.  
  
## <a name="example"></a>Örnek  
 ' Den bağlamak istediğiniz ortak dil çalışma zamanı (CLR) nesneniz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , nesneyi bağlama için kullanılabilir hale getirmenin bir yolu kaynak olarak tanımlamak ve ona vermektir `x:Key` . Aşağıdaki örnekte, bir `Person` String özelliği adlı bir nesneniz vardır `PersonName` . `Person`Nesnesi (öğesi içeren vurgulanmış olan satırdaki `<src>` ) adlı ad alanında tanımlanır `SDKSample` .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Daha sonra <xref:System.Windows.Controls.TextBlock> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , öğeyi içeren vurgulanan çizgi gösterildiği gibi denetimi içindeki nesnesine bağlayabilirsiniz `<TextBlock>` .
  
 Alternatif olarak, <xref:System.Windows.Data.ObjectDataProvider> Aşağıdaki örnekte olduğu gibi sınıfını kullanabilirsiniz:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Bağlamayı, öğeyi içeren vurgulanmış çizgi ile aynı şekilde tanımlarsınız `<TextBlock>` .  
  
 Bu örnekte, sonuç aynıdır: metin içeriğine sahip olduğunuz bir <xref:System.Windows.Controls.TextBlock> `Joe` . Ancak sınıfı, <xref:System.Windows.Data.ObjectDataProvider> bir yöntemin sonucuna bağlama özelliği gibi işlevler sağlar. <xref:System.Windows.Data.ObjectDataProvider>Sınıfının sağladığı işlevselliğe gereksinim duyuyorsanız, sınıfını kullanmayı tercih edebilirsiniz.  
  
 Ancak, zaten oluşturulmuş bir nesneye bağlıyorsanız, `DataContext` Aşağıdaki örnekte olduğu gibi kodu olarak ayarlamanız gerekir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Sınıfını kullanarak bağlamak üzere XML verilerine erişmek için <xref:System.Windows.Data.XmlDataProvider> bkz. [XmlDataProvider ve XPath SORGULARıNı kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Sınıfını kullanarak bağlamak üzere XML verilerine erişmek için <xref:System.Windows.Data.ObjectDataProvider> bkz. [XML sorgu sonuçları için XDocument, XElement veya LINQ 'a bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Bağladığınız verileri belirtebileceğiniz birçok yol hakkında daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md). Bağlayacağınız veri türleri veya bağlama için kendi ortak dil çalışma zamanı (CLR) nesnelerinizi uygulama hakkında daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
