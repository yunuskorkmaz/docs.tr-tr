---
title: "Windows Formlarında Grafikler ve Çizim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b2e8bde5d1c2904723282f03a815f17c5cc7622d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Formlarında Grafikler ve Çizim
Ortak dil çalışma zamanı Windows grafik cihaz arabirimi Gelişmiş uygulaması kullanır ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) olarak adlandırılan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik oluşturma, metin çizme ve grafik görüntü nesneleri olarak değiştirmek. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır. Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik görüntüleri Windows formlar ve denetimler üzerinde oluşturulacak. Kullanamasanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] doğrudan Web formlarında grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.  
  
 Bu bölümde, temel ilkeleri tanıtmak konuları bulur [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programlama. Kapsamlı bir başvuru olarak tasarlanmamıştır karşın, bu bölümde hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve bir metin çizim şekiller çizme gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme. Daha fazla bilgi için bkz: [GDI + başvuru](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).  
  
 İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Kod satırlarını, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için nasıl kullanılacağı hakkında konular bulunur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Grafiklere genel bakış](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Grafik ilgili yönetilen sınıflar bir giriş sağlar.  
  
 [GDI + yönetilen kodu hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Yönetilen hakkında bilgi sağlar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.  
  
 [Yönetilen grafik sınıflarını kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
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
 [Özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Boyama denetimleri için kod sağlamak nasıl ayrıntıları verilmektedir.
