---
title: 'Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3d57039d959aa63c031ef467cd2f8398fc3ffd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544150"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme
<xref:System.Windows.Documents.Hyperlink> Nesnesidir köprüler akış içeriği barındırmanıza olanak tanıyan bir satır içi düzeyde akış içeriği öğesidir. Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne. <xref:System.Windows.TextDecoration> nesneleri, performans örneği oluşturmak için yoğun olabilir, özellikle birçok varsa <xref:System.Windows.Documents.Hyperlink> nesneleri. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri, bir alt çizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.  
  
 Aşağıdaki örnekte, altı çizili "My MSN" bağlantısı için dinamik — yalnızca zaman göründüğü <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.  
  
 ![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
TextDecorations ile tanımlanan köprüler  
  
## <a name="example"></a>Örnek  
 Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ile ve bir alt çizginin olmadan tanımlanan:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Aşağıdaki kod örneği için bir alt çizginin oluşturulacağını gösterir <xref:System.Windows.Documents.Hyperlink> üzerinde <xref:System.Windows.ContentElement.MouseEnter> olayı ve kaldırılacağını <xref:System.Windows.ContentElement.MouseLeave> olay.  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Metin Süslemesi Oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
