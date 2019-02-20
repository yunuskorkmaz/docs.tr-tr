---
title: Windows Formlarında Grafikler ve Çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e6d3c395a2d5b8ae885114a53b230d7265102bc8
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441170"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Formlarında Grafikler ve Çizim
Ortak dil çalışma zamanı kullanan Windows grafik cihaz arabirimi Gelişmiş uygulaması ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) olarak adlandırılan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafikler oluşturun, metin çizme ve grafik görüntüleri nesneler olarak yönetmek. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır. Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik görüntüleri Windows formlar ve denetimler üzerinde oluşturulacak. Kullanamasanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] doğrudan Web formlarında, grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.  
  
 Bu bölümde, temelleri tanıtan konuları bulabilirsiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programlama. Kapsamlı bir referans olacak şekilde tasarlanmamıştır olsa da, bu bölüm hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve şekiller, metin çizme çizim gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme. Daha fazla bilgi için [GDI +'BAŞVURU](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Kod satırları, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için kullanma hakkında konular bulunur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Grafiklere Genel Bakış](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Grafikler ile ilgili yönetilen sınıflar için bir giriş sağlar.  
  
 [GDI+ Yönetilen Kodu Hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Yönetilen hakkında bilgi sağlar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.  
  
 [Yönetilen Grafik Sınıflarını Kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Çeşitli kullanarak görevleri tamamlamak gösterilmiştir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yönetilen sınıflar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing>  
 Erişim sağlayan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] temel grafik işlevselliği.  
  
 <xref:System.Drawing.Drawing2D>  
 Gelişmiş iki boyutlu sağlar ve vektör grafik işlevlerini.  
  
 <xref:System.Drawing.Imaging>  
 Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] görüntüleme işlevlerini.  
  
 <xref:System.Drawing.Text>  
 Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tipografi işlevselliği. Bu ad alanındaki sınıflar oluşturmak ve yazı tipi koleksiyonları kullanmak için kullanılabilir.  
  
 <xref:System.Drawing.Printing>  
 Yazdırma işlevselliği sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Denetim Boyama ve İşleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Boyama denetimleri için kodu sağlayabilir açıklanmaktadır.
