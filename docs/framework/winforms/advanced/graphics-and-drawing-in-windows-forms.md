---
title: Windows Formlarında Grafikler ve Çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 3dbb5d36ce2e550c0420a23b40247771e10d60ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521608"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Formlarında Grafikler ve Çizim
Ortak dil çalışma zamanı Windows grafik cihaz arabirimi Gelişmiş uygulaması kullanır ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) olarak adlandırılan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik oluşturma, metin çizme ve grafik görüntü nesneleri olarak değiştirmek. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır. Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik görüntüleri Windows formlar ve denetimler üzerinde oluşturulacak. Kullanamasanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] doğrudan Web formlarında grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.  
  
 Bu bölümde, temel ilkeleri tanıtmak konuları bulur [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programlama. Kapsamlı bir başvuru olarak tasarlanmamıştır karşın, bu bölümde hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve bir metin çizim şekiller çizme gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme. Daha fazla bilgi için bkz: [GDI + başvuru](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).  
  
 İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Kod satırlarını, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için nasıl kullanılacağı hakkında konular bulunur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Grafiklere Genel Bakış](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Grafik ilgili yönetilen sınıflar bir giriş sağlar.  
  
 [GDI+ Yönetilen Kodu Hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Yönetilen hakkında bilgi sağlar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.  
  
 [Yönetilen Grafik Sınıflarını Kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Çeşitli kullanarak görevleri tamamlamak gösterilmiştir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yönetilen sınıflar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing>  
 Erişim sağlayan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] temel grafik işlevselliği.  
  
 <xref:System.Drawing.Drawing2D>  
 Vektör grafikleri işlevselliği ve Gelişmiş iki boyutlu sağlar.  
  
 <xref:System.Drawing.Imaging>  
 Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] görüntüleme işlevselliği.  
  
 <xref:System.Drawing.Text>  
 Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tipografi işlevselliği. Bu ad alanındaki sınıflar, yazı tipi koleksiyonları oluşturmak için kullanılabilir.  
  
 <xref:System.Drawing.Printing>  
 Yazdırma işlevselliği sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Denetim Boyama ve İşleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Boyama denetimleri için kod sağlamak nasıl ayrıntıları verilmektedir.
