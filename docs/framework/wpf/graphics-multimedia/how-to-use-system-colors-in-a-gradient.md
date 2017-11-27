---
title: "Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı
Bir gradyan içerisinde sistem rengi kullanmak için kullandığınız  *\<SystemColor >*renk ve  *\<SystemColor >*ColorKey statik özelliklerini <xref:System.Windows.SystemColors> elde etmek için sınıf bir renk referansı nerede  *\<SystemColor >* istenen sistem rengi adıdır. Kullanım  *\<SystemColor >*sistem teması değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri. Aksi takdirde kullanın  *\<SystemColor >*renk özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 Sonraki örnek gradyan oluşturmak için statik sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SystemColors>  
 [Sistem fırçası ile bir alanı boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Boyama düz renklerle ve gradyan genel bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
