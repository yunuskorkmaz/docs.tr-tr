---
title: "Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92037be2280eaa248951ff9bad82b7a1581a4fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Nasıl yapılır: XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama
Bu örnek nasıl bağlanacağını gösterir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] verileri kullanarak bir <xref:System.Windows.Data.XmlDataProvider>.  
  
 İle bir <xref:System.Windows.Data.XmlDataProvider>, alttaki uygulamanızdaki veri bağlama üzerinden erişilen verileri herhangi bir ağacını olabilir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] düğümleri. Diğer bir deyişle, bir <xref:System.Windows.Data.XmlDataProvider> herhangi bir ağacını kullanmak için kullanışlı bir yol sağlayan [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] düğümleri bağlama kaynağı olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, verileri doğrudan olarak katıştırılır bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *veri adası* içinde <xref:System.Windows.FrameworkElement.Resources%2A> bölümü. Bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri adası Sarmalanan, içinde `<x:XData>` etiketleri ve her zaman olduğu bir tek bir kök düğümü sahip *stok* Bu örnekte.  
  
> [!NOTE]
>  Kök düğümü [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri içeren bir **xmlns** ayarlar özniteliği [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanına boş bir dize. Bu XPath sorguları içi olan bir veri adası uygulamak için bir gereksinimdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası. Bu satır içi durumda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ve bu nedenle veri adası devralır <xref:System.Windows> ad alanı. Bu nedenle, ad alanı boş tarafından tam XPath sorguları tutmak için ayarlamanız gerekir <xref:System.Windows> sorguları misdirect ad alanı.  
  
 [!code-xaml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Bu örnekte gösterildiği gibi öznitelik sözdiziminde aynı bağlama bildirimi oluşturmak için özel karakterleri düzgün kaçış gerekir. Daha fazla bilgi için bkz: [XML karakter varlıkları ve XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 <xref:System.Windows.Controls.ListBox> Bu örnek çalıştırdığınızda, aşağıdaki öğeler gösterilecektir. Bunlar *başlık*tüm altındaki öğelerin s *Books* ile ya da bir *hisse senedi* değerini "*çıkışı*" veya bir *numarası* değeri 3 veya daha büyük veya eşittir 8. Dikkat hiçbir *CD* öğeler döndürülür. çünkü <xref:System.Windows.Data.XmlDataProvider.XPath%2A> değerinin ayarlanmış <xref:System.Windows.Data.XmlDataProvider> gösterir, yalnızca *Books* öğeleri ortaya (aslında bir filtre ayarlayarak).  
  
 ![XPath örnek](../../../../docs/framework/wpf/data/media/xpathexample.PNG "XPathExample")  
  
 Bu örnekte, çünkü kitap başlıklarını görüntülenir <xref:System.Windows.Data.Binding.XPath%2A> , <xref:System.Windows.Controls.TextBlock> bağlama <xref:System.Windows.DataTemplate> ayarlamak "*başlık*". Bir özniteliğin değeri gibi görüntülemek isteyip istemediğinizi *ISBN*, ayarlarsınız <xref:System.Windows.Data.Binding.XPath%2A> değerini "`@ISBN`".  
  
 **XPath** özelliklerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XmlNode.SelectNodes yöntemi tarafından işlenir. Değiştirebileceğiniz **XPath** farklı sonuçlar almak için sorgular. İşte bazı örnekler için <xref:System.Windows.Data.Binding.XPath%2A> sorgu sınır <xref:System.Windows.Controls.ListBox> önceki örnekten:  
  
-   `XPath="Book[1]"`ilk kitap öğesini ("XML Eylemde") döndürür. Unutmayın **XPath** dizinlerinin 1, 0 temel.  
  
-   `XPath="Book[@*]"`tüm öznitelikleri olan tüm kitap öğelerini döndürür.  
  
-   `XPath="Book[last()-1]"`İkinci ("Tanıtımı Microsoft .NET") son kitap öğesini döndürür.  
  
-   `XPath="*[position()>3]"`ilk 3 dışında tüm kitap öğeleri döndürür.  
  
 Çalıştırdığınızda bir **XPath** değerini döndürür, sorgu bir <xref:System.Xml.XmlNode> veya XmlNodes listesi. <xref:System.Xml.XmlNode>olan bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kullanabileceğiniz anlamına gelir nesne <xref:System.Windows.Data.Binding.Path%2A> özelliğine bağlamak için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellikleri. Önceki örneği yeniden göz önünde bulundurun. Örneğin geri kalanı aynı kalır ve değiştirirseniz <xref:System.Windows.Controls.TextBlock> aşağıdaki bağlama, döndürülen XmlNodes içinde adlarını görürsünüz <xref:System.Windows.Controls.ListBox>. Bu durumda, döndürülen tüm düğümlerin adıdır "*defteri*".  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Bazı uygulamalarda, katıştırma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kaynağı veri adası olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veri tam içeriği derleme zamanında bilinmesi gerekir çünkü sayfa kullanışsız olabilir. Bu nedenle, dış veri alma [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosya de desteklenir, aşağıdaki örnekte olduğu gibi:  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Varsa [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri bulunduğu uzak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dosyası tanımlarsınız erişim verilere uygun bir atayarak [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için <xref:System.Windows.Data.XmlDataProvider.Source%2A> özniteliğini aşağıdaki gibi:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.ObjectDataProvider>  
 [XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)  
 [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Bağlama Kaynaklarına Genel Bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
