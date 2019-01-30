---
title: 'Nasıl yapılır: Uygulama Oturumları Arasında Uygulama Kapsamı Özelliklerini Koruma ve Geri Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: c64b13717a427bf7ad8f9cab0a450162ad0c6cde
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204710"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="6b23d-102">Nasıl yapılır: Uygulama Oturumları Arasında Uygulama Kapsamı Özelliklerini Koruma ve Geri Yükleme</span><span class="sxs-lookup"><span data-stu-id="6b23d-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="6b23d-103">Bu örnek, bir uygulama kapatıldığında ve geri yüklemek için bir uygulamanın sonraki açılışında uygulama kapsamı özelliklerini nasıl uygulama kapsamı özelliklerini kalıcı olarak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b23d-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b23d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b23d-104">Example</span></span>  
 <span data-ttu-id="6b23d-105">Uygulama için uygulama kapsamı özelliklerini devam ediyorsa ve yalıtılmış depolama alanından, geri yükler.</span><span class="sxs-lookup"><span data-stu-id="6b23d-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="6b23d-106">Yalıtılmış Depolama güvenli bir şekilde dosya erişim izni olmadan uygulamaları tarafından kullanılabilecek bir korumalı depolama alanıdır.</span><span class="sxs-lookup"><span data-stu-id="6b23d-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="6b23d-107">*App.xaml* dosyası tanımlar `App_Startup` yöntemi için bir işleyici olarak <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay ve `App_Exit` yöntemi için bir işleyici olarak <xref:System.Windows.Application.Exit?displayProperty=nameWithType> vurgulanan satırları ilk örnekte gösterildiği gibi olay.</span><span class="sxs-lookup"><span data-stu-id="6b23d-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="6b23d-108">İkinci örnek bir bölümü gösterilmektedir *App.xaml.cs* ve *App.xaml.vb* kodunu vurgular dosyaları `App_Startup` uygulama kapsamı özelliklerini ve yükleryöntemi`App_Exit` yöntemi uygulama kapsamı özelliklerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6b23d-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
