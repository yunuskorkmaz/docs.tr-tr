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
ms.openlocfilehash: 3d3032326a0cedc01b4a7ec8e6546044353d6b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553916"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma
Bu örnek tarafından oluşturulan öğeleri bulmayı gösteren bir <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte basit bir oluşturan bir stil gösterir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> sınıfı:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Şablon uygulandıktan sonra şablonu içindeki bir öğeyi bulmak için çağırabilirsiniz <xref:System.Windows.FrameworkTemplate.FindName%2A> yöntemi <xref:System.Windows.Controls.Control.Template%2A>. Aşağıdaki örnek gerçek genişlik değerini gösteren bir ileti kutusu oluşturur <xref:System.Windows.Controls.Grid> denetim şablonu içinde:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTemplate ile Oluşturulan Öğeleri Bulma](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML Ad Kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF İçinde Ağaçlar](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
