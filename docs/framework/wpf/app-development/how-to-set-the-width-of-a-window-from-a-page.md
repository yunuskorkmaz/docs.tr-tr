---
title: 'Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545998"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama
Bu örnek penceresinden genişliğini ayarlamak nasıl gösterilmektedir bir <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> ana penceresinin genişliğini ayarlayarak ayarlayabilirsiniz <xref:System.Windows.Controls.Page.WindowWidth%2A>. Bu özellik tanır <xref:System.Windows.Controls.Page> , onu barındıran pencere türünün açık bilgisine sahip değil.  
  
> [!NOTE]
>  Kullanarak bir pencerenin genişliğini ayarlamak için <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> pencerenin alt öğesi olması gerekir.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
