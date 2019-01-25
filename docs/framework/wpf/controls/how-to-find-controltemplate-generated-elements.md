---
title: 'Nasıl yapılır: ControlTemplate ile oluşturulan öğeleri bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: a93ec700bc0782439f98aed48f7094a50a3c0ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638387"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Nasıl yapılır: ControlTemplate ile oluşturulan öğeleri bulma
Bu örnek tarafından oluşturulan öğeleri bulma işlemini gösterir. bir <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, basit bir oluşturan bir stil gösterir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> sınıfı:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Şablon uygulandıktan sonra şablon içinde bir öğeyi bulmak için çağırabilirsiniz <xref:System.Windows.FrameworkTemplate.FindName%2A> yöntemi <xref:System.Windows.Controls.Control.Template%2A>. Aşağıdaki örnekte gerçek genişlik değerini gösteren bir ileti kutusu oluşturur <xref:System.Windows.Controls.Grid> denetim şablonu içinde:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataTemplate ile Oluşturulan Öğeleri Bulma](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [WPF XAML Ad Kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
