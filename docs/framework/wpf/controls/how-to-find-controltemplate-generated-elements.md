---
title: 'Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 426f6c93433711ac72fe67eff2ee3006aa4d9166
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092134"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek tarafından oluşturulan öğeleri bulma işlemini gösterir. bir <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, basit bir oluşturan bir stil gösterir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> sınıfı:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Şablon uygulandıktan sonra şablon içinde bir öğeyi bulmak için çağırabilirsiniz <xref:System.Windows.FrameworkTemplate.FindName%2A> yöntemi <xref:System.Windows.Controls.Control.Template%2A>. Aşağıdaki örnekte gerçek genişlik değerini gösteren bir ileti kutusu oluşturur <xref:System.Windows.Controls.Grid> denetim şablonu içinde:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTemplate ile Oluşturulan Öğeleri Bulma](../data/how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [WPF XAML Ad Kapsamları](../advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../advanced/trees-in-wpf.md)
