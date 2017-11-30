---
title: "Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme
Bu örnek, Gezinme geçmişi girişlerinde İleri veya geri gitmek göstermektedir.  
  
## <a name="example"></a>Örnek  
 Şu konakları içerikten çalışan kod, gezinti geçmişinde bir kerede bir girdiye ileriye veya geriye gidebilir.  
  
-   <xref:System.Windows.Navigation.NavigationWindow>kullanma<xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame>kullanma<xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Bir girdi ileriye gidebilirsiniz önce ilk olduğunu girişleri İleri gezinti geçmişinde inceleyerek işaretlemeniz gerekir **CanGoForward** özelliği. Bir girdi ileriye gitmek için arama **GoForward** yöntemi. Bu aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Gezinmek önce bir giriş yeniden, olduğunu girişleri geri gezinti geçmişinde incelenerek ilk denetlemelisiniz **CanGoBack** özelliği. Bir girdiye geri gitmek için arama **GoBack** yöntemi. Bu aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Çağırırsanız **GoForward**, ve İleri gezinti geçmişinde hiçbir girdi yoksa veya çağırırsanız **GoBack**, ve geri gezinti geçmişinde hiçbir girdi yoksa bir <xref:System.InvalidOperationException> oluşturulur.
