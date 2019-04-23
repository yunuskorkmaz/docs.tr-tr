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
ms.openlocfilehash: 86921b610b4b42cfc0393af2966b70870bc650f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104487"
---
# <a name="opentype-font-features"></a>OpenType Yazı Tipi Özellikleri

Bu konu anahtar özelliklerinden bazılarını gösteren bir genel bakış sağlar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi teknolojisi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType yazı tipi biçimi  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı biçimi uzantısıdır [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] yazı biçimi, PostScript'i yazı tipi verileri desteği eklendi. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı biçimi ortaklaşa tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ve Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri ve işletim sistemi hangi Destek Hizmetleri [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri yazı tiplerinin içerip içermediğini yükleme ve yazı tiplerini kullanma, kullanıcıların basit bir yol sağlar [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ana hatlarının veya CFF (PostScript'i) özetlenmektedir.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Yazı biçimi aşağıdaki Geliştirici sorunlarından ele alır:  
  
-   Daha geniş bir çoklu platform desteği.  
  
-   Uluslararası karakter kümesi için daha iyi destek.  
  
-   Yazı tipi verileri için daha iyi koruma.  
  
-   Yazı tipi dağıtım daha verimli hale getirmek için daha küçük dosya boyutu.  
  
-   Gelişmiş tipografik denetim için geniş destek.  
  
