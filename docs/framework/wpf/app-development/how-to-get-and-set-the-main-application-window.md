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
ms.locfileid: "33547988"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="da139-102">Nasıl yapılır: alma ve ana uygulama penceresi ayarlama</span><span class="sxs-lookup"><span data-stu-id="da139-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="da139-103">Bu örnek, get ve ana uygulama penceresi set gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da139-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da139-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="da139-104">Example</span></span>  
 <span data-ttu-id="da139-105">İlk <xref:System.Windows.Window> içinde bir Windows Presentation Foundation (uygulama tarafından otomatik olarak belirlenir WPF) örneği <xref:System.Windows.Application> ana uygulama penceresi olarak.</span><span class="sxs-lookup"><span data-stu-id="da139-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="da139-106">İlk <xref:System.Windows.Window> başlatılan işlem büyük olasılıkla başlangıç belirtilen pencere hesaplanması için [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (bkz: <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="da139-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="da139-107">İlk <xref:System.Windows.Window> kod kullanarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="da139-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="da139-108">Bir örnek, aşağıdaki gibi uygulama başlatma sırasında bir penceresi açıyor:</span><span class="sxs-lookup"><span data-stu-id="da139-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="da139-109">Bazı durumlarda, ilk örneği <xref:System.Windows.Window> gerçekten ana uygulama Örneğin giriş ekranı penceredir.</span><span class="sxs-lookup"><span data-stu-id="da139-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="da139-110">Bu durumda, aşağıdaki gibi biçimlendirme kullanarak ana uygulama penceresi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da139-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="da139-111">Ana penceresinde otomatik veya el ile belirtildiğini ana penceresinden alabilirsiniz <xref:System.Windows.Application.MainWindow%2A> aşağıdaki gibi aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="da139-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
