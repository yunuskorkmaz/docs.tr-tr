---
title: "Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7354a6c3f1b913494da9ad45181a0c7741a1cfa2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a>Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama
Bu örnek penceresinden genişliğini ayarlamak nasıl gösterilmektedir bir <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> ana penceresinin genişliğini ayarlayarak ayarlayabilirsiniz <xref:System.Windows.Controls.Page.WindowWidth%2A>. Bu özellik tanır <xref:System.Windows.Controls.Page> , onu barındıran pencere türünün açık bilgisine sahip değil.  
  
> [!NOTE]
>  Kullanarak bir pencerenin genişliğini ayarlamak için <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> pencerenin alt öğesi olması gerekir.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
