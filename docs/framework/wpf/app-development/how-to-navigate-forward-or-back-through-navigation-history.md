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
ms.openlocfilehash: 76a78debdce14123cc465ac9abf4db906fe0a2df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961345"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme
Bu örnek, gezinme geçmişinde girişlerin ileri veya geri nasıl gezindiğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konaklardaki içerikten çalıştırılan kod, tek seferde bir giriş olmak üzere gezinti geçmişi ile ileri veya geri gidebilir.  
  
- <xref:System.Windows.Navigation.NavigationWindow>kullanarak<xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame>kullanarak<xref:System.Windows.Navigation.NavigationService>  
  
- Internet Explorer  
  
 Bir giriş ileri gidebilmeniz için önce **CanGoForward** özelliğini inceleyerek ileri gezinme geçmişine giriş olup olmadığını kontrol etmeniz gerekir. Bir giriş ileri gitmek için **GoForward** yöntemini çağırın. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Bir giriş geri gidebilmeniz için önce **CanGoBack** özelliğini inceleyerek geri gezinti geçmişinde girişler olup olmadığını kontrol etmeniz gerekir. Bir giriş geri gitmek için **GoBack** metodunu çağırın. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**ve **GoBack** <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>tarafından uygulanır.  
  
> [!NOTE]
> **GoForward**çağırır ve ileri gezinme geçmişinde hiç giriş yoksa veya **GoBack**'i çağırırsanız ve geri gezinme geçmişinde hiç giriş yoksa, bir <xref:System.InvalidOperationException> oluşturulur.
