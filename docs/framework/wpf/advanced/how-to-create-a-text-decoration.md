---
title: 'Nasıl yapılır: Metin Süslemesi Oluşturma'
ms.date: 03/30/2017
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
ms.openlocfilehash: b85bbaed13d9406f85c62a9a5bc5ca220d90b0b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607953"
---
# <a name="how-to-create-a-text-decoration"></a>Nasıl yapılır: Metin Süslemesi Oluşturma
A <xref:System.Windows.TextDecoration> metni ekleyebileceğiniz görsel bir süsleme nesnedir. Metin süslemeleri dört tür vardır: alt çizgi, temel, üstü çizili ve üst çizgi. Aşağıdaki örnek, metin düzenlemelerinin metin göreli konumlarını gösterir.  
  
 ![Metin süslemesi konumları diyagramı](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Metin süslemesi türleri örneği  
  
 Metin süslemesi metin eklemek için oluşturun bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin. Kullanım <xref:System.Windows.TextDecoration.Location%2A> metin düzenleme, alt çizgi gibi görüneceği yeri belirtmek için özellik. Kullanım <xref:System.Windows.TextDecoration.Pen%2A> tek renk dolgu veya gradyan rengi gibi metin düzenleme görünümünü belirtmek için özellik. İçin bir değer belirtmezseniz <xref:System.Windows.TextDecoration.Pen%2A> özelliğini aynı metin rengini varsayılır. Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.  
  
 Aşağıdaki örnek, doğrusal gradyan fırçası ve bir kesikli kalem ile biçimlendirilmiş metin süslemesi gösterir.  
  
 ![Doğrusal gradyan altı çizili metin süslemesi](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Doğrusal gradyan ile bir alt çizgi örneği biçimlendirilmiş ve kesikli kalem  
  
 <xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne. <xref:System.Windows.TextDecoration> nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.  
  
 Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik — zaman görünür <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.  
  
 ![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
TextDecorations ile tanımlanan köprüler  
  
 Daha fazla bilgi için [belirtin olmadığını köprünün altı çizilir](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde altı çizili metin düzenleme varsayılan yazı tipi değeri kullanır.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Aşağıdaki kod örneğinde tek renk Fırçası kalem için altı çizili metin düzenleme oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Aşağıdaki kod örneğinde altı çizili metin düzenleme doğrusal gradyan fırçası kesik kalem için oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Köprünün Altı Çizili Olup Olmadığını Belirtme](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
