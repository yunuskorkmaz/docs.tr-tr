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
ms.openlocfilehash: 0d68eb40b60481709ff2852a643908025e2e43ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512339"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama
Bu örnek XML verilerine bağlama yapmayı gösteren bir <xref:System.Windows.Controls.ItemsControl> kullanarak <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML kodu tanımlayan bir <xref:System.Windows.Controls.ItemsControl> ve veri türü için veri şablonu içerir `Planet` içinde `http://planetsNS` XML ad alanı. Bir ad alanı kaplayan bir XML veri türü, küme ayraçları içine ad alanını içermeli ve bir XAML işaretleme uzantısı yeri görünebilir görüntülenirse, ad alanı ile bir küme ayracı kaçış sırası gelmelidir. Bu kod karşılık gelen dinamik özellikleri bağlar <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerinin <xref:System.Xml.Linq.XElement> sınıfı. Dinamik özellikler yöntemlerin adlarını paylaşan dinamik özellikleri bağlamak XAML etkinleştirin. Daha fazla bilgi için bkz. [LINQ to XML dinamik özellikleri](/visualstudio/designers/linq-to-xml-dynamic-properties). XML için varsayılan ad alanı bildiriminin nasıl öznitelik adları için geçerli değildir dikkat edin.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Aşağıdaki C# kod çağrıları <xref:System.Xml.Linq.XDocument.Load%2A> ve yığın paneli veri bağlamı adlı bir öğe tüm alt öğelerini ayarlar `SolarSystemPlanets` içinde `http://planetsNS` XML ad alanı.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML verileri, XAML kullanarak kaynak olarak depolanabilir <xref:System.Windows.Data.ObjectDataProvider>. Tam bir örnek için bkz. [L2DBForm.xaml kaynak kodu](https://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Aşağıdaki örnek kod için bir nesne kaynak veri bağlamı nasıl ayarlayabileceğinizi gösterir.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Eşleyen dinamik Özellikler <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> XAML içinde esneklik sağlar. Kodunuz LINQ to XML sorgu sonuçları da bağlayabilirsiniz. Bu örnekte öğe değeri tarafından istenen sorgu sonuçlarına bağlar.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [LINQ to XML Kullanarak WPF Verilerini Bağlama Örneği](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [LINQ to XML Dinamik Özellikleri](/visualstudio/designers/linq-to-xml-dynamic-properties)
