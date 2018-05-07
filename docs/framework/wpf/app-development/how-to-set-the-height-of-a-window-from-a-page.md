---
title: 'Nasıl yapılır: bir sayfadan bir pencere yüksekliğini ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: e25bc3cf2f5de01177f79f671390bac39875d079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Nasıl yapılır: bir sayfadan bir pencere yüksekliğini ayarlama
Bu örnek penceresinden yüksekliğinin nasıl ayarlanacağını gösterir bir <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> ayarlayarak ana penceresinin yüksekliğini belirleyebilir <xref:System.Windows.Controls.Page.WindowHeight%2A>. Bu özellik tanır <xref:System.Windows.Controls.Page> , onu barındıran pencere türünün açık bilgisine sahip değil.  
  
> [!NOTE]
>  Kullanarak bir pencerenin yüksekliğini ayarlamak için <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> pencerenin alt öğesi olması gerekir.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
