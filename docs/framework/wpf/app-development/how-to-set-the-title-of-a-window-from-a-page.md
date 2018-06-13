---
title: 'Nasıl yapılır: bir pencere başlık sayfasından ayarlayın'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: e69812b59783717b7b9c832d4e8ab01ab42827c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546191"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Nasıl yapılır: bir pencere başlık sayfasından ayarlayın
Bu örnek, pencere başlığı ayarlamak nasıl gösterir bir <xref:System.Windows.Controls.Page> barındırılır.  
  
## <a name="example"></a>Örnek  
 Bir sayfa ayarlayarak barındırma penceresinin başlık değiştirebilirsiniz <xref:System.Windows.Controls.Page.WindowTitle%2A> özellik sözlüğüdür:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Ayarı <xref:System.Windows.Controls.Page.Title%2A> bir sayfa özelliğinin değeri, pencere başlığı değiştirmez. Bunun yerine, <xref:System.Windows.Controls.Page.Title%2A> gezinti geçmişindeki sayfa girdisinin adını belirtir.
