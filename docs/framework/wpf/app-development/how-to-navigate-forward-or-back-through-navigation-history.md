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
ms.openlocfilehash: 4c20ebfab45a24cf34b1476fb94dae6913fb4d99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947764"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme
Bu örnek girişleri gezinme geçmişinde ileriye veya geriye gitmek nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Şu konakları içeriğinden çalışan kod gezinti geçmişinde bir zamanda bir girdi İleri veya geri gidebilirsiniz.  
  
- <xref:System.Windows.Navigation.NavigationWindow> kullanma <xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame> kullanma <xref:System.Windows.Navigation.NavigationService>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Bir girdi ileriye gidebilirsiniz önce ilk olduğunu girişleri İleri Gezinme geçmişi içinde inceleyerek işaretlemeniz gerekir **CanGoForward** özelliği. Bir girdi ileriye gezinmek için çağrı **GoForward** yöntemi. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Gidebilirsiniz önce bir girdi geri, olduğunu girişleri geri Gezinme geçmişi içinde incelenerek ilk denetlemelisiniz **CanGoBack** özelliği. Bir girdiye geri gitmek için çağrı **GoBack** yöntemi. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Eğer **GoForward**, ve İleri Gezinme geçmişi içinde hiç girdi yok veya çağırırsanız **GoBack**, ve geri Gezinme geçmişi içinde hiç girdi yok bir <xref:System.InvalidOperationException> oluşturulur.
