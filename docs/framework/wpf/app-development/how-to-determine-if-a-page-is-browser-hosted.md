---
title: "Nasıl yapılır: bir sayfa tarayıcı barındırılan olup olmadığını belirler"
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
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1da46596bf48d9648830d20758647be753f128fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Nasıl yapılır: bir sayfa tarayıcı barındırılan olup olmadığını belirler
Bu örnek belirlemek gösterilmiştir bir <xref:System.Windows.Controls.Page> bir tarayıcı içinde barındırılır.  
  
## <a name="example"></a>Örnek  
 A <xref:System.Windows.Controls.Page> konak belirsiz olabilir ve bu nedenle, konakları dahil olmak üzere, birkaç farklı türde yüklenebilir bir <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, veya bir tarayıcı. Bir veya daha fazla sayfa içerir ve birden fazla tek başına tarafından başvurulan ve gözatılamaz Kitaplık derlemesi olduğunda bu durum oluşabilir ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) barındıran uygulamalar.  
  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> belirlemek için bir <xref:System.Windows.Controls.Page> bir tarayıcıda barındırılan.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
