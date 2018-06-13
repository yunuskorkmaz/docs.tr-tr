---
title: OpenType Yazı Tipi Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: a8ee4107ee7db20f2948ea9a33ef853815a22665
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549610"
---
# <a name="opentype-font-features"></a>OpenType Yazı Tipi Özellikleri
Bu konu önemli özelliklerinden bazıları bir bakış sunar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi teknolojisinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType yazı tipi biçimi  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı tipi biçimi uzantısıdır [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] PostScript'i yazı tipi verisi için destek ekleyen yazı tipi biçimi. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı tipi biçimi ortaklaşa tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ve Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri ve işletim sistemi hizmetleri destekleyen [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri sağlar yüklemek ve yazı tipleri kullanmak için basit bir yol kullanıcılarla yazı tipleri içeren olup olmadığını [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] anahatları veya CFF (PostScript'i) aşağıda ana hatlarıyla verilmiştir.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı tipi biçimi aşağıdaki Geliştirici sorunları giderir:  
  
-   Daha geniş birden çok platform desteği.  
  
-   Uluslararası karakter kümeleri için daha iyi destek.  
  
-   Yazı tipi veriler için daha iyi koruma.  
  
-   Yazı tipi dağıtımını daha verimli hale getirmek için daha küçük dosya boyutları.  
  
-   Gelişmiş tipografik denetim daha geniş desteği.  
  
> [!NOTE]
>  Windows SDK'sı örnek kümesini içeren [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile birlikte kullanabileceğiniz yazı tipleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu yazı tiplerini, bu konunun geri kalanında gösterilen özelliklerin çoğunu sağlar. Daha fazla bilgi için bkz: [örnek OpenType yazıtipi paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Bkz: [OpenType Belirtimi](http://go.microsoft.com/fwlink/?LinkId=96731) ilgili ayrıntılar için [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi biçimi.  
  
