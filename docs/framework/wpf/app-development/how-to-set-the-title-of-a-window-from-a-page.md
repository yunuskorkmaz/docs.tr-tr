---
title: 'Nasıl yapılır: Bir Sayfadan Pencere Başlığını Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: 0f618af89965822b0df96a264997dabd9cae7608
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940781"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Nasıl yapılır: Bir Sayfadan Pencere Başlığını Ayarlama
Bu örnekte <xref:System.Windows.Controls.Page> , içinde barındırılan pencerenin başlığının nasıl ayarlanacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir sayfa, <xref:System.Windows.Controls.Page.WindowTitle%2A> özelliği ayarlayarak onu barındıran pencerenin başlığını değiştirebilir, örneğin:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
> Bir sayfanın <xref:System.Windows.Controls.Page.Title%2A> özelliğinin ayarlanması pencere başlığının değerini değiştirmez. Bunun yerine <xref:System.Windows.Controls.Page.Title%2A> , gezinme geçmişinde bir sayfa girişinin adını belirtir.
