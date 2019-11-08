---
title: Örnek OpenType Yazı Tipi Paketi
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: a5b49e2a1f7536fb9d8e8f4dbfc53494dcd1f1ac
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740776"
---
# <a name="sample-opentype-font-pack"></a>Örnek OpenType Yazı Tipi Paketi
Bu konu, Windows SDK dağıtılan örnek OpenType yazı tiplerine genel bir bakış sağlar. Örnek yazı tipleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar tarafından kullanılabilen genişletilmiş OpenType özelliklerini destekler.  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType yazı tipi paketindeki yazı tipleri  
 Windows SDK, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar oluşturmak için kullanabileceğiniz örnek bir OpenType yazı tipi kümesi sağlar. Örnek yazı tipleri, Ascender Corporation lisansı altında sağlanır. Bu yazı tipleri, OpenType biçimi tarafından tanımlanan toplam özelliklerin yalnızca bir alt kümesini uygular. Aşağıdaki tabloda örnek OpenType yazı tiplerinin adları listelenmektedir.  
  
|**Ad**|**Dosyasýný**|  
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
> Geliştirici olarak, bir uygulama içine eklediğiniz veya başka bir şekilde yeniden dağıtırabilmeniz gereken herhangi bir yazı tipi için gerekli lisans haklarına sahip olduğunuzdan emin olmak sizin sorumluluğunuzdadır.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Yazı tiplerini yükleme  
 Örnek OpenType yazı tiplerini varsayılan Windows Fonts dizinine ( **\Windows\fonts**) yükleme seçeneğiniz vardır. Yazı tiplerini yüklemek için yazı tipleri denetim masasını kullanın. Bu yazı tipleri bilgisayarınızda olduktan sonra, varsayılan Windows yazı tiplerine başvuran tüm uygulamalar tarafından erişilebilir. Yazı tipi dosyasına çift tıklayarak çeşitli yazı tipi boyutlarında temsili bir karakter kümesi görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde Lindsey yazı tipi dosyası, Linds. ttf gösterilmektedir.  
  
 ![Lindsey yazı &#40;tipi OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Lindsey yazı tipini görüntüleme  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Yazı tiplerini kullanma  
 Uygulamanızda yazı tiplerini kullanmanın iki yolu vardır. Uygulamanıza, derleme içinde kaynak olarak gömülü olmayan proje içerik öğeleri olarak yazı tipi ekleyebilirsiniz. Alternatif olarak, uygulamanıza, uygulamanın derleme dosyaları içine katıştırılmış proje kaynak öğeleri olarak yazı tipleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [uygulamaları Ile paketleme yazı tipleri](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType Yazı Tipi Özellikleri](opentype-font-features.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)
