---
title: 'Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 3148a5901ccf64194717e26664ab8b9cbd57db2a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365964"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı
Gradyan içinde sistem renk kullanmak için kullandığınız  *\<SystemColor >* renk ve  *\<SystemColor >* ColorKey statik özelliklerini <xref:System.Windows.SystemColors> almak için bir renk başvuru yeri  *\<SystemColor >* istenen sistem renk adıdır. Kullanım  *\<SystemColor >* sistem tema değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri. Aksi takdirde kullanın  *\<SystemColor >* Color özelliklerini.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 Sonraki örnek, bir gradyan oluşturmak için statik bir sistem renk kaynakları kullanır.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.SystemColors>
- [Sistem Fırçası ile bir Alanı Boyama](how-to-paint-an-area-with-a-system-brush.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
