---
title: 'Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 9e8eb54d4710095a1aba052b16e49c528bd17c0e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371063"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme
<xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne. <xref:System.Windows.TextDecoration> nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.  
  
 Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik — zaman görünür <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.  
  
 ![TextDecorations görüntüleyen köprüler](./media/textdecoration03.png "TextDecoration03")  
TextDecorations ile tanımlanan köprüler  
  
## <a name="example"></a>Örnek  
 Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ve alt çizgi olmadan tanımlanan:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Aşağıdaki kod örneği için altı çizili oluşturma işlemi gösterilmektedir <xref:System.Windows.Documents.Hyperlink> üzerinde <xref:System.Windows.ContentElement.MouseEnter> olay ve kaldırılacağını <xref:System.Windows.ContentElement.MouseLeave> olay.  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Metin Süslemesi Oluşturma](how-to-create-a-text-decoration.md)
