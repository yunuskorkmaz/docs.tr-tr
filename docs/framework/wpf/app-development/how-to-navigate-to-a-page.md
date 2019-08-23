---
title: 'Nasıl yapılır: Sayfaya Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 38814268c9bb271ad3d88d549fb6ec4c6cbfed40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966037"
---
# <a name="how-to-navigate-to-a-page"></a>Nasıl yapılır: Sayfaya Gitme
Bu örnekte, bir sayfaya bir <xref:System.Windows.Navigation.NavigationWindow>sayfa üzerinden gidilebileceği çeşitli yollar gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdakilerden birini kullanarak bir <xref:System.Windows.Navigation.NavigationWindow> sayfaya gitmek mümkündür:  
  
- <xref:System.Windows.Navigation.NavigationWindow.Source%2A> Özelliği.  
  
- <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Yöntemi.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]göreli ya da mutlak olabilir. Daha fazla bilgi için bkz. [WPF 'de paket URI 'leri](pack-uris-in-wpf.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
