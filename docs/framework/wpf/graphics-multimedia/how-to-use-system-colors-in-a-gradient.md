---
title: 'Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562186"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı
Bir gradyan içerisinde sistem rengi kullanmak için kullandığınız  *\<SystemColor >* renk ve  *\<SystemColor >* ColorKey statik özelliklerini <xref:System.Windows.SystemColors> elde etmek için sınıf bir renk referansı nerede  *\<SystemColor >* istenen sistem rengi adıdır. Kullanım  *\<SystemColor >* sistem teması değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri. Aksi takdirde kullanın  *\<SystemColor >* renk özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 Sonraki örnek gradyan oluşturmak için statik sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SystemColors>  
 [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
