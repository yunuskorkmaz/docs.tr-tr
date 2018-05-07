---
title: 'Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme
Bu örnek, Gezinme geçmişi girişlerinde İleri veya geri gitmek göstermektedir.  
  
## <a name="example"></a>Örnek  
 Şu konakları içerikten çalışan kod, gezinti geçmişinde bir kerede bir girdiye ileriye veya geriye gidebilir.  
  
-   <xref:System.Windows.Navigation.NavigationWindow> Kullanma <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> Kullanma <xref:System.Windows.Navigation.NavigationService>  
  
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
