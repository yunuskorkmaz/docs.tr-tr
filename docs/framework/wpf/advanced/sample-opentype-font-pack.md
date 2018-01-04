---
title: "Örnek OpenType Yazı Tipi Paketi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7390c8c84caa17b984d5a16b7ac6b9704b8f3c6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sample-opentype-font-pack"></a>Örnek OpenType Yazı Tipi Paketi
Bu konu örnek bir bakış sunar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile dağıtılmış yazı tiplerini [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Genişletilmiş örnek yazı tipi desteği [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tarafından kullanılan özellikler [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar.  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType yazı tipi paketi yazı tipleri  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Örnek kümesi sağlar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] oluşturmada kullanabileceğiniz yazı tipleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Örnek yazı tipleri Ascender Corporation lisansı altında sağlanır. Bu yazı tiplerini yalnızca tarafından tanımlanan tüm özelliklerin bir kısmı uygulamak [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] biçimi. Aşağıdaki tabloda örnek adlarını listeler [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi.  
  
|**Ad**|**Dosya**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte kalın|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles açık|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero kalın|Pescab.ttf|  
  
 Aşağıdaki resimde örnek gösterilmektedir [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri gibi görünüyor.  
  
 ![Örnek yazı tipi paketindeki yazı tipi adlarının listesi](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
OpenType yazı tipi paketi yazı tipleri  
  
 Örnek yazı tipleri Ascender Corporation lisansı altında sağlanır. Ascender gelişmiş yazı tipi ürünleri sağlayıcısıdır. Örnek yazı tipleri genişletilmiş veya özel sürümlerinin lisansı için bkz: [Ascender Corporation'ın Web sitesi](http://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Geliştirici olarak bir uygulama içinde katıştırılan veya aksi halde yeniden dağıtmak istediğiniz yazı tipi için gerekli lisans haklarına sahip olmasını sağlamak için sorumluluğundadır.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Yazı tipleri yükleme  
 Örnek yükleme seçeneğiniz [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tiplerini varsayılan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazı tipleri dizini **\WINDOWS\Fonts**. Yazı tiplerini yüklemek için yazı tipleri Denetim Masası'nı kullanın. Bu yazı tipleri bilgisayarınızda olduktan sonra varsayılan başvuran tüm uygulamalar için erişilebilir olduklarını [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazı tipi. Katlama-yazı tipi dosyası tıklayarak birkaç yazı tipi boyutlarında temsilci karakter kümesini görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde Lindsey yazı tipi dosyası, Linds.ttf gösterir.  
  
 ![Lindsey yazı tipi &#40; OpenType &#41; ] (../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey yazı tipi görüntüleme  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Yazı tiplerini kullanma  
 Uygulamanızda yazı tiplerini kullanmanın iki yolu vardır. Proje derleme içindeki kaynaklar olarak gömülü olmayan içerik öğeleri olarak uygulamanıza yazı tiplerini ekleyebilirsiniz. Alternatif olarak, uygulamanın derleme dosyaları içinde katıştırılmış proje kaynak öğeleri olarak uygulamanıza yazı tiplerini ekleyebilirsiniz. Daha fazla bilgi için bkz: [uygulamalarla paketleme yazı tipleri](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.Typography>  
 [OpenType Yazı Tipi Özellikleri](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Uygulamalarla Yazı Tiplerini Paketleme](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
