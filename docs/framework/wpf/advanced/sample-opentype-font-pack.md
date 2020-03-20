---
title: Örnek OpenType Yazı Tipi Paketi
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 30cb69fcf05108822e8f3e2d45c9e79dbced26ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181904"
---
# <a name="sample-opentype-font-pack"></a>Örnek OpenType Yazı Tipi Paketi
Bu konu, Windows SDK ile dağıtılan örnek OpenType yazı tiplerine genel bir bakış sağlar. Örnek yazı tipleri, uygulamalar tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanılabilecek genişletilmiş OpenType özelliklerini destekler.  

<a name="overview"></a>
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType Font Paketi'ndeki yazı tipleri  
 Windows SDK, uygulama oluştururken [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanabileceğiniz bir dizi örnek OpenType yazı tipi sağlar. Örnek yazı tipleri Ascender Corporation lisansı altında sağlanır. Bu yazı tipleri, OpenType biçimi tarafından tanımlanan toplam özelliklerin yalnızca bir alt kümesini uygular. Aşağıdaki tabloda opentype yazı tiplerinin adları listelenir.  
  
|**Adı**|**Dosya**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Kalın|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Perikles Işık|Pericl.ttf|  
|Palatino|Pesca.ttf|  
|Pescadero Kalın|Pescab.ttf|  
  
 Aşağıdaki resimde, örnek OpenType yazı tiplerinin nasıl göründüğü gösterilmektedir.  
  
 ![Örnek yazı tipi paketindeki yazı tipi adlarının listesi](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Örnek yazı tipleri Ascender Corporation lisansı altında sağlanır. Ascender gelişmiş yazı tipi ürünleri sağlayıcısıdır. Örnek yazı tiplerinin genişletilmiş veya özel sürümlerini lisanslamak için [Ascender Corporation'ın Web sitesine](https://www.monotype.com/)bakın.  
  
> [!NOTE]
> Bir geliştirici olarak, bir uygulamaya katıştırdığınız veya başka bir şekilde yeniden dağıttığınız herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.  
  
<a name="installing_the_fonts"></a>
## <a name="installing-the-fonts"></a>Yazı Tiplerini Yükleme  
 Örnek OpenType yazı tiplerini varsayılan Windows Fontlar dizini, **\WINDOWS\Fontlar'a**yükleme seçeneğiniz vardır. Yazı tiplerini yüklemek için Fontlar denetim panelini kullanın. Bu yazı tipleri bilgisayarınızda bir kez açıldıktan sonra, varsayılan Windows yazı tiplerine başvuran tüm uygulamalar tarafından erişilebilir. Yazı tipi dosyasını iki katına çıkararak çeşitli yazı tipi boyutlarında temsili karakter kümesini görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsü Lindsey yazı tipi dosyasını gösterir, Linds.ttf.  
  
 ![Lindsey font &#40;OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey yazı tipini görüntüleme  
  
<a name="using_the_fonts"></a>
## <a name="using-the-fonts"></a>Yazı Tiplerini Kullanma  
 Uygulamanızda yazı tiplerini kullanmanın iki yolu vardır. Uygulamanıza, derleme içinde kaynak olarak katıştırılmış olmayan proje içerik öğeleri olarak yazı tipleri ekleyebilirsiniz. Alternatif olarak, uygulamanızın derleme dosyalarına katıştırılmış proje kaynağı öğeleri olarak uygulamanıza yazı tipleri ekleyebilirsiniz. Daha fazla bilgi için [bkz.](packaging-fonts-with-applications.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)
