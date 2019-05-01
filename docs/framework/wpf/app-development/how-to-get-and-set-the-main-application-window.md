---
title: 'Nasıl yapılır: Ana Uygulama Penceresini Alma ve Ayarlama'
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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947803"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="f1747-102">Nasıl yapılır: Ana Uygulama Penceresini Alma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f1747-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="f1747-103">Bu örnek nasıl alınacağını ve ana uygulama penceresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1747-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1747-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1747-104">Example</span></span>  
 <span data-ttu-id="f1747-105">İlk <xref:System.Windows.Window> uygulama tarafından otomatik olarak belirlenir Windows Presentation Foundation (WPF) içinde örneği <xref:System.Windows.Application> ana uygulama penceresini olarak.</span><span class="sxs-lookup"><span data-stu-id="f1747-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="f1747-106">İlk <xref:System.Windows.Window> olması başlangıç olarak belirtilen pencere örneklenmiş olacak büyük olasılıkla olmasını [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (bkz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="f1747-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="f1747-107">İlk <xref:System.Windows.Window> da kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f1747-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="f1747-108">Bir örnek, aşağıdaki gibi uygulama başlatma sırasında bir penceresi açıyor:</span><span class="sxs-lookup"><span data-stu-id="f1747-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="f1747-109">Bazı durumlarda, ilk örneği <xref:System.Windows.Window> gerçekten ana uygulama penceresini örn giriş ekranıdır.</span><span class="sxs-lookup"><span data-stu-id="f1747-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="f1747-110">Bu durumda, biçimlendirme, aşağıdaki gibi kullanarak ana uygulama penceresini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1747-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="f1747-111">Ana pencereyi otomatik olarak veya el ile belirtildiğini ana pencereden alabilirsiniz <xref:System.Windows.Application.MainWindow%2A> aşağıdaki kod, aşağıdaki gibi kullanarak:</span><span class="sxs-lookup"><span data-stu-id="f1747-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
