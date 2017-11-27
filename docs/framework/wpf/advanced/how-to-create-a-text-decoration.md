---
title: "Nasıl yapılır: Metin Süslemesi Oluşturma"
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
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a>Nasıl yapılır: Metin Süslemesi Oluşturma
A <xref:System.Windows.TextDecoration> metne ekleyebileceğiniz görsel süslemedir nesnesidir. Metin düzenlemelerinin dört tür vardır: alt çizgi, taban çizgisi, üst çizgi ve üst çizgi. Aşağıdaki örnek metin göre metin düzenlemelerinin konumlarını gösterir.  
  
 ![Metin dekorasyonu konumları diyagramı](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Metin dekorasyonu türleri örneği  
  
 Metin dekorasyonu metne eklemek için oluşturma bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin. Kullanım <xref:System.Windows.TextDecoration.Location%2A> özelliği dekorasyonu, alt çizgi gibi göründüğü belirtin. Kullanım <xref:System.Windows.TextDecoration.Pen%2A> düz dolgu veya gradyan rengi gibi dekorasyonu görünümünü belirtmek için özellik. İçin bir değer belirtmezseniz, <xref:System.Windows.TextDecoration.Pen%2A> özelliği, aynı renk metin olarak varsayılır. Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.  
  
 Aşağıdaki örnek, doğrusal gradyan fırçası ve kesikli kalem ile biçimlendirilmiş bir metin dekorasyonu gösterir.  
  
 ![Metin dekorasyonu doğrusal gradyan alt çizgiyle](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Bir alt çizgi örneği stilde ile doğrusal gradyan fırçası ve kesikli kalem  
  
 <xref:System.Windows.Documents.Hyperlink> Nesnesidir köprüler akış içeriği barındırmanıza olanak tanıyan bir satır içi düzeyde akış içeriği öğesidir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne. <xref:System.Windows.TextDecoration>nesneleri, performans örneği oluşturmak için yoğun olabilir, özellikle birçok varsa <xref:System.Windows.Documents.Hyperlink> nesneleri. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri, bir alt çizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.  
  
 Aşağıdaki örnekte, altı çizili "My MSN" bağlantısı için dinamik — yalnızca zaman göründüğü <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.  
  
 ![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
TextDecorations ile tanımlanan köprüler  
  
 Daha fazla bilgi için bkz: [belirtin olup olmadığını bir köprü çizilir](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir alt çizgi dekorasyonu varsayılan yazı tipi değeri kullanır.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Aşağıdaki kod örneğinde, altı çizili metin düzenleme kalem için düz renk fırça ile oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Aşağıdaki kod örneğinde, altı çizili metin düzenleme kesik kalem için doğrusal gradyan fırçası oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Olup olmadığını bir köprü altı çizili belirtin](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
