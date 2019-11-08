---
title: 'Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: f075d646539de5d68e1c9c75d9664451125e9919
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733555"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama
Bu örnek, bir <xref:System.Windows.Data.XmlDataProvider>kullanarak XML verilerinin nasıl bağlanacağını gösterir.  
  
 <xref:System.Windows.Data.XmlDataProvider>, uygulamanızdaki veri bağlama aracılığıyla erişilebilen temel veriler herhangi bir XML düğümleri ağacı olabilir. Diğer bir deyişle, bir <xref:System.Windows.Data.XmlDataProvider> herhangi bir XML düğümleri ağacını bağlama kaynağı olarak kullanmak için uygun bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, veriler <xref:System.Windows.FrameworkElement.Resources%2A> bölümünde doğrudan bir XML *veri Adası* olarak katıştırılır. Bir XML veri Adası `<x:XData>` etiketlere sarmalanmış olmalı ve her zaman bu örnekte *Envanter* olan tek bir kök düğüme sahip olmalıdır.  
  
> [!NOTE]
> XML verilerinin kök düğümü, XML ad alanını boş bir dizeye ayarlayan bir **xmlns** özniteliğine sahiptir. Bu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında satır içi bir veri adasına XPath sorguları uygulamak için bir gereksinimdir. Bu satır içi durumda, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve bu nedenle veri Adası, <xref:System.Windows> ad alanını devralır. Bu nedenle, XPath sorgularının <xref:System.Windows> ad alanı tarafından nitelendirilmeden tutulması için ad alanını boş olarak ayarlamanız gerekir, bu da sorguları hatalı yönlendirebilir.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Bu örnekte gösterildiği gibi, öznitelik sözdiziminde aynı bağlama bildirimini oluşturmak için özel karakterleri düzgün bir şekilde atlamanız gerekir. Daha fazla bilgi için bkz. [XML karakter varlıkları ve xaml](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox>, bu örnek çalıştırıldığında aşağıdaki öğeleri gösterir. Bunlar, *hisse senedi* değeri "*Out*" veya *sayı* değeri 3 veya daha büyük ya da 8 ' e eşit olan *kitaplar* altındaki tüm öğelerin *unvanına ait başlıktır*. <xref:System.Windows.Data.XmlDataProvider> ayarlanan <xref:System.Windows.Data.XmlDataProvider.XPath%2A> değeri yalnızca *Books* öğelerinin gösterilmesini (temelde bir filtre ayarlaması) gerektiğini gösterdiği için, hiçbir *CD* öğesi döndürülmediğine dikkat edin.  
  
 ![Dört kitapların başlığını gösteren XPath örneği ekran görüntüsü.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Bu örnekte, <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.TextBlock> bağlamasının <xref:System.Windows.Data.Binding.XPath%2A> "*title*" olarak ayarlandığından kitap başlıkları görüntülenir. *ISBN*gibi bir özniteliğin değerini göstermek istiyorsanız, bu <xref:System.Windows.Data.Binding.XPath%2A> değerini "`@ISBN`" olarak ayarlamanız gerekir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **XPath** özellikleri XmlNode. SelectNodes yöntemi tarafından işlenir. Farklı sonuçlar almak için **XPath** sorgularını değiştirebilirsiniz. Önceki örnekteki bağlı <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.Binding.XPath%2A> sorguya ilişkin bazı örnekler aşağıda verilmiştir:  
  
- `XPath="Book[1]"`, ilk kitap öğesini döndürür ("XML eyleminde"). **XPath** dizinlerinin 0 değil 1 ' i temel alan olduğunu unutmayın.  
  
- `XPath="Book[@*]"`, tüm kitap öğelerini tüm özniteliklerle döndürecek.  
  
- `XPath="Book[last()-1]"`, ikinciden son kitap öğesine ("Microsoft .NET giriş") döndürür.  
  
- `XPath="*[position()>3]"` ilk 3 hariç tüm kitap öğelerini döndürür.  
  
 Bir **XPath** sorgusu çalıştırdığınızda bir <xref:System.Xml.XmlNode> veya XMLNodes listesini döndürür. <xref:System.Xml.XmlNode> ortak dil çalışma zamanı (CLR) nesnesidir ve bu, ortak dil çalışma zamanı (CLR) özelliklerine bağlamak için <xref:System.Windows.Data.Binding.Path%2A> özelliğini kullanabileceğiniz anlamına gelir. Önceki örneği yeniden deneyin. Örneğin geri kalanı aynı kalırsa ve <xref:System.Windows.Controls.TextBlock> bağlamayı aşağıdaki şekilde değiştirirseniz, <xref:System.Windows.Controls.ListBox>döndürülen XmlNodes 'nin adlarını görürsünüz. Bu durumda, döndürülen tüm düğümlerin adı "*Book*" dır.  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Bazı uygulamalarda, verilerin tam içeriğinin derleme zamanında bilinmesi gerektiğinden, bazı uygulamalarda, verileri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın kaynağına bir veri Adası olarak gömmek çok kullanışlı olabilir. Bu nedenle, aşağıdaki örnekte olduğu gibi harici bir XML dosyasından veri alma de desteklenir:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 XML verileri uzak bir XML dosyasında yer alıyorsa, <xref:System.Windows.Data.XmlDataProvider.Source%2A> özniteliğine uygun bir URL atayarak aşağıdaki gibi verilere erişim tanımlayabilirsiniz:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.ObjectDataProvider>
- [XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Bağlama Kaynaklarına Genel Bakış](binding-sources-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
