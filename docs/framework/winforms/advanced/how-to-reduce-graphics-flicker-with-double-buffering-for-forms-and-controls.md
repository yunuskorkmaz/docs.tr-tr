---
title: 'Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma'
description: Windows Forms için çift arabelleğe alma ile grafik titreşimini azaltmayı öğrenin ve boyama işlemleriyle ilişkili titreşim sorunlarını gidermek için denetimleri kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618135"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma
Çift arabelleğe alma, birden çok boyama işlemiyle ilişkili titreşim sorunlarını gidermek için bir bellek arabelleği kullanır. Çift arabelleğe alma etkinleştirildiğinde, tüm boyama işlemleri, ekranda çizim yüzeyi yerine öncelikle bir bellek arabelleğine işlenir. Tüm boyama işlemleri tamamlandıktan sonra, bellek arabelleği doğrudan onunla ilişkili çizim yüzeyine kopyalanır. Ekranda yalnızca bir grafik işlemi gerçekleştirildiğinden, karmaşık boyama işlemleriyle ilişkili görüntü titreşmesini ortadan kaldırmıştır. Çoğu uygulama için, .NET Framework tarafından belirtilen varsayılan çift arabelleğe alma en iyi sonuçları sağlayacaktır. Standart Windows Forms denetimleri varsayılan olarak iki kez arabelleğe alınır. Formlarınızın ve yazılan denetimlerde varsayılan çift arabelleğe almayı iki şekilde etkinleştirebilirsiniz. <xref:System.Windows.Forms.Control.DoubleBuffered%2A>Özelliğini olarak ayarlayabilir `true` ya da <xref:System.Windows.Forms.Control.SetStyle%2A> bayrağını olarak ayarlamak için yöntemini çağırabilirsiniz <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> `true` . Her iki yöntem de, formunuz veya denetiminiz için varsayılan çift arabelleğe almayı etkinleştirir ve titreşimsiz grafik işleme sağlar. Yöntemi çağırmak <xref:System.Windows.Forms.Control.SetStyle%2A> yalnızca tüm işleme kodunu yazdığınız özel denetimler için önerilir.  
  
 Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryolarında kendi çift arabelleğe alma mantığınızı uygulayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Titreşimi azaltmak için  
  
- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>Özelliğini olarak ayarlayın `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \-veya  
  
- <xref:System.Windows.Forms.Control.SetStyle%2A>Bayrağını ayarlamak için yöntemini çağırın <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [İki Kez Arabelleğe Alınan Grafikler](double-buffered-graphics.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
