---
title: "Nasıl yapılır: alma ve ana uygulama penceresi ayarlama"
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
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d6bca158172fd3fc31526287c6d4a9928a8ea0c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="078bd-102">Nasıl yapılır: alma ve ana uygulama penceresi ayarlama</span><span class="sxs-lookup"><span data-stu-id="078bd-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="078bd-103">Bu örnek, get ve ana uygulama penceresi set gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="078bd-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="078bd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="078bd-104">Example</span></span>  
 <span data-ttu-id="078bd-105">İlk <xref:System.Windows.Window> içinde örneği bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulama tarafından otomatik olarak belirlenir <xref:System.Windows.Application> ana uygulama penceresi olarak.</span><span class="sxs-lookup"><span data-stu-id="078bd-105">The first <xref:System.Windows.Window> that is instantiated within a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="078bd-106">İlk <xref:System.Windows.Window> başlatılan işlem büyük olasılıkla başlangıç belirtilen pencere hesaplanması için [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (bkz: <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="078bd-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="078bd-107">İlk <xref:System.Windows.Window> kod kullanarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="078bd-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="078bd-108">Bir örnek, aşağıdaki gibi uygulama başlatma sırasında bir penceresi açıyor:</span><span class="sxs-lookup"><span data-stu-id="078bd-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="078bd-109">Bazı durumlarda, ilk örneği <xref:System.Windows.Window> gerçekten ana uygulama Örneğin giriş ekranı penceredir.</span><span class="sxs-lookup"><span data-stu-id="078bd-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="078bd-110">Bu durumda, aşağıdaki gibi biçimlendirme kullanarak ana uygulama penceresi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="078bd-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="078bd-111">Ana penceresinde otomatik veya el ile belirtildiğini ana penceresinden alabilirsiniz <xref:System.Windows.Application.MainWindow%2A> aşağıdaki gibi aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="078bd-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
