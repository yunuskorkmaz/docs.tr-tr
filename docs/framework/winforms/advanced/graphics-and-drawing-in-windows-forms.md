---
title: Grafikler ve çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746407"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Formlarında Grafikler ve Çizim
Ortak dil çalışma zamanı, GDI+ adlı Windows Grafik Cihaz Arabirimi (GDI) gelişmiş uygulamasını kullanır. GDI+ ile grafik oluşturabilir, metin çizebilir ve grafik görüntülerini nesne olarak değiştirebilirsiniz. GDI+, performans ve kullanım kolaylığı sunacak şekilde tasarlanmıştır. Windows Forms ve denetimlerinde grafik görüntülerini işlemek için GDI+ kullanabilirsiniz. Doğrudan Web Forms üzerinde GDI+ kullanamazsınız, ancak görüntü Web sunucusu denetimi aracılığıyla grafik görüntüleri görüntüleyebilirsiniz.  
  
 Bu bölümde, GDI+ programlama temellerini ortaya çıkaracak konuları bulacaksınız. Kapsamlı bir başvuru olmasını amaçlanmamış olsa da, bu bölüm <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>ve <xref:System.Drawing.Color> nesneleri hakkında bilgiler içerir ve bu görevlerin, şekil çizme, metin çizme veya görüntü görüntüleme gibi görevleri nasıl gerçekleştirebileceğinizi açıklar. Daha fazla bilgi için bkz. [GDI+ başvurusu](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Hızlı bir başlangıç yapmak ve hemen başlamak istiyorsanız bkz. [Grafik programlamaya Başlarken](getting-started-with-graphics-programming.md). Windows Forms 'ta çizgi, şekil, metin ve daha fazlasını çizmek için kodun nasıl kullanılacağına ilişkin konular içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)  
 Grafiklerle ilgili yönetilen sınıflara bir giriş sağlar.  
  
 [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)  
 Yönetilen GDI+ sınıfları hakkında bilgi sağlar.  
  
 [Yönetilen Grafik Sınıflarını Kullanma](using-managed-graphics-classes.md)  
 GDI+ Yönetilen sınıfları kullanarak çeşitli görevlerin nasıl tamamlandığını gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing>  
 GDI+ temel grafik işlevselliğine erişim sağlar.  
  
 <xref:System.Drawing.Drawing2D>  
 Gelişmiş iki boyutlu ve vektör grafik işlevselliği sağlar.  
  
 <xref:System.Drawing.Imaging>  
 Gelişmiş GDI+ görüntüleme işlevselliği sağlar.  
  
 <xref:System.Drawing.Text>  
 Gelişmiş GDI+ tipografi işlevselliği sağlar. Bu ad alanındaki sınıflar, yazı tipi koleksiyonları oluşturmak ve kullanmak için kullanılabilir.  
  
 <xref:System.Drawing.Printing>  
 Yazdırma işlevlerini sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Denetim Boyama ve İşleme](../controls/custom-control-painting-and-rendering.md)  
 Boyama denetimleri için kod sağlama hakkında ayrıntılı bilgi.
