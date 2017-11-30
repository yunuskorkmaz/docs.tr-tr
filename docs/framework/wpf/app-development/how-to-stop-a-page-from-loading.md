---
title: "Nasıl yapılır: bir sayfanın yüklenmesini durdurmak"
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
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b68936ed83a61fc6d4c80408bd055c0eb05e030d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-stop-a-page-from-loading"></a>Nasıl yapılır: bir sayfanın yüklenmesini durdurmak
Bu örnek nasıl çağrılacağını gösterir <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> indirilmesi bitmeden önce içerik için Gezinti durdurmak için yöntem.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>İstenen içeriğin indirilmesini durdurur ve neden <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> çıkarılmasına olay.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
