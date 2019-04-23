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
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133841"
---
# <a name="how-to-create-a-text-decoration"></a>Nasıl yapılır: Metin Süslemesi Oluşturma
A <xref:System.Windows.TextDecoration> metni ekleyebileceğiniz görsel bir süsleme nesnedir. Metin süslemeleri dört tür vardır: alt çizgi, temel, üstü çizili ve üst çizgi. Aşağıdaki örnek, metin düzenlemelerinin metin göreli konumlarını gösterir.  
  
 ![Metin düzenleme türleri diyagramı](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Metin süslemesi metin eklemek için oluşturun bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin. Kullanım <xref:System.Windows.TextDecoration.Location%2A> metin düzenleme, alt çizgi gibi görüneceği yeri belirtmek için özellik. Kullanım <xref:System.Windows.TextDecoration.Pen%2A> tek renk dolgu veya gradyan rengi gibi metin düzenleme görünümünü belirtmek için özellik. İçin bir değer belirtmezseniz <xref:System.Windows.TextDecoration.Pen%2A> özelliğini aynı metin rengini varsayılır. Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.  
  
 Aşağıdaki örnek, doğrusal gradyan fırçası ve bir kesikli kalem ile biçimlendirilmiş metin süslemesi gösterir.  
  
 ![Doğrusal gradyan altı çizili metin düzenleme](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne. <xref:System.Windows.TextDecoration> nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.  
  
 Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik — zaman görünür <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.  
  
 ![Köprüler TextDecorations görüntüleme](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 Daha fazla bilgi için [belirtin olmadığını köprünün altı çizilir](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde altı çizili metin düzenleme varsayılan yazı tipi değeri kullanır.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 Aşağıdaki kod örneğinde tek renk Fırçası kalem için altı çizili metin düzenleme oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 Aşağıdaki kod örneğinde altı çizili metin düzenleme doğrusal gradyan fırçası kesik kalem için oluşturulur.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Köprünün Altı Çizili Olup Olmadığını Belirtme](how-to-specify-whether-a-hyperlink-is-underlined.md)
