---
title: 'Nasıl yapılır: alma ve ana uygulama penceresi ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ae70b482eba8fb4e0bf587def06bb90d751a4312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Nasıl yapılır: alma ve ana uygulama penceresi ayarlama
Bu örnek, get ve ana uygulama penceresi set gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 İlk <xref:System.Windows.Window> içinde bir Windows Presentation Foundation (uygulama tarafından otomatik olarak belirlenir WPF) örneği <xref:System.Windows.Application> ana uygulama penceresi olarak. İlk <xref:System.Windows.Window> başlatılan işlem büyük olasılıkla başlangıç belirtilen pencere hesaplanması için [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (bkz: <xref:System.Windows.Application.StartupUri%2A>).  
  
 İlk <xref:System.Windows.Window> kod kullanarak da oluşturulabilir. Bir örnek, aşağıdaki gibi uygulama başlatma sırasında bir penceresi açıyor:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Bazı durumlarda, ilk örneği <xref:System.Windows.Window> gerçekten ana uygulama Örneğin giriş ekranı penceredir. Bu durumda, aşağıdaki gibi biçimlendirme kullanarak ana uygulama penceresi belirtebilirsiniz:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Ana penceresinde otomatik veya el ile belirtildiğini ana penceresinden alabilirsiniz <xref:System.Windows.Application.MainWindow%2A> aşağıdaki gibi aşağıdaki kodu kullanarak:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
