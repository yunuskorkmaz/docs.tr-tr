---
title: Çizgi ve Dolgularda Alfa Karışım Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506110"
---
# <a name="alpha-blending-lines-and-fills"></a>Çizgi ve Dolgularda Alfa Karışım Kullanma
GDI +'da bir renk 32-bit 8 bit her alfa, kırmızı, yeşil ve mavi için değerdir. Renk saydam alfa değeri gösterir — istediğiniz rengi karışık arka plan rengi ile uzantısı. Alfa değerleri aralığı 0 ile 255, burada 0 tamamen saydam bir rengi temsil eder ve 255 arasında bir tam opak rengi temsil eder.  
  
 Alfa karıştırma piksel piksel karıştırma kaynak ve arka plan rengi veri olur. Her bir verilen kaynak rengin üç bileşen (kırmızı, yeşil, mavi) karşılık gelen bileşenle göre şu formül olarak ayarlayın arka plan renginin harmanlanan:  
  
 displayColor sourceColor × alpha = / 255 + backgroundColor × (255 – alfa) / 255  
  
 Örneğin, kaynak rengin kırmızı bileşeni 150 ve arka plan rengini kırmızı bileşeni 100 varsayalım. Alfa değeri 200 ise, sonuç rengin kırmızı bileşeni şu şekilde hesaplanır:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme](how-to-draw-opaque-and-semitransparent-lines.md)  
 Alfa karışık çizgi çizmek gösterilmektedir.  
  
 [Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Fırçalar ile alfa karıştırma açıklanmaktadır.  
  
 [Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Alfa karıştırma kullanarak denetlemek nasıl açıklar <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Nasıl yapılır: Görüntülerdeki alfa değerleri ayarlamak için renk matrisi kullanma](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Nasıl kullanılacağını açıklayan bir <xref:System.Drawing.Imaging.ColorMatrix> alfa karıştırma denetlemek için nesne.
