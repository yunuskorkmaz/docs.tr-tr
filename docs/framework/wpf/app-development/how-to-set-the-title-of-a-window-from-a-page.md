---
title: "Nasıl yapılır: bir pencere başlık sayfasından ayarlayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11f33eede479e090a78bffe841d7998e03eab6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>Nasıl yapılır: bir pencere başlık sayfasından ayarlayın
Bu örnek, pencere başlığı ayarlamak nasıl gösterir bir <xref:System.Windows.Controls.Page> barındırılır.  
  
## <a name="example"></a>Örnek  
 Bir sayfa ayarlayarak barındırma penceresinin başlık değiştirebilirsiniz <xref:System.Windows.Controls.Page.WindowTitle%2A> özellik sözlüğüdür:  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  Ayarı <xref:System.Windows.Controls.Page.Title%2A> bir sayfa özelliğinin değeri, pencere başlığı değiştirmez. Bunun yerine, <xref:System.Windows.Controls.Page.Title%2A> gezinti geçmişindeki sayfa girdisinin adını belirtir.
