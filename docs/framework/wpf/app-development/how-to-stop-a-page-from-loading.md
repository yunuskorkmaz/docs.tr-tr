---
title: 'Nasıl yapılır: Sayfanın Yüklenmesini Durdurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006687"
---
# <a name="how-to-stop-a-page-from-loading"></a>Nasıl yapılır: Sayfanın Yüklenmesini Durdurma
Bu örnek nasıl çağrılacağını gösterir <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> indirilmesi bitmeden önce içerik gezintisini durdurmak için yöntemi.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> İstenen içeriğin indirilmesini durdurur ve neden <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> olay oluşturulur.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
