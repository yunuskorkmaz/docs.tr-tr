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
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186813"
---
# <a name="opentype-font-features"></a>OpenType Yazı Tipi Özellikleri

Bu konu, OpenType yazı tipi teknolojisinin bazı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]temel özelliklerine genel bir bakış sağlar.  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>OpenType Font Formatı  
 OpenType yazı tipi biçimi, TrueType® yazı tipi biçiminin bir uzantısıdır ve PostScript yazı tipi verileri için destek ekler. OpenType yazı tipi biçimi Microsoft ve Adobe Corporation tarafından ortaklaşa geliştirilmiştir. OpenType yazı tipleri ve OpenType yazı tiplerini destekleyen işletim sistemi hizmetleri, yazı tipleri TrueType anahatlarını veya CFF (PostScript) anahatlarını içersin, kullanıcılara yazı tiplerini yüklemek ve kullanmak için basit bir yol sağlar.  
  
 OpenType yazı tipi biçimi aşağıdaki geliştirici zorluklarını giderer:  
  
- Daha geniş çoklu platform desteği.  
  
- Uluslararası karakter setleri için daha iyi destek.  
  
- Yazı tipi verileri için daha iyi koruma.  
  
- Yazı tipi dağıtımın daha verimli olmasını sağlamak için daha küçük dosya boyutları.  
  
- Gelişmiş tipografik kontrol için daha geniş destek.  
  
