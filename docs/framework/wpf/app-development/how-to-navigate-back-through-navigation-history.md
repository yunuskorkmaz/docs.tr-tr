---
title: 'Nasıl yapılır: geri gezinti geçmişinde gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 9acbc5d3388a8df0ec7d7b5326f449f092f0cb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546682"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Nasıl yapılır: geri gezinti geçmişinde gezinme
Bu örnek, Gezinme geçmişi arkada girişleri için gezinme göstermektedir.  
  
## <a name="example"></a>Örnek  
 İçinde barındırılan içerikten çalışan kod bir <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> kullanmak <xref:System.Windows.Navigation.NavigationService>, veya [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] geri geçmişinde gezinme, bir kerede bir girdiye gidebilir.  
  
 Gezinme geri bir girişi gerektiren olduğunu girişleri geri gezinti geçmişinde incelenerek ilk denetimi **CanGoBack** gezinme yedeklenmeden önce bir girdi çağırarak özelliği **GoBack** yöntem. Bu aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Çağırırsanız **GoBack**, ve geri gezinti geçmişinde hiçbir girdi yoksa bir <xref:System.InvalidOperationException> tetiklenir.
