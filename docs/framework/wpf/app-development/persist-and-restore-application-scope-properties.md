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
ms.openlocfilehash: 99b04060d4e7c14313655010dc4fbd5ce1c90487
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977658"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Nasıl yapılır: Uygulama Oturumları Arasında Uygulama Kapsamı Özelliklerini Koruma ve Geri Yükleme
Bu örnek, bir uygulama kapatıldığında ve geri yüklemek için bir uygulamanın sonraki açılışında uygulama kapsamı özelliklerini nasıl uygulama kapsamı özelliklerini kalıcı olarak gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Uygulama için uygulama kapsamı özelliklerini devam ediyorsa ve yalıtılmış depolama alanından, geri yükler. Yalıtılmış Depolama güvenli bir şekilde dosya erişim izni olmadan uygulamaları tarafından kullanılabilecek bir korumalı depolama alanıdır.  *App.xaml* dosyası tanımlar `App_Startup` yöntemi için bir işleyici olarak <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay ve `App_Exit` yöntemi için bir işleyici olarak <xref:System.Windows.Application.Exit?displayProperty=nameWithType> vurgulanan satırları ilk örnekte gösterildiği gibi olay. İkinci örnek bir bölümü gösterilmektedir *App.xaml.cs* ve *App.xaml.vb* kodunu vurgular dosyaları `App_Startup` uygulama kapsamı özelliklerini ve yükleryöntemi`App_Exit` yöntemi uygulama kapsamı özelliklerini kaydeder.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
