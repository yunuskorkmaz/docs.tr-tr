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
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460711"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek, bir <xref:System.Windows.Controls.ControlTemplate>tarafından oluşturulan öğelerin nasıl bulunacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Button> sınıfı için basit <xref:System.Windows.Controls.ControlTemplate> oluşturan bir stil gösterir:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Şablon uygulandıktan sonra şablon içinde bir öğe bulmak için <xref:System.Windows.Controls.Control.Template%2A><xref:System.Windows.FrameworkTemplate.FindName%2A> yöntemini çağırabilirsiniz. Aşağıdaki örnek, denetim şablonu içinde <xref:System.Windows.Controls.Grid> gerçek genişlik değerini gösteren bir ileti kutusu oluşturur:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTemplate ile Oluşturulan Öğeleri Bulma](../data/how-to-find-datatemplate-generated-elements.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [WPF XAML Ad Kapsamları](../advanced/wpf-xaml-namescopes.md)
- [WPF İçinde Ağaçlar](../advanced/trees-in-wpf.md)
