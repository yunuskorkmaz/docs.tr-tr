---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
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
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d734a7f17f8843ff284ac0854ac41d4a5b9f5584
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu konuda yapabilirsiniz verileri için kullanılabilir bağlama farklı yolları açıklanmaktadır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], uygulamanızın gereksinimlerine bağlı olarak.  
  
## <a name="example"></a>Örnek  
 Varsa bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] gelen bağlamak istediğiniz nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yapabilirsiniz nesne kullanılabilir bir kaynak olarak tanımlamak ve buna vermek için bağlama için tek yolu bir `x:Key`. Aşağıdaki örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`. `Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 Nesne sonra bağlayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Data.ObjectDataProvider> aşağıdaki örnekteki gibi sınıfı.  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 Bağlama tanımladığınız aynı şekilde:  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Bu örnekte, sonuç aynıdır: elinizde bir <xref:System.Windows.Controls.TextBlock> metin içeriği ile `Joe`. Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıfı, bir yöntemin sonucu bağlamak özelliği gibi işlevsellik sağlar. Kullanmayı tercih edebileceğiniz <xref:System.Windows.Data.ObjectDataProvider> sağladığı işlevselliğe gerekiyorsa sınıfı.  
  
 Önceden oluşturulmuş bir nesneye bağlıyorsanız, ancak ayarlamak gerekir `DataContext` kodda, aşağıdaki örnekte olduğu gibi.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama kullanmak için veri <xref:System.Windows.Data.XmlDataProvider> sınıfı için bkz: [XML verileri kullanarak bir XMLDataProvider ve XPath sorguları bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama kullanmak için veri <xref:System.Windows.Data.ObjectDataProvider> sınıfı için bkz: [XDocument, XElement veya LINQ XML sorgu sonuçları için bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Veri bağlama için farklı yollar hakkında bilgi için bkz [bağlama kaynak](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Hangi veri türlerini bağlayabileceğiniz veya kendi uygulama hakkında bilgi için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri bağlama için bkz: [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
