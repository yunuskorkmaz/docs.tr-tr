---
title: 'Nasıl yapılır: Ana uygulama penceresini alma ve ayarlama'
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582553"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Nasıl yapılır: Ana uygulama penceresini alma ve ayarlama
Bu örnek, ana uygulama penceresinin nasıl alınacağını ve ayarlanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bir Windows Presentation Foundation (WPF) uygulaması içinde oluşturulan ilk <xref:System.Windows.Window>, ana uygulama penceresi olarak <xref:System.Windows.Application> tarafından otomatik olarak ayarlanır. Örnek olarak oluşturulacak ilk <xref:System.Windows.Window>, büyük olasılıkla başlangıç Tekdüzen Kaynak tanımlayıcısı (URI) olarak belirtilen pencere olacaktır (bkz. <xref:System.Windows.Application.StartupUri%2A>).  
  
 İlk <xref:System.Windows.Window> kod kullanılarak da oluşturulabilir. Bir örnek, uygulamanın başlatılması sırasında aşağıdaki gibi bir pencere açıyor:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Bazı durumlarda, ilk oluşturulan <xref:System.Windows.Window> aslında ana uygulama penceresi (örn. bir giriş ekranı) değildir. Bu durumda, aşağıdaki gibi, biçimlendirme kullanarak ana uygulama penceresini belirtebilirsiniz:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Ana pencerenin otomatik olarak mı yoksa el ile mi belirtilmediğini aşağıda olduğu gibi aşağıdaki kodu kullanarak <xref:System.Windows.Application.MainWindow%2A> ana pencereyi alabilirsiniz:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
