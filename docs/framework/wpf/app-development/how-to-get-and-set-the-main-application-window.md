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
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="251ce-103">Nasıl yapılır: Ana uygulama penceresini alma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="251ce-103">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="251ce-104">Bu örnek, ana uygulama penceresinin nasıl alınacağını ve ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="251ce-104">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="251ce-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="251ce-105">Example</span></span>  
 <span data-ttu-id="251ce-106"><xref:System.Windows.Window>Bir Windows Presentation Foundation (WPF) uygulaması içinde oluşturulan ilki otomatik olarak <xref:System.Windows.Application> ana uygulama penceresi olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="251ce-106">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="251ce-107">İlk <xref:System.Windows.Window> örneklendirmesi, büyük olasılıkla başlangıç Tekdüzen Kaynak tanımlayıcısı (URI) (bkz.) olarak belirtilen pencere olacaktır <xref:System.Windows.Application.StartupUri%2A> .</span><span class="sxs-lookup"><span data-stu-id="251ce-107">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup uniform resource identifier (URI) (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="251ce-108">İlki <xref:System.Windows.Window> kod kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="251ce-108">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="251ce-109">Bir örnek, uygulamanın başlatılması sırasında aşağıdaki gibi bir pencere açıyor:</span><span class="sxs-lookup"><span data-stu-id="251ce-109">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="251ce-110">Bazı durumlarda, ilk örneği <xref:System.Windows.Window> aslında ana uygulama penceresi (örn. bir giriş ekranı) değildir.</span><span class="sxs-lookup"><span data-stu-id="251ce-110">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="251ce-111">Bu durumda, aşağıdaki gibi, biçimlendirme kullanarak ana uygulama penceresini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="251ce-111">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="251ce-112">Ana pencerenin otomatik olarak mı yoksa el ile mi belirtilmediğini aşağıda olduğu gibi, ana pencerenin <xref:System.Windows.Application.MainWindow%2A> aşağıdaki kodu kullanmasını sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="251ce-112">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
