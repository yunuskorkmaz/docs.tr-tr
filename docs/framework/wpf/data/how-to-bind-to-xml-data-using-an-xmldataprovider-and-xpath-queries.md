---
title: 'Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: d92b01c453a9e07a5d4a6d1900d54e8c86210041
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005688"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama
Bu örnek, bir <xref:System.Windows.Data.XmlDataProvider> kullanarak [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] verilerine nasıl bağlanılacağını gösterir.  
  
 @No__t-0 ile uygulamanızdaki veri bağlama aracılığıyla erişilebilen temel veriler, herhangi bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] düğüm ağacı olabilir. Diğer bir deyişle, <xref:System.Windows.Data.XmlDataProvider>, [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] düğümlerin herhangi bir ağacını bağlama kaynağı olarak kullanmak için uygun bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, veriler, <xref:System.Windows.FrameworkElement.Resources%2A> bölümü içinde [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *veri Adası* olarak doğrudan katıştırılır. @No__t-0 veri Adası `<x:XData>` etiketlerinde sarmalanmış olmalıdır ve her zaman bu örnekte *Envanter* olan tek bir kök düğümü olmalıdır.  
  
> [!NOTE]
> @No__t-0 verilerinin kök düğümü, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanını boş bir dizeye ayarlayan bir **xmlns** özniteliğine sahiptir. Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında satır içi bir veri Adası için XPath sorguları uygulama gereksinimidir. Bu satır içi durumda, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve bu nedenle veri Adası, <xref:System.Windows> ad alanını devralır. Bu nedenle, XPath sorgularının <xref:System.Windows> ad alanı tarafından nitelendirilmeden tutulması için ad alanını boş olarak ayarlamanız gerekir, bu da sorguları hatalı yönlendirebilir.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Bu örnekte gösterildiği gibi, öznitelik sözdiziminde aynı bağlama bildirimini oluşturmak için özel karakterleri düzgün bir şekilde atlamanız gerekir. Daha fazla bilgi için bkz. [XML karakter varlıkları ve xaml](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 @No__t-0, bu örnek çalıştırıldığında aşağıdaki öğeleri gösterir. Bunlar, *hisse senedi* değeri "*Out*" veya *sayı* değeri 3 veya daha büyük ya da 8 ' e eşit olan *kitaplar* altındaki tüm öğelerin *unvanına ait başlıktır*. @No__t 2 ' de ayarlanan <xref:System.Windows.Data.XmlDataProvider.XPath%2A> değeri yalnızca *kitaplar* öğelerinin (temelde bir filtre ayarlaması) gösterilmesini gerektiğini gösterdiği Için hiçbir *CD* öğesi döndürülmediğine dikkat edin.  
  
 ![Dört kitapların başlığını gösteren XPath örneği ekran görüntüsü.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Bu örnekte, <xref:System.Windows.DataTemplate> ' deki <xref:System.Windows.Controls.TextBlock> bağlamasının <xref:System.Windows.Data.Binding.XPath%2A> "*title*" olarak ayarlandığından kitap başlıkları görüntülenir. *ISBN*gibi bir özniteliğin değerini göstermek istiyorsanız, bu <xref:System.Windows.Data.Binding.XPath%2A> değerini "`@ISBN`" olarak ayarlamanız gerekir.  
  
 @No__t-1 ' deki **XPath** özellikleri XmlNode. SelectNodes yöntemi tarafından işlenir. Farklı sonuçlar almak için **XPath** sorgularını değiştirebilirsiniz. Önceki örnekte, bağlı <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.Binding.XPath%2A> sorgusunun bazı örnekleri aşağıda verilmiştir:  
  
- `XPath="Book[1]"`, ilk kitap öğesini döndürür ("XML eyleminde"). **XPath** dizinlerinin 0 değil 1 ' i temel alan olduğunu unutmayın.  
  
- `XPath="Book[@*]"`, tüm kitap öğelerini tüm özniteliklere döndürecek.  
  
- `XPath="Book[last()-1]"`, ikinciden son kitap öğesine döndürür ("Microsoft .NET tanıtma").  
  
- `XPath="*[position()>3]"`, ilk 3 hariç tüm kitap öğelerini döndürür.  
  
 Bir **XPath** sorgusu çalıştırdığınızda <xref:System.Xml.XmlNode> veya XMLNodes listesini döndürür. <xref:System.Xml.XmlNode> ortak dil çalışma zamanı (CLR) nesnesidir ve bu, ortak dil çalışma zamanı (CLR) özelliklerine bağlamak için <xref:System.Windows.Data.Binding.Path%2A> özelliğini kullanabileceğiniz anlamına gelir. Önceki örneği yeniden deneyin. Örneğin geri kalanı aynı kalırsa ve <xref:System.Windows.Controls.TextBlock> bağlamasını aşağıdaki şekilde değiştirirseniz, <xref:System.Windows.Controls.ListBox> ' de döndürülen XmlNodes 'nin adlarını görürsünüz. Bu durumda, döndürülen tüm düğümlerin adı "*Book*" dır.  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Bazı uygulamalarda, verilerin tam içeriğinin derleme zamanında bilinmesi gerektiğinden, @no__t [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının kaynağına veri Adası olarak eklemek kullanışlı olabilir. Bu nedenle, aşağıdaki örnekte olduğu gibi bir dış [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyasından veri alma de desteklenir:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 @No__t-0 verisi, uzak bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyasında yer alıyorsa, <xref:System.Windows.Data.XmlDataProvider.Source%2A> özniteliğine uygun bir URL atayarak aşağıdaki gibi verilere erişim tanımlayabilirsiniz:  
  
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
