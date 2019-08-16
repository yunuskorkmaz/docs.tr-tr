---
title: Örnek OpenType Yazı Tipi Paketi
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: e2b3dc3b95cf81a60494f7a02488067717938e97
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545232"
---
# <a name="sample-opentype-font-pack"></a>Örnek OpenType Yazı Tipi Paketi
Bu konu, [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]Ile dağıtılan örnek OpenType yazı tiplerine genel bir bakış sağlar. Örnek yazı tipleri, uygulamalar tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanılabilen genişletilmiş OpenType özelliklerini destekler.  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType yazı tipi paketindeki yazı tipleri  
 , [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Uygulamalar oluşturmak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] için kullanabileceğiniz örnek bir OpenType yazı tipi kümesi sağlar. Örnek yazı tipleri, Ascender Corporation lisansı altında sağlanır. Bu yazı tipleri, OpenType biçimi tarafından tanımlanan toplam özelliklerin yalnızca bir alt kümesini uygular. Aşağıdaki tabloda örnek OpenType yazı tiplerinin adları listelenmektedir.  
  
|**Ad**|**Dosya**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Juniors|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles ışığı|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 Aşağıdaki çizimde örnek OpenType yazı tiplerinin nasıl görüneceği gösterilmektedir.  
  
 ![Örnek yazı tipi paketindeki yazı tipi adlarının listesi](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Örnek yazı tipleri, Ascender Corporation lisansı altında sağlanır. Ascender, gelişmiş yazı tipi ürünlerinin bir sağlayıcısıdır. Örnek yazı tiplerinin genişletilmiş veya özel sürümlerini lisanslamak için, bkz. [Ascender Corporation 'ın Web sitesi](https://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Geliştirici olarak, bir uygulama içine eklediğiniz veya başka bir şekilde yeniden dağıtırabilmeniz gereken herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Yazı tiplerini yükleme  
 Örnek OpenType yazı tiplerini, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] **\Windows\Fonts**dizinine varsayılan Fonts dizinine yükleme seçeneğiniz vardır. Yazı tiplerini yüklemek için yazı tipleri denetim masasını kullanın. Bu yazı tipleri bilgisayarınızda olduktan sonra, varsayılan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazı tiplerine başvuran tüm uygulamalar tarafından erişilebilir. Yazı tipi dosyasına çift tıklayarak çeşitli yazı tipi boyutlarında temsili bir karakter kümesi görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde Lindsey yazı tipi dosyası, Linds. ttf gösterilmektedir.  
  
 ![Lindsey yazı &#40;tipi&#41; OpenType](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey yazı tipini görüntüleme  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Yazı tiplerini kullanma  
 Uygulamanızda yazı tiplerini kullanmanın iki yolu vardır. Uygulamanıza, derleme içinde kaynak olarak gömülü olmayan proje içerik öğeleri olarak yazı tipi ekleyebilirsiniz. Alternatif olarak, uygulamanıza, uygulamanın derleme dosyaları içine katıştırılmış proje kaynak öğeleri olarak yazı tipleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [uygulamaları Ile paketleme yazı tipleri](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)