> [!NOTE]
>  Windows SDK'sını içeren bir dizi örnek [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] ile kullanabileceğiniz yazı tipleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar. Bu yazı tipleri, bu konunun geri kalanında gösterilen özelliklerin çoğunu sağlar. Daha fazla bilgi için [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).  
  
 Bkz: [OpenType Belirtimi](https://go.microsoft.com/fwlink/?LinkId=96731) hakkında ayrıntılar için [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı biçimi.  
  
### <a name="advanced-typographic-extensions"></a>Gelişmiş tipografik uzantıları  
 Gelişmiş tipografik tablolar ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen tabloları) ile yazı tiplerinin genişletmek [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] veya CFF özetlenmektedir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen yazı tipleri, yüksek kaliteli uluslararası tipografi desteklemek için yazı tiplerini yeteneklerini genişletir ek bilgiler içermektedir. Çoğu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri kullanıma yalnızca bir alt toplam [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri kullanılabilir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri aşağıdaki özellikleri sağlar.  
  
-   Karakter bitişik, konumsal forms, diğerleri ve diğer yazı tipi değişimler destekleyen karakterleri arasında zengin eşleme.  
  
-   İki boyutlu konumlandırma ve karakter eki için destek.  
  
-   Bir metin işleme uygulama davranışını uygun şekilde ayarlayabilmeniz için yazı tipinde bulunan açık betik ve dil bilgileri.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Düzen tabloları daha ayrıntılı olarak açıklanmıştır ["Yazı tipi dosyası tabloları"](https://www.microsoft.com/typography/otspec/otff.htm) bölümünü [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] belirtimi.  
  
 Bu genel bakışta geri kalanında avantajlarına ve görsel olarak çekici bazıları esnekliğini sunar [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri tarafından kullanıma sunulan özellikler <xref:System.Windows.Documents.Typography> nesne. Bu nesne üzerinde daha fazla bilgi için bkz. [tipografi sınıfı](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Değişkenler  
 Çeşitleri, üst ve alt simgelerin gibi farklı tipografik stilleri işlemek için kullanılır.  
  
### <a name="superscripts-and-subscripts"></a>Üst ve alt simgeler  
 <xref:System.Windows.Documents.Typography.Variants%2A> Özelliği sayesinde üst ve alt simge değerlerini ayarlamak bir [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi.  
  
 Aşağıdaki metni indisleri Palatino Linotype yazı tipi için görüntüler.  
  
 ![OpenType indisleri kullanarak metin](./media/opentype-font-features/opentype-superscripts.gif "OpenType indisleri kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için üst simgelerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Aşağıdaki metni Palatino Linotype yazı tipi için alt simge görüntüler.  
  
 ![OpenType alt simgeler kullanarak metin](./media/opentype-font-features/opentype-subscripts.gif "OpenType alt simgeler kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi alt simgelerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Üst ve alt simgelerin dekoratif kullanımları  
 Karma durum metin dekoratif etkilerini oluşturmak için üst ve alt simgelerin kullanabilirsiniz. Aşağıdaki metni Palatino Linotype yazı tipi için üst ve alt simge metni görüntüler. Büyük harflerin etkilenmez unutmayın.  
  
 ![OpenType üst ve alt simgelerin kullanarak metin](./media/opentype-font-features/opentype-superscripts-subscripts.gif "OpenType üst ve alt simgelerin kullanarak metin")  

 Aşağıdaki biçimlendirme örneği, üst ve alt özelliklerini kullanarak bir yazı tipi için simgelerin tanımlamak gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Büyük harf  
 Büyük harf karakterler büyük biçimlendirilmiş metin işleme tipografi forms kümesidir. Metin tümü büyük harf işlendiğinde, genellikle harfler aralığını çok sıkı görünebilir ağırlığı ve çok ağır harf oranı. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Stil biçimleri sayısı, büyük harfler, küçük harf dahil, çok küçük büyük harf bir büyük harf, stillendirme biçimini ve büyük harf aralığı destekler. Bu stil biçimleri, büyük harflerin görünümünü denetlemenize olanak tanır.  
  
 Standart büyük harf "SmallCaps" ve "AllSmallCaps" biçimlendirilmiş ardından Palatino yazı tipi için aşağıdaki metni görüntüler. Bu durumda, aynı yazı tipi boyutunu her üç sözcük için kullanılır.  
  
 ![OpenType başkentleri kullanarak metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerin kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pescadero yazı tipi için büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne. Tüm önde gelen bir büyük harf "SmallCaps" biçim kullanıldığında, göz ardı edilir.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Devrik  
 Başlık büyük harf ağırlık ve oranı, daha açık ve normal bir büyük harf değerinden daha zarif bir görünüm kazandırmak için tasarlanmıştır. Başlık büyük harf, genellikle daha büyük yazı tipi boyutlarını içinde başlığı olarak kullanılır. Aşağıdaki metni Palatino yazı tipi için normal ve başlık büyük harflerin görüntüler. İkinci satırdaki metin dar fetemm genişliğini dikkat edin.  
  
 ![Devrik OpenType kullanarak metin](./media/opentype-font-features/opentype-titling-capitals.gif "devrik OpenType kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pescadero yazı tipi için başlık büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Büyük harf aralığı  
 Büyük harf aralığı tüm harfleri büyük metin kullanırken daha fazla boşluk vermenizi sağlayan bir özelliktir. Büyük harf, küçük harfler ile karıştırmak için genellikle tasarlanmıştır. Çekici arasında görünen aralık ve tümü büyük harf olarak kullanıldığında, bir büyük harf ve küçük harf çok sıkı görünebilir. Aşağıdaki metni Palatino yazı tipi için normal ve sermaye aralığı görüntüler.  
  
 ![OpenType büyük harf aralığı kullanarak metin](./media/opentype-font-features/opentype-capital-spacing.gif "OpenType büyük harf aralığı kullanarak metin ")  
 
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pescadero yazı tipi için sermaye aralığını tanımlamak gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Bitişik  
 Bitişik daha okunabilir veya dikkat çekici metin oluşturmak için tek bir karakter ile oluşturulmuş iki veya daha fazla karakter var. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri bitişik dört türlerini destekler:  
  
-   **Standart Bitişik**. Okunabilirliği artırmak için tasarlanmıştır. Standart bitişik "fi", "fl" ve "ff" ekleyin.  
  
-   **Bağlamsal bitişik**. Bağ olun karakter arasında daha iyi birleşme davranışı sağlayarak okunabilirliği artırmak için tasarlanmıştır.  
  
-   **İsteğe bağlı bitişik**. Süslü ve Okunabilirlik için özel olarak tasarlanmış olacak şekilde tasarlanmıştır.  
  
-   **Geçmiş bitişik**. Geçmiş ve Okunabilirlik için özel olarak tasarlanmış olacak şekilde tasarlanmıştır.  
  
 Aşağıdaki metni Pericles yazı tipi için standart bağ karakterlerinin görüntüler.  
  
 ![OpenType standart bitişik kullanarak metin](./media/opentype-font-features/opentype-standard-ligatures.gif "OpenType standart bitişik kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için standart bağ karakterlerinin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 İsteğe bağı karakterleri Pericles yazı tipi için aşağıdaki metni görüntüler.  
  
 ![OpenType isteğe bağlı bitişik kullanarak metin](./media/opentype-font-features/opentype-discretionary-ligatures.gif "OpenType isteğe bağlı bitişik kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için isteğe bağlı bir bağ karakterlerinin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Varsayılan olarak, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tiplerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] standart bitişik etkinleştirin. Örneğin, Palatino Linotype yazı tipi kullanırsanız, standart bitişik "fi", "ff" ve "fl" birleştirilmiş karakter simgesi görünür. Her standart bağ karakterleri çifti birbirine touch dikkat edin.  
  
 ![OpenType standart bitişik Palatino Linotype ile kullanarak metin](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "OpenType standart bitişik Palatino Linotype ile kullanarak metin")    
   
 Ancak, standart bir bağ "ff" gibi iki ayrı karakter yerine birleşik bir karakter simgesi olarak görüntülenmesini standart bağ özellikleri devre dışı bırakabilirsiniz.  
  
 ![Metin kullanılarak devre dışı OpenType standart bitişik](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "devre dışı OpenType standart bitişik metin kullanma")  
    
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için standart bağ karakterlerinin devre dışı bırakma gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Süsler  
 Süsler genellikle calligraphy ile ilişkili ayrıntılı süsleme kullanan dekoratif karakterlerdir. Standart ve dalgalı karakterleri Palatino yazı tipi için aşağıdaki metni görüntüler.  
  
 ![OpenType standart ve swash karakterleri kullanarak metin](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "OpenType standart ve swash karakterleri kullanarak metin")  

 Süsler genellikle olay duyuruları gibi kısa deyimlerin dekoratif öğeleri olarak kullanılır. Aşağıdaki metni süsler olay adının büyük harf vurgulamak için kullanır.  
  
 ![OpenType süsler kullanarak metin](./media/opentype-font-features/opentype-swashes.gif "OpenType süsler kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak bir yazı tipi için süsler tanımlamak gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Bağlamsal süsler  
 Süslü karakterleri belirli birleşimlerini gibi bitişik harfler üzerinde örtüşen çıkıntılarını çekici olmayan bir görünüme neden olabilir. Bir bağlamsal swash kullanarak daha iyi bir görünüm oluşturan bir yedek swash glif kullanmanıza olanak tanır. Aşağıdaki metni bağlamsal swash uygulanmadan önce ve sonra aynı sözcük gösterir.  
  
 ![OpenType bağlamsal süsler kullanarak metin](./media/opentype-font-features/opentype-contextual-swashes.gif "OpenType bağlamsal süsler kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pescadero yazı tipi için bağlamsal bir swash tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternatifler  
 Alternatifleri için standart bir karakter yerine kullanılabileceği karakterlerdir. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri, aşağıdaki örneklerde kullanılan Pericles yazı tipi gibi metin için farklı görünümler oluşturmak için kullanabileceğiniz diğer karakterleri içerebilir. Standart karakterleri Pericles yazı tipi için aşağıdaki metni görüntüler.  
  
 ![OpenType standart karakterleri kullanarak metin](./media/opentype-font-features/opentype-standard-glyphs.gif "OpenType standart karakterleri kullanarak metin")  

 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi standart karakter kümesini biçimsel alternatifler sağlayan ek karakterleri içerir. Aşağıdaki metni diğer biçimsel görüntüler.  
  
 ![OpenType diğer biçimsel kullanarak metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "OpenType diğer biçimsel kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pericles yazı tipi için diğer biçimsel tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Aşağıdaki metni birkaç diğer alternatif Pericles yazı tipi için biçimsel görüntüler.  
  
 ![OpenType diğer biçimsel Pericles yazı tipini kullanarak metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "OpenType diğer biçimsel Pericles yazı tipini kullanarak metin")

 Aşağıdaki biçimlendirme örneği, bu diğer diğer biçimsel tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Rastgele bağlamsal alternatifler  
 Rastgele bağlamsal alternatifler birden çok yedek karakterler için tek bir karakter sağlar. Betik türü yazı tipleri ile uygulandığında, bu özellik bir görünümde küçük farklılıklar ile rastgele seçilen karakter kümesini kullanarak el yazısı benzetimini yapabilirsiniz. Aşağıdaki metni rastgele bağlamsal alternatifler Lindsey yazı tipi için kullanır. Dikkat harf "a" değişir biraz görünümü  
  
 ![OpenType rastgele bağlamsal alternatifler kullanarak metin](./media/opentype-font-features/opentype-random-contextual-alternates.gif "OpenType rastgele bağlamsal alternatifler kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Lindsey yazı tipi için rastgele bağlamsal alternatifleri tanımlamak gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Tarihsel biçimleri  
 Tarihsel biçimleri geçmişte ortak tipografik kurallardır. Aşağıdaki metni "Boston, Massachusetts" ifadesini görüntüler karakterleri geçmiş bir tür Palatino Linotype yazı tipini kullanarak.  
  
 ![OpenType tarihsel biçimleri kullanarak metin](./media/opentype-font-features/opentype-historical-forms.gif "OpenType tarihsel biçimleri kullanarak metin")  
   
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için geçmiş formların nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Sayısal stilleri  
 OpenType yazı tipi çok sayıda metin sayısal değerler ile kullanılabilen özellikleri destekler.  
  
### <a name="fractions"></a>Kesir  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi stillerini eğik çizgili ve Yığılmış gibi dakikalarının bölümü destekler.  
  
 Aşağıdaki metni kesir Palatino Linotype yazı tipi stilleri görüntüler.  
  
 ![OpenType kullanarak metin eğik çizgili ve Yığılmış kesirler](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "OpenType kullanarak metin eğik çizgili ve Yığılmış faturalandırılmayacak")  
   
 Aşağıdaki biçimlendirme örneği kesir özelliklerini kullanarak Palatino Linotype yazı tipi stillerini tanımlamak gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Eski stil sayılar  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi stili için eski bir sayısal biçimi destekler. Bu biçim, sayısal değerler artık standart stillerde görüntülemek için yararlıdır. Aşağıdaki metni Palatino Linotype yazı tipi için standart ve eski stil sayısal biçimler 18. yüzyıla uygun bir tarih görüntüler.  
  
 ![OpenType eski stil sayılar kullanarak metin](./media/opentype-font-features/opentype-old-style-numerals.gif "OpenType eski stil sayılar kullanarak metin")  
    
 Eski stil sayılar tarafından izlenen Palatino Linotype yazı tipi için standart sayılar aşağıdaki metni görüntüler.  
  
 ![OpenType eski stil sayısal kümelerinin kullanarak metin](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "OpenType eski stil sayısal kümelerinin kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Palatino Linotype yazı tipi için eski stil sayıların nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Orantılı ve tablo rakamlarını  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipleri genişliklerin sayılar kullanırken denetlemek için bir orantılı ve tablo şekil özelliğini destekler. Orantılı rakamları her sayısal farklı genişliği sahip olacak şekilde davranma: "1" dar "5'ten". Böylece bunlar dikey, finansal tür bilgileri okunabilirliğini artırır Hizala tablo rakamlarını eşit genişlik sayılar olarak kabul edilir.  
  
 Aşağıdaki metni iki orantılı rakamları Miramonte yazı tipini kullanarak ilk sütunda görüntüler. Width "5" ve "1" sayı arasındaki farkı unutmayın. İkinci sütun, tablo şekil özelliğini kullanarak ayarlanan genişlikler ile aynı olan iki sayı değerini gösterir.  
  
 ![OpenType orantılı & Tablo rakamlarını kullanarak metin](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "OpenType orantılı ve tablo rakamlarını kullanarak metin")  
    
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Miramonte yazı tipi orantılı ve tablo rakamlarını tanımlanacağı gösterilmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Eğik çizgili sıfır  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi desteği eğik çizgili harfi "O" ve "0" sayı arasındaki farkı vurgulamak için sıfır sayısal biçimi. Eğik çizgili sıfır sayı genellikle finansal ve işletme bilgileri tanımlayıcıları için kullanılır.  
  
 Aşağıdaki metni Miramonte yazı tipini kullanarak örnek bir siparişi tanımlayıcısı görüntüler. İlk satırı standart sayıları kullanır. Kullanılan ikinci satır eğik çizgili büyük harf "O" harfi ile daha iyi karşıtlık sağlamak için sıfır sayı.  
  
 ![OpenType kullanarak metin sıfır sayı eğik çizgili](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "OpenType kullanarak metin sıfır sayı eğik çizgili")  
    
 Aşağıdaki biçimlendirme örneği nasıl tanımlanacağını gösterir eğik çizgili özelliklerini kullanarak Miramonte yazı tipi sıfır sayılarının <xref:System.Windows.Documents.Typography> nesne.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Tipografi sınıfı  
 <xref:System.Windows.Documents.Typography> Nesne özellikler sunan, bir [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi destekler. Özelliklerini ayarlayarak <xref:System.Windows.Documents.Typography> biçimlendirme içinde kolayca yararlanan belgeleri yazabilirsiniz [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] özellikleri.  
  
 Standart büyük harf "SmallCaps" ve "AllSmallCaps" biçimlendirilmiş ardından Palatino yazı tipi için aşağıdaki metni görüntüler. Bu durumda, aynı yazı tipi boyutunu her üç sözcük için kullanılır.  
  
 ![OpenType başkentleri kullanarak metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerin kullanarak metin")  
    
 Aşağıdaki biçimlendirme örneği özelliklerini kullanarak Pescadero yazı tipi için büyük harflerin nasıl tanımlanacağını gösterir <xref:System.Windows.Documents.Typography> nesne. Tüm önde gelen bir büyük harf "SmallCaps" biçim kullanıldığında, göz ardı edilir.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Aşağıdaki kod örneği, önceki biçimlendirme örnek aynı görevi gerçekleştirir.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Tipografi sınıfı özellikleri  
 Özellikler, değerleri ve varsayılan ayarları aşağıdaki tabloda listelenmektedir <xref:System.Windows.Documents.Typography> nesne.  
  
|Özellik|Değerler|Varsayılan Değer|  
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
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Sayısal değer – bayt|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Sayısal değer – bayt|0|  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType Belirtimi](https://go.microsoft.com/fwlink/?LinkId=96731)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Örnek OpenType Yazı Tipi Paketi](sample-opentype-font-pack.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)