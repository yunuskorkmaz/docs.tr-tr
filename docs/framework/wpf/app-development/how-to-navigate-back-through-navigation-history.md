---
title: 'Nasıl yapılır: Gezinme Geçmişinde Geriye Doğru Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 86590c2794339ac22cbc8ec5e11224736133e870
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817969"
---
# <a name="how-to-navigate-back-through-navigation-history"></a>Nasıl yapılır: Gezinme Geçmişinde Geriye Doğru Gitme
Bu örnek, geri gezinme geçmişindeki girişlere nasıl gidileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Navigation.NavigationWindow> ,<xref:System.Windows.Navigation.NavigationService>, Veya Internet Explorer 'da barındırılan içerikten çalıştırılan kod, tek seferde bir giriş olan gezinti geçmişi aracılığıyla geri gidebilir. <xref:System.Windows.Controls.Frame>  
  
 Tek bir girdinin geri dönmesi için, önce bir giriş geri gidilerek **CanGoBack** özelliğini Inceleyerek, **GoBack** metodunu çağırarak, geri gezinti geçmişinde girişler olup olmadığını kontrol edin. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoBack** ve **GoBack** , <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationService>tarafından uygulanır.  
  
> [!NOTE]
>  **GoBack**'i çağırırsanız ve geri gezinme geçmişinde hiç giriş yoksa, bir <xref:System.InvalidOperationException> oluşturulur.
