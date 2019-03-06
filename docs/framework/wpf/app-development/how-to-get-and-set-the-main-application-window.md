---
title: 'Nasıl yapılır: Alma ve ana uygulama penceresi ayarlama'
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
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373562"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Nasıl yapılır: Alma ve ana uygulama penceresi ayarlama
Bu örnek nasıl alınacağını ve ana uygulama penceresini gösterir.  
  
## <a name="example"></a>Örnek  
 İlk <xref:System.Windows.Window> uygulama tarafından otomatik olarak belirlenir Windows Presentation Foundation (WPF) içinde örneği <xref:System.Windows.Application> ana uygulama penceresini olarak. İlk <xref:System.Windows.Window> olması başlangıç olarak belirtilen pencere örneklenmiş olacak büyük olasılıkla olmasını [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (bkz <xref:System.Windows.Application.StartupUri%2A>).  
  
 İlk <xref:System.Windows.Window> da kod kullanılarak oluşturulabilir. Bir örnek, aşağıdaki gibi uygulama başlatma sırasında bir penceresi açıyor:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Bazı durumlarda, ilk örneği <xref:System.Windows.Window> gerçekten ana uygulama penceresini örn giriş ekranıdır. Bu durumda, biçimlendirme, aşağıdaki gibi kullanarak ana uygulama penceresini belirtebilirsiniz:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Ana pencereyi otomatik olarak veya el ile belirtildiğini ana pencereden alabilirsiniz <xref:System.Windows.Application.MainWindow%2A> aşağıdaki kod, aşağıdaki gibi kullanarak:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
