---
title: "Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b39c45a7c85155a0fb46e8e176da5979e52e6e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama
Bu örnek XML verinin nasıl bağlanacağını gösterir bir <xref:System.Windows.Controls.ItemsControl> kullanarak <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML kodu tanımlayan bir <xref:System.Windows.Controls.ItemsControl> ve veri türü veri şablonu içerir `Planet` içinde `http://planetsNS` XML ad alanı. Bir ad alanı kaplayan bir XML veri türü ayraçlar içinde ad içermelidir ve XAML biçimlendirme uzantısı göründüğü görünürse, bir küme parantezi kaçış sırası içeren ad gelmelidir. Bu kod karşılık dinamik özellikleri bağlar <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerinin <xref:System.Xml.Linq.XElement> sınıfı. Dinamik özellikler yöntemlerin adlarını paylaşan dinamik özellikleri bağlamak XAML etkinleştirin. Daha fazla bilgi için bkz: [LINQ-XML dinamik özellikleri](/visualstudio/designers/linq-to-xml-dynamic-properties). XML için varsayılan ad alanı bildiriminin nasıl öznitelik adları için geçerli değildir dikkat edin.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Aşağıdaki C# kod çağrıları <xref:System.Xml.Linq.XDocument.Load%2A> ve yığın paneli veri içeriğinin adlı öğesinin tüm alt öğeleri için ayarlar `SolarSystemPlanets` içinde `http://planetsNS` XML ad alanı.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML verilerini kullanan XAML kaynağı olarak depolanabilir <xref:System.Windows.Data.ObjectDataProvider>. Tam bir örnek için bkz: [L2DBForm.xaml kaynak kodu](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Aşağıdaki örnek kod bir nesne kaynak veri bağlamı nasıl ayarlayacağınızı gösterir.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Eşle dinamik özellikleri <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> XAML içinde esneklik sağlar. Kodunuzu XML sorgu için bir LINQ sonuçlarını de bağlayabilirsiniz. Bu örnek öğe değeri tarafından istenen sorgu sonuçlarına bağlar.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [WPF veri bağlama ile LINQ-XML genel bakış](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [LINQ-XML örneği kullanarak WPF veri bağlama](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [LINQ-XML Dinamik Özellikler](/visualstudio/designers/linq-to-xml-dynamic-properties)
