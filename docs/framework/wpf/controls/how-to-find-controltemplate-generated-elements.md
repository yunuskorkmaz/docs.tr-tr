---
title: "Nasıl yapılır: ControlTemplate ile Oluşturulan Öğeleri Bulma"
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
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f81069873930af57e1f6ab2f3e0408b4d53f38b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [DataTemplate oluşturulan öğeleri bulma](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML ad kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF ağaçlarında](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
