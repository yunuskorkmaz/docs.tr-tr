---
title: 'Nasıl yapılır: Ana uygulama penceresini alma ve ayarlama'
description: Windows Presentation Foundation (WPF) uygulaması içindeki ana uygulama penceresini almak ve ayarlamak için bu örneği izleyin.
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
ms.openlocfilehash: 9bb5bce9b90482796acd8c62e77dc8bd9a850eeb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622685"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Nasıl yapılır: Ana uygulama penceresini alma ve ayarlama
Bu örnek, ana uygulama penceresinin nasıl alınacağını ve ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Window>Bir Windows Presentation Foundation (WPF) uygulaması içinde oluşturulan ilki otomatik olarak <xref:System.Windows.Application> ana uygulama penceresi olarak ayarlanır. İlk <xref:System.Windows.Window> örneklendirmesi, büyük olasılıkla başlangıç Tekdüzen Kaynak tanımlayıcısı (URI) (bkz.) olarak belirtilen pencere olacaktır <xref:System.Windows.Application.StartupUri%2A> .  
  
 İlki <xref:System.Windows.Window> kod kullanılarak da oluşturulabilir. Bir örnek, uygulamanın başlatılması sırasında aşağıdaki gibi bir pencere açıyor:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Bazı durumlarda, ilk örneği <xref:System.Windows.Window> aslında ana uygulama penceresi (örn. bir giriş ekranı) değildir. Bu durumda, aşağıdaki gibi, biçimlendirme kullanarak ana uygulama penceresini belirtebilirsiniz:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Ana pencerenin otomatik olarak mı yoksa el ile mi belirtilmediğini aşağıda olduğu gibi, ana pencerenin <xref:System.Windows.Application.MainWindow%2A> aşağıdaki kodu kullanmasını sağlayabilirsiniz:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
