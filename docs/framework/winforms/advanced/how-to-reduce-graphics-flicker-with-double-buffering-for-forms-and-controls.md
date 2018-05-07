---
title: 'Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: 6e11e364af5dc361a24cdd88d72432d6ba4d4058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma
İki kez arabelleğe alma bellek arabelleği birden çok boyama işlemlerle ilişkili titreşimi sorunları ele almak için kullanır. İki kez arabelleğe alma etkinleştirildiğinde, tüm boyama işlemleri ilk ekranda çizim yüzeyini yerine bir arabelleğe işlenir. Tüm boyama işlemleri tamamlandıktan sonra Ara belleğe doğrudan ilişkili çizim yüzeyini kopyalanır. Yalnızca bir grafik işlem ekranda gerçekleştirildiğinden, karmaşık boyama işlemlerle ilişkili görüntü titremeyi ortadan kalkar. Çoğu uygulama için varsayılan iki kez arabelleğe alma sağladığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en iyi sonuçlar sağlar. Varsayılan olarak arabelleğe alınan standart Windows Forms denetimleri çift. Varsayılan, formlarda arabelleğe alma çift etkinleştirebilirsiniz ve denetimleri iki yolla yazıldı. Ya da ayarlayabilirsiniz <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğine `true`, ya da çağırabilirsiniz <xref:System.Windows.Forms.Control.SetStyle%2A> ayarlamak için yöntemin <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> bayrağını `true`. Her iki yöntem varsayılan çift form veya denetim için arabelleğe almayı etkinleştir ve titreşimsiz grafik işleme sağlayın. Çağırma <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi için yazdığınız tüm işleme kod yalnızca fazla özel denetimler için önerilir.  
  
 Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryoları için kendi çift arabelleğe alma mantığını uygulayabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: el ile arabelleğe alınan grafikleri yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Titreşimi azaltmak için  
  
-   Ayarlama <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğine `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- veya -  
  
-   Çağrı <xref:System.Windows.Forms.Control.SetStyle%2A> ayarlamak için yöntemin <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> bayrağını `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [İki Kez Arabelleğe Alınan Grafikler](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
