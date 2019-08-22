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
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666721"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Nasıl yapılır: Uygulama Oturumları Arasında Uygulama Kapsamı Özelliklerini Koruma ve Geri Yükleme
Bu örnek, bir uygulama kapandığında uygulama kapsamı özelliklerinin nasıl devam ettirilemeyeceğini ve bir uygulamanın bir sonraki başlatıldığında uygulama kapsamı özelliklerinin nasıl geri yükleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Uygulama, uygulama kapsamı özelliklerini için devam ettirir ve yalıtılmış depolama alanından geri yükler. Yalıtılmış depolama, dosya erişim izni olmayan uygulamalar tarafından güvenli bir şekilde kullanılabilecek, korumalı bir depolama alanıdır.  *App. xaml* dosyası, ilk Örneğin `App_Startup` vurgulanan satırlarında gösterildiği gibi, yöntemi <xref:System.Windows.Application.Startup?displayProperty=nameWithType> olay işleyicisi olarak ve `App_Exit` <xref:System.Windows.Application.Exit?displayProperty=nameWithType> olay işleyicisi olarak yöntemini tanımlar. İkinci örnek, *app.xaml.cs* ve *app. xaml. vb* dosyalarının, uygulama kapsamı özelliklerini geri yükleyen yöntemi ve `App_Startup` `App_Exit` uygulama kapsamını kaydeden yöntemini vurgulayan bir bölümünü gösterir özelliklerinin.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