> [!NOTE]
> Windows SDK, uygulamalarla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] birlikte kullanabileceğiniz bir dizi örnek OpenType yazı tipi içerir. Bu yazı tipleri, bu konunun geri kalanında gösterilen özelliklerin çoğunu sağlar. Daha fazla bilgi için [Örnek OpenType Yazı Tipi Paketi'ne](sample-opentype-font-pack.md)bakın.  
  
OpenType yazı tipi biçiminin ayrıntıları için [OpenType belirtimine](https://docs.microsoft.com/typography/opentype/spec/)bakın.  
  
### <a name="advanced-typographic-extensions"></a>Gelişmiş Tipografik Uzantılar  
 Gelişmiş Tipografik tablolar (OpenType Düzen tabloları), TrueType veya CFF anahatlarına sahip yazı tiplerinin işlevselliğini genişletir. OpenType Düzen yazı tipleri, yüksek kaliteli uluslararası tipografiyi desteklemek için yazı tiplerinin özelliklerini genişleten ek bilgiler içerir. Çoğu OpenType yazı tipi, kullanılabilir toplam OpenType özelliklerinin yalnızca bir alt kümesini ortaya çıkarır. OpenType yazı tipleri aşağıdaki özellikleri sağlar.  
  
- Bağlar, konumsal formlar, alternatifler ve diğer yazı tipi değiştirmelerini destekleyen karakterler ve glifler arasında zengin eşleme.  
  
- İki boyutlu konumlandırma ve gliflere ek desteği.  
  
- Metin işleme uygulamasının davranışını buna göre ayarlayabilmesi için yazı tipinde bulunan açık komut dosyası ve dil bilgileri.  
  
 OpenType Düzen tabloları, OpenType belirtiminin ["Font Dosya Tabloları"](https://www.microsoft.com/typography/otspec/otff.htm) bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Bu genel bakışın geri kalanı, nesnenin özellikleri tarafından ortaya çıkarılan görsel olarak ilginç OpenType <xref:System.Windows.Documents.Typography> özelliklerinin bazılarının genişliğini ve esnekliğini sunar. Bu nesne hakkında daha fazla bilgi için [Tipografi Sınıfı'na](#typography_class)bakın.  
  
<a name="variants"></a>
## <a name="variants"></a>Değişkenler  
 Varyantlar, üst yazılar ve alt yazılar gibi farklı tipografik stilleri işlemek için kullanılır.  
  
### <a name="superscripts-and-subscripts"></a>Üst Yazılar ve Alt Yazılar  
 Özellik, <xref:System.Windows.Documents.Typography.Variants%2A> OpenType yazı tipi için üst yazı ve alt yazı değerleri ayarlamanızı sağlar.  
  
 Aşağıdaki metin, Palatino Linotype yazı tipi için üst yazılar görüntüler.  
  
 ![OpenType üst yazılarını kullanan metin](./media/opentype-font-features/opentype-superscripts.gif "OpenType üst yazılarını kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Palatino Linotype yazı tipi için üst yazı nasıl tanımlanacak gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Aşağıdaki metin, Palatino Linotype yazı tipi için alt yazılar görüntüler.  
  
 ![OpenType alt yazılarını kullanarak metin](./media/opentype-font-features/opentype-subscripts.gif "OpenType alt yazılarını kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Palatino Linotype yazı tipi için alt yazı nasıl tanımlanacak gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Superscripts ve Subscripts Dekoratif Kullanımları  
 Karma durum metninin dekoratif efektlerini oluşturmak için üst yazılar ve alt yazılar da kullanabilirsiniz. Aşağıdaki metin, Palatino Linotype yazı tipi için üst yazı ve alt metin görüntüler. Büyük harflerin etkilenmediğini unutmayın.  
  
 ![OpenType üst yazılarını ve alt yazılarını kullanan metin](./media/opentype-font-features/opentype-superscripts-subscripts.gif "OpenType üst yazılarını ve alt yazılarını kullanan metin")  

 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak bir yazı tipi için üst yazı yazı larının ve alt yazı yazı larının nasıl tanımlanacak olduğunu gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>Başkentler  
 Büyük harfler, metni büyük harf stilinde işleyen tipografik formlar kümesidir. Genellikle, metin tüm büyük harfler olarak işlendiğinde, harfler arasındaki boşluk çok sıkı görünebilir ve harflerin ağırlığı ve oranı çok ağır dır. OpenType, küçük büyük harfler, minyon büyük harfler, titling ve büyük harf aralıkları da dahil olmak üzere büyük harfler için bir dizi stil biçimini destekler. Bu stil biçimleri büyük harflerin görünümünü denetlemenize olanak sağlar.  
  
 Aşağıdaki metinpescadero yazı tipi için standart büyük harfleri görüntüler, ardından "SmallCaps" ve "AllSmallCaps" harfleri bulunur. Bu durumda, her üç sözcük için de aynı yazı tipi boyutu kullanılır.  
  
 ![OpenType büyük harflerini kullanan metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerini kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Pescadero yazı tipi için büyük harflerin nasıl tanımlandığını gösterir. "SmallCaps" biçimi kullanıldığında, herhangi bir satır baş harfi yoksayılır.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Titling Başkentleri  
 Titling başkentleri ağırlık ve oran daha hafif ve normal başkentleri daha şık bir görünüm vermek için tasarlanmıştır. Titling büyük harfleri genellikle başlık olarak daha büyük yazı tipi boyutlarında kullanılır. Aşağıdaki metin Pescadero yazı tipi için normal ve titling büyük harfleri görüntüler. İkinci satırdaki metnin dar kök genişliklerine dikkat edin.  
  
 ![OpenType titling büyük harflerini kullanan metin](./media/opentype-font-features/opentype-titling-capitals.gif "OpenType titling büyük harflerini kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak Pescadero yazı tipi için titling büyük harflerinin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Sermaye Aralığı  
 Büyük harf aralığı, metindeki tüm büyük harfleri kullanırken daha fazla boşluk sağlamanızı sağlayan bir özelliktir. Büyük harfler genellikle küçük harflerle karıştırılacak şekilde tasarlanmıştır. Büyük harf ile büyük harf arasında çekici görünen aralıklar ve küçük harf, tüm büyük harfler kullanıldığında çok sıkı görünebilir. Aşağıdaki metin Pescadero yazı tipi için normal ve büyük aralıkgörüntüler.  
  
 ![OpenType büyük aralığını kullanan metin](./media/opentype-font-features/opentype-capital-spacing.gif "OpenType büyük aralığını kullanan metin")  

 Aşağıdaki biçimlendirme örneği, nesnenin özelliklerini kullanarak Pescadero yazı tipi için <xref:System.Windows.Documents.Typography> büyük harf aralığının nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>Bağlar  
 Ligatürler, daha okunabilir veya çekici bir metin oluşturmak için tek bir glifler halinde oluşturulan iki veya daha fazla gliflerdir. OpenType yazı tipleri dört tür bağyı destekler:  
  
- **Standart bağlar.** Okunabilirliği artırmak için tasarlanmıştır. Standart bağlar "fi", "fl" ve "ff" içerir.  
  
- **Bağlamsal bağlar.** Bağyı oluşturan karakterler arasında daha iyi birleştirme davranışı sağlayarak okunabilirliği artırmak için tasarlanmıştır.  
  
- **İhtiyari bağlar.** Süs amaçlı olarak tasarlanmıştır ve okunabilirlik için özel olarak tasarlanmaz.  
  
- **Tarihsel bağlar**. Tarihsel olarak tasarlanmış ve okunabilirlik için özel olarak tasarlanmamış.  
  
 Aşağıdaki metin, Perikles yazı tipi için standart bağ glifleri görüntüler.  
  
 ![OpenType standart bağlarını kullanan metin](./media/opentype-font-features/opentype-standard-ligatures.gif "OpenType standart bağlarını kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak Perikles yazı tipi için standart bağ gliflerinin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Aşağıdaki metin, Perikles yazı tipi için isteğe bağlı ligatür glifleri görüntüler.  
  
 ![OpenType isteğe bağlı bağlarını kullanan metin](./media/opentype-font-features/opentype-discretionary-ligatures.gif "OpenType isteğe bağlı bağlarını kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak Perikles yazı tipi için isteğe bağlı bağ gliflerinin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Varsayılan olarak, OpenType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tipleri standart bağları etkinleştirin. Örneğin, Palatino Linotype yazı tipini kullanırsanız, standart "fi", "ff" ve "fl" bağları birleşik karakter glyph'si olarak görünür. Her standart ligatür için karakter çiftinin birbirine dokunduğuna dikkat edin.  
  
 ![Palatino Linotype ile OpenType standart ligatürler kullanarak metin](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Palatino Linotype ile OpenType standart ligatürler kullanarak metin")

 Ancak, standart ligatür özelliklerini devre dışı kullanabilirsiniz, böylece "ff" gibi standart bir bağ, birleşik bir karakter glifleri yerine iki ayrı glifler olarak görüntülenir.  
  
 ![Devre dışı bırakılmış OpenType standart bağlarını kullanan metin](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Devre dışı bırakılmış OpenType standart bağlarını kullanan metin")  

 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak Palatino Linotype yazı tipi için standart ligature gliflerin nasıl devre dışı kaltılsüreceğini gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>Süsler  
 Swashes genellikle kaligrafi ile ilişkili ayrıntılı süsleme kullanan dekoratif glifler vardır. Aşağıdaki metin Pescadero yazı tipi için standart ve swash glifleri görüntüler.  
  
 ![OpenType standardı ve swash glifleri kullanan metin](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "OpenType standardı ve swash glifleri kullanan metin")  

 Swashes genellikle olay duyuruları gibi kısa ifadeler dekoratif unsurlar olarak kullanılır. Aşağıdaki metin, olayın adının büyük harflerini vurgulamak için swashes kullanır.  
  
 ![OpenType swashes kullanarak metin](./media/opentype-font-features/opentype-swashes.gif "OpenType swashes kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak bir yazı tipi için swashes nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Bağlamsal Swashes  
 Swash gliflerin bazı kombinasyonları, bitişik harflerdeki üst üste binen soyundan lar gibi itici bir görünüme neden olabilir. Bağlamsal bir swash kullanarak daha iyi bir görünüm üreten bir yedek swash glyph kullanmanıza olanak sağlar. Aşağıdaki metin, bağlamsal bir swash uygulanmadan önce ve sonra aynı sözcüğü gösterir.  
  
 ![OpenType bağlamsal swashes kullanarak metin](./media/opentype-font-features/opentype-contextual-swashes.gif "OpenType bağlamsal swashes kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin özelliklerini kullanarak Pescadero yazı tipi için bağlamsal bir swash'ın nasıl tanımlanabildiğini <xref:System.Windows.Documents.Typography> gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>Diğerleri  
 Alternatifler standart bir gliflerin yerine geçebilen gliflerdir. Aşağıdaki örneklerde kullanılan Perikles yazı tipi gibi OpenType yazı tipleri, metin için farklı görünümler oluşturmak için kullanabileceğiniz alternatif glifler içerebilir. Aşağıdaki metin, Perikles yazı tipi için standart glifleri görüntüler.  
  
 ![OpenType standart glifleri kullanan metin](./media/opentype-font-features/opentype-standard-glyphs.gif "OpenType standart glifleri kullanan metin")  

 Pericles OpenType yazı tipi, standart glifler kümesine stil alternatifleri sağlayan ek glifler içerir. Aşağıdaki metin de stilistik alternatif glifleri görüntüler.  
  
 ![OpenType stilistik alternatif glifleri kullanarak metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "OpenType stilistik alternatif glifleri kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Perikles yazı tipi için stil alternatif gliflerin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Aşağıdaki metin, Perikles yazı tipi için diğer birkaç stilistik alternatif glifleri görüntüler.  
  
 ![Perikles yazı tipi için OpenType stilistik alternatif glifleri kullanan metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Perikles yazı tipi için OpenType stilistik alternatif glifleri kullanan metin")

 Aşağıdaki biçimlendirme örneği, bu diğer stilistik alternatif gliflerin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Rastgele Bağlamsal Alternatifler  
 Rasgele bağlamsal alternatifler, tek bir karakter için birden çok yedek glifler sağlar. Komut dosyası türü yazı tipleri ile uygulandığında, bu özellik görünüm küçük farklılıklar ile rasgele seçilmiş glifler bir dizi kullanarak el yazısı simüle edebilirsiniz. Aşağıdaki metin, Lindsey yazı tipi için rasgele bağlamsal alternatifler kullanır. "a" harfinin görünüm olarak biraz değiştiğine dikkat edin  
  
 ![OpenType rasgele bağlamsal alternatiflerini kullanarak metin](./media/opentype-font-features/opentype-random-contextual-alternates.gif "OpenType rasgele bağlamsal alternatiflerini kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, nesnenin <xref:System.Windows.Documents.Typography> özelliklerini kullanarak Lindsey yazı tipi için rasgele bağlamsal alternatiflerin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Tarihsel Formlar  
 Tarihsel formlar geçmişte yaygın olan tipografik sözleşmelerdir. Aşağıdaki metin, Palatino Linotype yazı tipi için gliflerin tarihsel bir biçimini kullanarak "Boston, Massachusetts" ifadesini görüntüler.  
  
 ![OpenType geçmiş formlarını kullanan metin](./media/opentype-font-features/opentype-historical-forms.gif "OpenType geçmiş formlarını kullanan metin")  

 Aşağıdaki biçimlendirme örneği, nesnenin özelliklerini kullanarak Palatino Linotype yazı <xref:System.Windows.Documents.Typography> tipi için geçmiş formların nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>Sayısal Stiller  
 OpenType yazı tipleri metindeki sayısal değerlerle kullanılabilecek çok sayıda özelliği destekler.  
  
### <a name="fractions"></a>Kesir  
 OpenType yazı tipleri, kesilmiş ve yığılmış kesirler için stilleri destekler.  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için kesir stilleri görüntüler.  
  
 ![OpenType'ı kullanarak kesilmiş ve yığılmış kesirleri kullanan metin](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "OpenType'ı kullanarak kesilmiş ve yığılmış kesirleri kullanan metin")  

 Aşağıdaki biçimlendirme örneği, nesnenin özelliklerini kullanarak Palatino Linotype yazı <xref:System.Windows.Documents.Typography> tipi için kesir stillerinin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Eski Stil Rakamları  
 OpenType yazı tipleri eski stil sayı biçimini destekler. Bu biçim, artık standart olmayan stillerdeki rakamları görüntülemek için yararlıdır. Aşağıdaki metin, Palatino Linotype yazı tipi için standart ve eski stil sayı biçimlerinde 18.  
  
 ![OpenType eski stil sayılarını kullanan metin](./media/opentype-font-features/opentype-old-style-numerals.gif "OpenType eski stil sayılarını kullanan metin")  

 Aşağıdaki metin, Palatino Linotype yazı tipi için standart rakamları görüntüler ve ardından eski stil rakamları görüntülenir.  
  
 ![OpenType eski stil sayı kümelerini kullanarak metin](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "OpenType eski stil sayı kümelerini kullanarak metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Palatino Linotype yazı tipi için eski stil rakamlarının nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Orantılı ve Tabular Rakamlar  
 OpenType yazı tipleri, sayılar kullanırken genişliklerin hizalanmasını denetlemek için orantılı ve tabular şekil özelliğini destekler. Orantılı rakamlar her sayıyı farklı bir genişliğe sahip olarak ele alır—"1" "5"den daha dardır. Tabular rakamlar, dikey olarak hizalanabilmeleri için eşit genişlikteki sayılar olarak kabul edilir ve bu da finansal tür bilgilerinin okunabilirliğini artırır.  
  
 Aşağıdaki metin, Miramonte yazı tipini kullanarak ilk sütunda iki orantılı şekil görüntüler. "5" ve "1" rakamları arasındaki genişlik farkı dikkate abak. İkinci sütun, tabular şekil özelliği kullanılarak ayarlanan genişlikleri ile aynı iki sayısal değerleri gösterir.  
  
 ![OpenType orantılı & tabular rakamlar kullanarak metin](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "OpenType orantılı ve tabular rakamlar kullanarak metin")  

 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Miramonte yazı tipi için orantılı ve tabular şekillerin nasıl tanımlandığını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Kesilen Sıfır  
 OpenType yazı tipleri, "O" harfi ile "0" rakamı arasındaki farkı vurgulamak için kesilmiş sıfır rakamı biçimini destekler. Kesilen sıfır rakamı genellikle finansal ve iş bilgilerindeki tanımlayıcılar için kullanılır.  
  
 Aşağıdaki metin, Miramonte yazı tipini kullanarak örnek bir sipariş tanımlayıcısı görüntüler. İlk satır standart sayılar kullanır. İkinci satır, büyük harf "O" harfi ile daha iyi kontrast sağlamak için kesilen sıfır rakamları kullandı.  
  
 ![OpenType kullanarak metin sıfır rakamları kesilmiş](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "OpenType kullanarak metin sıfır rakamları kesilmiş")  

 Aşağıdaki biçimlendirme örneği, nesnenin özelliklerini kullanarak Miramonte yazı tipi için kesilen <xref:System.Windows.Documents.Typography> sıfır rakamlarının nasıl tanımlanış yapılacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>Tipografi Sınıfı  
 Nesne, <xref:System.Windows.Documents.Typography> OpenType yazı tipinin desteklediği özellikler kümesini ortaya çıkarır. Biçimlendirmedeki özellikleri <xref:System.Windows.Documents.Typography> ayarlayarak, OpenType özelliklerinden yararlanan belgeleri kolayca yazabilirsiniz.  
  
 Aşağıdaki metinpescadero yazı tipi için standart büyük harfleri görüntüler, ardından "SmallCaps" ve "AllSmallCaps" harfleri bulunur. Bu durumda, her üç sözcük için de aynı yazı tipi boyutu kullanılır.  
  
 ![OpenType büyük harflerini kullanan metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerini kullanan metin")  

 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnenin özelliklerini kullanarak Pescadero yazı tipi için büyük harflerin nasıl tanımlandığını gösterir. "SmallCaps" biçimi kullanıldığında, herhangi bir satır baş harfi yoksayılır.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Aşağıdaki kod örneği önceki biçimlendirme örneğiyle aynı görevi gerçekleştirir.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Tipografi Sınıfı Özellikleri  
 Aşağıdaki tabloda <xref:System.Windows.Documents.Typography> nesnenin özellikleri, değerleri ve varsayılan ayarları listelenir.  
  
|Özellik|Değer(ler)|Varsayılan Değer|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Sayısal değer - bayt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps>&#124; <xref:System.Windows.FontCapitals.AllSmallCaps> <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; &#124; &#124; &#124;<xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Sayısal değer - bayt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji>&#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal>&#124; <xref:System.Windows.FontFraction.Slashed> &#124;<xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal>&#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124;<xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> <xref:System.Windows.FontVariants.Subscript> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType belirtimi](https://docs.microsoft.com/typography/opentype/spec/)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Örnek OpenType Yazı Tipi Paketi](sample-opentype-font-pack.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)
