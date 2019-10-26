---
title: "Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920120"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama

Bu örnek, <xref:System.Xml.Linq.XDocument>kullanarak bir <xref:System.Windows.Controls.ItemsControl> XML verilerinin nasıl bağlanacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki XAML kodu bir <xref:System.Windows.Controls.ItemsControl> tanımlar ve `http://planetsNS` XML ad alanında `Planet` türündeki veriler için bir veri şablonu içerir. Bir ad alanını kaplayan bir XML veri türü, küme ayracı içine ad alanını içermelidir ve bir XAML biçimlendirme uzantısının görünebileceği yerde görünürse, ad alanından önce ayraç kaçış dizisi ile önce gelmelidir. Bu kod, <xref:System.Xml.Linq.XElement> sınıfının <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerine karşılık gelen dinamik özelliklere bağlanır. Dinamik özellikler, XAML 'nin yöntemlerin adlarını paylaşan dinamik özelliklere bağlamasını sağlar. Daha fazla bilgi için bkz. [LINQ to XML dinamik özellikler](linq-to-xml-dynamic-properties.md). XML için varsayılan ad alanı bildiriminin öznitelik adlarına nasıl uygulanmadığından dikkat edin.

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

Aşağıdaki C# kod<xref:System.Xml.Linq.XDocument.Load%2A>çağırır ve yığın paneli veri BAĞLAMıNı`http://planetsNS`XML ad alanındaki`SolarSystemPlanets`adlı öğenin tüm alt öğeleri olarak ayarlar.

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

XML verileri, <xref:System.Windows.Data.ObjectDataProvider>kullanarak bir XAML kaynağı olarak depolanabilir. Tüm örnek için bkz [. L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md). Aşağıdaki örnek, kodun veri bağlamını bir nesne kaynağına nasıl ayarlayagösterdiğini gösterir.

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

<xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> eşlenen dinamik özellikler XAML içinde esneklik sağlar. Kodunuz Ayrıca bir LINQ for XML sorgusu sonuçlarına bağlanabilir. Bu örnek, bir öğe değeri tarafından sıralanan sorgu sonuçlarına bağlanır.

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış](wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML Kullanarak WPF Verilerini Bağlama Örneği](linq-to-xml-data-binding-sample.md)
- [LINQ to XML Dinamik Özellikleri](linq-to-xml-dynamic-properties.md)
