---
title: 'Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 9a6869b84746081df7917aca32042002b8b044c5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371352"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama
Bu örnek nasıl bağlanacağını gösterir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] verileri kullanarak bir <xref:System.Windows.Data.XmlDataProvider>.  
  
 İle bir <xref:System.Windows.Data.XmlDataProvider>, temel alınan veri bağlama, uygulamanızda aracılığıyla erişilebilen veriler herhangi bir ağacını olabilir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] düğümleri. Diğer bir deyişle, bir <xref:System.Windows.Data.XmlDataProvider> herhangi bir ağacını kullanmak için kullanışlı bir yol sağlayan [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] düğümleri bağlama kaynağı olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, verileri doğrudan olarak gömülü bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *veri adası* içinde <xref:System.Windows.FrameworkElement.Resources%2A> bölümü. Bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri adası sarmalanmış, içinde `<x:XData>` etiketleri ve her zaman olan bir tek kök düğümüne sahip *Envanter* Bu örnekte.  
  
> [!NOTE]
>  Kök düğümü [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilere sahip bir **xmlns** ayarlar özniteliği [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı boş bir dize. Bu XPath sorguları içinde satır içi bir veri adası uygulamak için bir zorunluluktur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası. Bu satır içi durumda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ve veri adası, böylece devralan <xref:System.Windows> ad alanı. Bu nedenle, ad alanı boş XPath sorguları tarafından nitelendirilen tutmak için ayarlamanız gerekir <xref:System.Windows> sorgular misdirect ad alanı.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Bu örnekte gösterildiği gibi nitelik söz dizimindeki aynı bağlama bildirimi oluşturmak için özel karakterleri düzgün kaçışını yapmanız gerekir. Daha fazla bilgi için [XML karakter varlıkları ve XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Bu örneği çalıştırdığınızda aşağıdaki öğeleri gösterir. Bunlar *başlık*s tüm öğelerin altında *Books* ile ya da bir *hisse senedi* değerini "*kullanıma*" veya *numarası* değeri 3 veya daha büyük veya eşittir 8. Dikkat hiçbir *CD* çünkü öğeleri döndürülür <xref:System.Windows.Data.XmlDataProvider.XPath%2A> değerinin ayarlanmış <xref:System.Windows.Data.XmlDataProvider> gösterir, yalnızca *Books* öğeleri ortaya (aslında bir filtre ayarlayarak).  
  
 ![XPath örnek](./media/xpathexample.PNG "XPathExample")  
  
 Bu örnekte, bir kitap adları görüntülenir, çünkü <xref:System.Windows.Data.Binding.XPath%2A> , <xref:System.Windows.Controls.TextBlock> bağlama <xref:System.Windows.DataTemplate> ayarlanmış "*başlık*". Gibi bir özniteliğin değerini görüntülemek istiyorsanız *ISBN*, ayarlarsınız <xref:System.Windows.Data.Binding.XPath%2A> değerini "`@ISBN`".  
  
 **XPath** özelliklerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XmlNode.SelectNodes yöntemi tarafından işlenir. Değiştirebileceğiniz **XPath** farklı sonuçlar elde etmek için sorgular. İşte bazı örnekler için <xref:System.Windows.Data.Binding.XPath%2A> sorgu sınır <xref:System.Windows.Controls.ListBox> önceki örnekte:  
  
-   `XPath="Book[1]"` ilk kitap öğesi eylem ("XML") döndürür. Unutmayın **XPath** dizinleri, 1, 0 bağlıdır.  
  
-   `XPath="Book[@*]"` herhangi bir özniteliği tüm kitap öğelerini döndürür.  
  
-   `XPath="Book[last()-1]"` İkinci son kitap öğesi ("Karşınızda Microsoft .NET") döndürür.  
  
-   `XPath="*[position()>3]"` ilk 3 hariç tüm kitap öğeleri döndürür.  
  
 Çalıştırdığınızda bir **XPath** döndürür, sorgu bir <xref:System.Xml.XmlNode> veya XmlNodes listesi. <xref:System.Xml.XmlNode> olan bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kullanabileceğiniz anlamına gelir, nesne <xref:System.Windows.Data.Binding.Path%2A> özelliğine bağlamak için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellikleri. Önceki örnek yeniden göz önünde bulundurun. Örneğin geri kalanı aynı kalır ve değiştirirseniz <xref:System.Windows.Controls.TextBlock> aşağıdaki bağlama, döndürülen XmlNodes içinde adlarını görürsünüz <xref:System.Windows.Controls.ListBox>. Bu durumda, döndürülen tüm düğümlerin adıdır "*kitap*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Bazı uygulamalarda katıştırma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynağı içindeki bir veri adası olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] verilerin tam içeriği, derleme zamanında bilinen gerekir çünkü sayfa kullanışsız olabilir. Bu nedenle, dış veri alma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya da desteklenir, aşağıdaki örnekte olduğu gibi:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Varsa [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veriler uzak yer [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyası tanımlarsınız erişim verilere uygun bir atayarak [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için <xref:System.Windows.Data.XmlDataProvider.Source%2A> özniteliğini aşağıdaki gibi:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Data.ObjectDataProvider>
- [XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
