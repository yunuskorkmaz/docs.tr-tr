---
title: "Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi"
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
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142c2faa01c32ac6602e80eaef18779f93154aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi
Görsel nesneler içinde oluşturduğunuz bir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] görsel nesneler için bir konak pencere kapsayıcı sağlayarak penceresi. Olay kapsanan görsel nesneler için işleme sağlamak için konak penceresi kapsayıcının ileti filtre döngüsüne geçirilen iletileri işleyin. Başvurmak [Öğreticisi: görsel nesneleri bir Win32 uygulaması barındırma](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) görsel nesneleri barındırmak hakkında daha fazla bilgi için bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod için fare olay işleyicilerini ayarlama gösterilmektedir bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] konak kapsayıcısı olarak görsel nesneler için kullanılan penceresi.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Aşağıdaki örnek, belirli fare olayları yakalama yanıt isabet testi ayarlama gösterilmektedir.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Nesne sunar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içinde içerik bir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] penceresi. Değeri <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource> nesnesi görsel ağaç hiyerarşideki en üst düğümü temsil eder.  
  
 Win32 Konak Kapsayıcısı kullanarak isabet sınaması tam örnek nesneleri için bkz: [isabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndSource>  
 [Görsel Katmanda Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
