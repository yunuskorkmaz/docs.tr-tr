---
title: 'Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: dc4fb2d5f0c48c077d2ff7ca5e5269ce5cba71e5
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400494"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama
Bu örnekte, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] <xref:System.Windows.Data.XmlDataProvider>kullanılarak verilerin nasıl bağlanacağı gösterilmektedir.  
  
 İle, uygulamanızda veri bağlama aracılığıyla erişilebilen temel veriler herhangi bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] düğüm ağacı olabilir. <xref:System.Windows.Data.XmlDataProvider> Diğer bir deyişle, bir <xref:System.Windows.Data.XmlDataProvider> bağlama kaynağı olarak herhangi bir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] düğüm ağacını kullanmanın kolay bir yolunu sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, veriler, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.FrameworkElement.Resources%2A> bölüm içinde doğrudan bir *veri Adası* olarak katıştırılır. Bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri Adası, `<x:XData>` etiketlerde sarmalanmış olmalı ve her zaman tek bir kök düğüme sahip olmalıdır ve bu örnekte *Stok* vardır.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Verilerin kök düğümü, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanını boş bir dizeye ayarlayan bir **xmlns** özniteliğine sahiptir. Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfada satır içi bir veri adasına XPath sorguları uygulama gereksinimidir. Bu satır içi durumda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ve bu nedenle veri Adası <xref:System.Windows> ad alanını devralır. Bu nedenle, XPath sorgularının <xref:System.Windows> ad alanı tarafından nitelendirilmeden ve sorguları hatalı yönlendirerek ad alanını boş olarak ayarlamanız gerekir.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Bu örnekte gösterildiği gibi, öznitelik sözdiziminde aynı bağlama bildirimini oluşturmak için özel karakterleri düzgün bir şekilde atlamanız gerekir. Daha fazla bilgi için bkz. [XML karakter varlıkları ve xaml](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Bu örnek çalıştırıldığında aşağıdaki öğeleri gösterir. Bunlar, *hisse senedi* değeri "*Out*" veya *sayı* değeri 3 veya daha büyük ya da 8 ' e eşit olan *kitaplar* altındaki tüm öğelerin unvanına ait *başlıktır*. Üzerinde ayarlanan <xref:System.Windows.Data.XmlDataProvider.XPath%2A> değer yalnızca *Books* öğelerinin gösterilmesini (temelde bir filtre ayarlaması) gerektiğini gösterdiği için, <xref:System.Windows.Data.XmlDataProvider> hiçbir *CD* öğesinin döndürülmediğine dikkat edin.  
  
 ![Dört kitapların başlığını gösteren XPath örneği ekran görüntüsü.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Bu örnekte <xref:System.Windows.Data.Binding.XPath%2A> , içindeki <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.DataTemplate> bağlamasının "*title*" olarak ayarlandığı için kitap başlıkları görüntülenir. *ISBN*gibi bir özniteliğin değerini göstermek istiyorsanız, bu <xref:System.Windows.Data.Binding.XPath%2A> değeri "`@ISBN`" olarak ayarlamanız gerekir.  
  
 İçindeki[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **XPath** özellikleri, XmlNode. SelectNodes yöntemi tarafından işlenir. Farklı sonuçlar almak için **XPath** sorgularını değiştirebilirsiniz. Önceki örnekten bağlantılı <xref:System.Windows.Data.Binding.XPath%2A> <xref:System.Windows.Controls.ListBox> sorgu için bazı örnekler aşağıda verilmiştir:  
  
- `XPath="Book[1]"`, ilk kitap öğesini döndürür ("XML eyleminde"). **XPath** dizinlerinin 0 değil 1 ' i temel alan olduğunu unutmayın.  
  
- `XPath="Book[@*]"`Tüm bir öznitelik ile tüm kitap öğelerini döndürür.  
  
- `XPath="Book[last()-1]"`, ikinciden son kitap öğesine ("Microsoft .NET giriş") döndürür.  
  
- `XPath="*[position()>3]"`ilk 3 hariç tüm kitap öğelerini döndürür.  
  
 Bir **XPath** sorgusu çalıştırdığınızda, bir <xref:System.Xml.XmlNode> XMLNodes listesi veya bir listesini döndürür. <xref:System.Xml.XmlNode>, ortak dil çalışma zamanı (CLR) özelliklerine bağlamak için <xref:System.Windows.Data.Binding.Path%2A> özelliğini kullanabileceğiniz anlamına gelen bir ortak dil çalışma zamanı (CLR) nesnesidir. Önceki örneği yeniden deneyin. Örneğin geri kalanı aynı kalırsa ve <xref:System.Windows.Controls.TextBlock> bağlamayı aşağıdaki şekilde değiştirirseniz, <xref:System.Windows.Controls.ListBox>' de döndürülen XMLNodes 'nin adlarını görürsünüz. Bu durumda, döndürülen tüm düğümlerin adı "*Book*" dır.  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Bazı uygulamalarda, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerin tam içeriğinin derleme zamanında bilinmesi gerektiğinden, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın kaynağı içine veri Adası olarak eklemek kullanışlı olabilir. Bu nedenle, verileri bir dış [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyadan almak aşağıdaki örnekte olduğu gibi desteklenir:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Veriler uzak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bir dosyada yer alıyorsa, <xref:System.Windows.Data.XmlDataProvider.Source%2A> özniteliğe aşağıdaki şekilde uygun [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] bir şekilde atayarak verilere erişim tanımlayabilirsiniz: [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
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
