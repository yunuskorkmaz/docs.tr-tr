---
title: Windows Formlarında Grafikler ve Çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505546"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Formlarında Grafikler ve Çizim
Ortak dil çalışma zamanı, Gelişmiş bir uygulaması, Windows grafik cihaz arabirimi (GDI +'OLARAK adlandırılan GDI) kullanır. GDI + ile grafikler oluşturabilir, metin çizme ve grafik görüntüleri nesneler olarak yönetmek. GDI +'da performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır. Windows formlar ve denetimler grafik görüntülerinde işlenecek GDI +'da kullanabilirsiniz. GDI +'da doğrudan Web formlarında kullanamasanız, grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.  
  
 Bu bölümde, GDI + programlamanın temellerini tanıtan konuları bulur. Kapsamlı bir referans olacak şekilde tasarlanmamıştır olsa da, bu bölüm hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve şekiller, metin çizme çizim gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme. Daha fazla bilgi için [GDI +'BAŞVURU](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](getting-started-with-graphics-programming.md). Kod satırları, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için kullanma hakkında konular bulunur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)  
 Grafikler ile ilgili yönetilen sınıflar için bir giriş sağlar.  
  
 [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)  
 Yönetilen GDI + sınıflar hakkında bilgi sağlar.  
  
 [Yönetilen Grafik Sınıflarını Kullanma](using-managed-graphics-classes.md)  
 Nasıl için tam çeşitli görevleri kullanarak GDI + yönetilen sınıflar gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing>  
 GDI + grafik temel işlevlerini erişim sağlar.  
  
 <xref:System.Drawing.Drawing2D>  
 Gelişmiş iki boyutlu sağlar ve vektör grafik işlevlerini.  
  
 <xref:System.Drawing.Imaging>  
 Gelişmiş GDI görüntüleme işlevlerini + sağlar.  
  
 <xref:System.Drawing.Text>  
 Gelişmiş GDI + tipografi işlevlerini sağlar. Bu ad alanındaki sınıflar oluşturmak ve yazı tipi koleksiyonları kullanmak için kullanılabilir.  
  
 <xref:System.Drawing.Printing>  
 Yazdırma işlevselliği sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Denetim Boyama ve İşleme](../controls/custom-control-painting-and-rendering.md)  
 Boyama denetimleri için kodu sağlayabilir açıklanmaktadır.