### <a name="advanced-typographic-extensions"></a>Gelişmiş tipografik uzantılar  
 Gelişmiş tipografik tablolar ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen tabloları) ya da yazıtipleriyle işlevselliğini genişletmek [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] veya CFF anahatları. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen yazı tipleri yüksek kaliteli uluslararası tipografi desteklemek için yazı tiplerini özelliklerini genişletir ek bilgi içerir. Çoğu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tiplerini kullanıma yalnızca bir alt toplam [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri kullanılabilir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri aşağıdaki özellikleri sağlar.  
  
-   Karakterler ve ligatürleri, konumsal formlar, alternatifler ve diğer yazı tipi değişimler destek karakter arasında zengin eşleme.  
  
-   İki boyutlu konumlandırma ve karakter eki desteği.  
  
-   Bir metin işleme uygulaması davranışını buna göre ayarlayabilirsiniz yazı tipiyle yer açık komut dosyası ve dil bilgileri.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen tabloları daha ayrıntılı olarak açıklanmıştır ["Yazı tipi dosyası tabloları"](http://www.microsoft.com/typography/otspec/otff.htm) bölümünü [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] belirtimi.  
  
 Bu genel bakışta kalanı avantajlarına ve bazı görsel ilginç esnekliğini sunar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri tarafından sunulan özellikler <xref:System.Windows.Documents.Typography> nesnesi. Bu nesne üzerinde daha fazla bilgi için bkz: [tipografi sınıfı](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Değişkenler  
 Çeşitleri, üst ve alt simgelerin gibi farklı tipografik stillerini işlemek için kullanılır.  
  
### <a name="superscripts-and-subscripts"></a>Üst ve alt simgeler  
 <xref:System.Windows.Documents.Typography.Variants%2A> Özelliği sağlar, simge ve alt simge değerlerini ayarlamak bir [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi.  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için üst indisleri görüntüler.  
  
 ![OpenType üst indisleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
OpenType üst indisleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için üst simgelerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için alt simgeler görüntüler.  
  
 ![OpenType indisleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
OpenType indisleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için alt simgeler tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Üst ve alt simgelerin dekoratif kullanımları  
 Karışık büyük metin dekoratif etkilerini oluşturmak için üst ve alt simgelerin kullanabilirsiniz. Aşağıdaki metin Palatino Linotype yazı tipi için üst ve alt simge metni görüntüler. Büyük harflerin etkilenmediğini unutmayın.  
  
 ![OpenType üst ve alt simgelerin kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
OpenType üst ve alt simgelerin kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği, üst ve alt simgelerin özelliklerini kullanarak bir yazı tipi için tanımlamak gösterilmiştir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Büyük harf  
 Büyük harfler, büyük stilde karakterlerin metinde işlemek tipografik biçimler kümesidir. Metin tüm büyük harf olarak işlendiğinde, genellikle, harfler arasındaki aralığı çok sıkı görünebilir ağırlığı ve çok yoğun harflerin doğru orantılıdır. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] büyük harfler, büyük harfler küçük dahil olmak üzere, çok küçük büyük harf, titling ve büyük harf aralığı için stil biçimlerinin destekler. Bu stil biçimleri, büyük harflerin görünümünü denetlemenize olanak tanır.  
  
 Aşağıdaki metni "SmallCaps" ve "AllSmallCaps" biçimlendirilmiş ve ardından Palatino yazı tipi için standart büyük harfleri görüntüler. Bu durumda, aynı yazı tipi boyutu tüm üç kelime için kullanılır.  
  
 ![OpenType büyük harf kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
OpenType büyük harf kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino yazı tipi için büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi. Tüm önde gelen büyük harf "SmallCaps" biçimi kullanıldığında, göz ardı edilir.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Başlık büyük harf  
 Başlık büyük harf ağırlık ve oran açık ve normal büyük harf'den fazla zarif bir görünüm kazandırmak için tasarlanmıştır. Başlık büyük harf, genellikle daha büyük yazı tipi boyutlarında başlıkları olarak kullanılır. Aşağıdaki metin Pescadero yazı tipi için normal ve başlık büyük harflerin görüntüler. İkinci satır üzerindeki metin dar stem genişliğini dikkat edin.  
  
 ![Büyük harfler ile Yazılama OpenType kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
Büyük harfler ile Yazılama OpenType kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino yazı tipi için başlık büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Büyük harf aralığı  
 Büyük harf aralığı tüm büyük harf metinde kullanırken daha fazla aralık vermenizi sağlayan bir özelliktir. Büyük harf genellikle küçük harfle karıştırmak için tasarlanmıştır. Arasında çekici görünen aralık ve tümü büyük harfle kullanıldığında bir büyük harf ve küçük harf çok sıkı görünebilir. Aşağıdaki metin Pescadero yazı tipi için normal büyük harf aralığını görüntüler.  
  
 ![OpenType büyük harf aralığı kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
OpenType büyük harf aralığı kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino yazı tipi için büyük harf aralığı tanımlamak gösterilmiştir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatürleri  
 Bitişik bir tek karakteri daha okunabilir veya çekici metin oluşturmak için oluşturulmuş iki veya daha fazla karakterlerdir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri ligatürleri dört türlerini destekler:  
  
-   **Standart ligatürleri**. Okunabilirliğini artırmak için tasarlanmıştır. Standart ligatürleri "fi", "fl" ve "ff" içerir.  
  
-   **Bağlamsal ligatürleri**. Bağ yapmak karakter arasında daha iyi birleşme davranışı sağlayarak okunabilirliği artırmak için tasarlanmıştır.  
  
-   **İsteğe bağlı ligatürleri**. Süslü ve Okunabilirlik için özellikle tasarlanmış olacak şekilde tasarlanmıştır.  
  
-   **Eski ligatürleri**. Geçmiş ve Okunabilirlik için özellikle tasarlanmış olacak şekilde tasarlanmıştır.  
  
 Aşağıdaki metin Pericles yazı tipi için standart bağ karakterlerinin görüntüler.  
  
 ![OpenType standart ligatürleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
OpenType standart ligatürleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için standart bağ karakterlerinin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Aşağıdaki metin Pericles yazı tipi için isteğe bağlı bağ karakterlerinin görüntüler.  
  
 ![OpenType isteğe bağlı ligatürleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
OpenType isteğe bağlı ligatürleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için isteğe bağlı bağ karakterlerinin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Varsayılan olarak, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tiplerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] standart ligatürleri etkinleştirin. Örneğin, Palatino Linotype yazı tipi kullanırsanız, standart ligatürleri "fi", "ff" ve "fl" birleştirilmiş karakter simgesi görünür. Her standart bağ için karakter çiftinin birbirlerine touch dikkat edin.  
  
 ![OpenType standart ligatürleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
OpenType standart ligatürleri kullanarak metin  
  
 Ancak, böylece iki ayrı karakter yerine birleşik bir karakter simgesi olarak "ff" gibi standart bir bağ görüntüler standart bağ özellikleri devre dışı bırakabilirsiniz.  
  
 ![Metin kullanılarak devre dışı OpenType standart ligatürleri](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
Devre dışı bırakılmış OpenType standart ligatürleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için standart bağ karakterlerinin devre dışı bırakmak gösterilmiştir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Dalgalı karakterler  
 Dalgalı karakterler genellikle calligraphy ile ilişkili ayrıntılı süsleme kullanan dekoratif karakterlerdir. Aşağıdaki metin Pescadero yazı tipi için standart ve süslü karakterleri görüntüler.  
  
 ![OpenType standart ve süslü karakterleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
OpenType standart ve süslü karakterleri kullanarak metin  
  
 Dalgalı karakterler genellikle olay bildirileri gibi kısa tümceleri içinde dekoratif öğeler olarak kullanılır. Aşağıdaki metin dalgalı karakterler büyük harfler olayın adı ile vurgulamak için kullanır.  
  
 ![OpenType dalgalı karakterler kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
OpenType dalgalı karakterler kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak bir yazı tipi için dalgalı karakterlerin tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Bağlamsal dalgalı karakterler  
 Süslü karakterleri belirli birleşimlerini bitişik harfler üzerinde çakışan harfin alt gibi çekici olmayan bir görünüme neden olabilir. Bağlamsal süslü kullanarak, daha iyi bir görünüm üretir yedek bir dalgalı karakter kullanmanıza olanak sağlar. Aşağıdaki metni bağlamsal süslü uygulanmadan önce ve sonra aynı sözcük gösterir.  
  
 ![OpenType bağlamsal dalgalı karakterler kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
OpenType bağlamsal dalgalı karakterler kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino yazı tipi için bağlamsal süslü tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternatifler  
 Alternatifler standart karaktere yerine karakterlerdir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri, aşağıdaki örneklerde kullanılan Pericles yazı tipi gibi metin için farklı görünümler oluşturmak için kullanabileceğiniz diğer karakterleri içerebilir. Aşağıdaki metin Pericles yazı tipi için standart karakterleri görüntüler.  
  
 ![OpenType standart karakterlerinin kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
OpenType standart karakterlerinin kullanarak metin  
  
 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi standart kümesine stil seçeneklerini sağlayan ek karakterleri içerir. Aşağıdaki metin diğer biçimsel görüntüler.  
  
 ![OpenType diğer biçimsel kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
OpenType diğer biçimsel kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için diğer biçimsel tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Aşağıdaki metni birkaç diğer diğer biçimsel Pericles yazı tipi için görüntüler.  
  
 ![OpenType diğer biçimsel kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
OpenType diğer biçimsel kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği, bu diğer diğer biçimsel tanımlamak gösterilmiştir.  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Rastgele bağlamsal alternatifler  
 Rastgele bağlamsal alternatifler tek bir karakter için birden çok yedek karakterlerin sağlar. Komut dosyası türü yazı tipleri ile uygulandığında, bu özellik rastgele Seçilen karakterlerin görünümde küçük farklılıklar olan kümesinin kullanarak el yazısı benzetimini yapabilirsiniz. Aşağıdaki metin Lindsey yazı tipi için rasgele bağlamsal alternatifler kullanır. Dikkat harf "a" harfinin görünümünün biraz  
  
 ![OpenType Rasgele bağlamsal alternatifler kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
OpenType Rasgele bağlamsal alternatifler kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Lindsey yazı tipi için rasgele bağlamsal alternatifler tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Tarihsel biçimleri  
 Tarihsel biçimleri geçmişte yaygın tipografik kurallardır. Aşağıdaki metin "Boston, Massachusetts" tümceciği görüntüler Palatino Linotype yazı tipi için geçmiş bir form karakterlerin kullanma.  
  
 ![OpenType tarihsel biçimleri kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
OpenType tarihsel biçimleri kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için geçmiş formların nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Sayısal stiller  
 OpenType yazıtipleriyle çok sayıda metin içinde sayısal değerler ile kullanılan özellikleri destekler.  
  
### <a name="fractions"></a>Kesirler  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi stillerini eğik çizgili ve Yığılmış dahil olmak üzere kesirler için destekler.  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için kesir stiller görüntüler.  
  
 ![OpenType kullanarak metin çizgili ve Yığılmış Kesir](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
OpenType kullanarak metin çizgili ve kesirler Yığılmış  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için kesir stiller tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Eski stil sayılar  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri eski stil sayısal biçimi destekler. Bu biçim, artık standart stillerde rakamları görüntülemek için yararlıdır. Aşağıdaki metin Palatino Linotype yazı tipi için standart ve eski stil sayısal biçimler 18 tarihi görüntüler.  
  
 ![OpenType eski stil sayılar kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
OpenType eski stil sayılar kullanarak metin  
  
 Aşağıdaki metni eski stil sayılar tarafından izlenen Palatino Linotype yazı tipi için standart sayıları görüntüler.  
  
 ![OpenType eski stil rakam kümelerinin kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
OpenType eski stil rakam kümelerinin kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için eski stil sayıların tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Orantılı ve sekmeli şekiller  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri rakamları kullanırken genişliklerin denetlemek için orantılı ve sekmeli şekil özelliğini destekler. Farklı bir genişliğine sahip olacak şekilde her rakamı kabul orantılı rakamları — "1" "5"'ten daha dar. Tablo rakamlarını eşit genişlikte rakamları olarak kabul edilir. böylece bunlar dikey, finansal türü bilgilerin okunabilirliğini artıran hizalayın.  
  
 Aşağıdaki metni iki orantılı rakamları Miramonte yazı tipi kullanarak ilk sütununda görüntülenir. Genişlik "5" ve "1" sayı arasındaki farkı unutmayın. İkinci sütun sekmeli şekil özelliğini kullanarak ayarlanan genişlikler ile aynı iki sayı değerini gösterir.  
  
 ![OpenType orantılı & Tablo rakamlarını kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
OpenType orantılı ve tablo rakamlarını kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Miramonte yazı tipi orantılı ve tablo rakamlarını tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Eğik çizgili sıfır  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri destekleyen bir eğik çizgili harf "O" ve "0" sayı arasındaki farkı vurgulamak için sıfır sayısal biçimi. Eğik çizgili sıfır rakamı genellikle finansal ve iş bilgilerini tanımlayıcıları için kullanılır.  
  
 Aşağıdaki metin Miramonte yazı tipi kullanarak örnek sıra tanımlayıcısını görüntüler. İlk satırı standart sayıları kullanır. Kullanılan ikinci satır eğik çizgili sıfır sayılarının büyük "O" harfle daha iyi karşıtlık sağlamak için.  
  
 ![OpenType kullanarak metin eğik çizgili sıfır sayılarının](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
Eğik çizgili sıfır sayılarının OpenType kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği nasıl tanımlanacağı gösterilmektedir eğik çizgili sıfır sayılarının özelliklerini kullanarak Miramonte yazı tipi <xref:System.Windows.Documents.Typography> nesnesi.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Tipografi sınıfı  
 <xref:System.Windows.Documents.Typography> Nesneyi kullanıma sunan özellik kümesi, bir [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi destekler. Özelliklerini ayarlayarak <xref:System.Windows.Documents.Typography> biçimlendirmesinde yararlanmak belgeleri kolayca yazabilirsiniz [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri.  
  
 Aşağıdaki metni "SmallCaps" ve "AllSmallCaps" biçimlendirilmiş ve ardından Palatino yazı tipi için standart büyük harfleri görüntüler. Bu durumda, aynı yazı tipi boyutu tüm üç kelime için kullanılır.  
  
 ![OpenType büyük harf kullanarak metin](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
OpenType büyük harf kullanarak metin  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino yazı tipi için büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesnesi. Tüm önde gelen büyük harf "SmallCaps" biçimi kullanıldığında, göz ardı edilir.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Aşağıdaki kod örneğinde, önceki biçimlendirme örneği gibi aynı görevi gerçekleştirir.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Tipografi sınıfının özellikleri  
 Aşağıdaki tabloda özelliklerini, değerleri ve varsayılan ayarlarını listeler <xref:System.Windows.Documents.Typography> nesnesi.  
  
|Özellik|Değerleri|Varsayılan Değer|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Sayısal değer - bayt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Sayısal değer - bayt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|sayısal değer – bayt|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|sayısal değer – bayt|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.Typography>  
 [OpenType Belirtimi](http://go.microsoft.com/fwlink/?LinkId=96731)  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Örnek OpenType Yazı Tipi Paketi](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)  
 [Uygulamalarla Yazı Tiplerini Paketleme](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
