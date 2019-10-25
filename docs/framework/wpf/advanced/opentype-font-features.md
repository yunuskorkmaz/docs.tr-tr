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
ms.openlocfilehash: da8f3e592e47c9482d4395b81627c1582e2354f7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72005243"
---
# <a name="opentype-font-features"></a>OpenType Yazı Tipi Özellikleri

Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]OpenType yazı tipi teknolojisinin bazı temel özelliklerine genel bakış sağlar.  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType yazı tipi biçimi  
 OpenType yazı tipi biçimi, TrueType® yazı tipi biçiminin bir uzantısıdır ve PostScript yazı tipi verileri için destek ekler. OpenType yazı tipi biçimi Microsoft ve Adobe Corporation tarafından ortaklaşa geliştirilmiştir. OpenType yazı tiplerini destekleyen OpenType yazı tipleri ve işletim sistemi hizmetleri, kullanıcıların yazı tiplerini TrueType anahatlar veya CFF (PostScript) anahatları içerip içermediği gibi kolay bir şekilde kullanmasını sağlar.  
  
 OpenType yazı tipi biçimi aşağıdaki geliştirici güçlüklerine yöneliktir:  
  
- Daha geniş çok platformlu destek.  
  
- Uluslararası karakter kümeleri için daha iyi destek.  
  
- Yazı tipi verileri için daha iyi koruma.  
  
- Yazı tipi dağıtımını daha verimli hale getirmek için daha küçük dosya boyutları.  
  
- Gelişmiş tipografik denetim için daha geniş destek.  
  
> [!NOTE]
> Windows SDK, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarıyla kullanabileceğiniz örnek bir OpenType yazı tipi kümesi içerir. Bu yazı tipleri, bu konunun geri kalanında gösterilen özelliklerin çoğunu sağlar. Daha fazla bilgi için bkz. [örnek OpenType yazı tipi paketi](sample-opentype-font-pack.md).  
  
 OpenType yazı tipi biçiminin ayrıntıları için bkz. [OpenType belirtimi](https://go.microsoft.com/fwlink/?LinkId=96731) .  
  
### <a name="advanced-typographic-extensions"></a>Gelişmiş tipografik uzantılar  
 Gelişmiş tipografik tablolar (OpenType Düzen tabloları), yazı tiplerinin işlevselliğini TrueType ya da CFF anahatlarıyla genişletir. OpenType Düzen yazı tipleri, yüksek kaliteli uluslararası Tipografisi desteklemek için yazı tiplerinin yeteneklerini genişleten ek bilgiler içerir. Çoğu OpenType yazı tipi, kullanılabilen toplam OpenType özelliklerinin yalnızca bir alt kümesini sunar. OpenType yazı tipleri aşağıdaki özellikleri sağlar.  
  
- Ligatür, konumsal formlar, alternatifler ve diğer yazı tipi değişimlerini destekleyen karakterler ve Glifler arasında zengin eşleme.  
  
- İki boyutlu konumlandırma ve glif eki için destek.  
  
- Yazı tipinde bulunan açık betik ve dil bilgileri, bir metin işleme uygulaması davranışını uygun şekilde ayarlayabilir.  
  
 OpenType Düzen tabloları, OpenType belirtiminin ["yazı tipi dosya tabloları"](https://www.microsoft.com/typography/otspec/otff.htm) bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
 Bu genel bakışın geri kalanında <xref:System.Windows.Documents.Typography> nesnesinin özellikleri tarafından açığa çıkarılan, bazı görsel açıdan ilgi çekici OpenType özelliklerinin kapsamını ve esnekliği tanıtılmıştır. Bu nesne hakkında daha fazla bilgi için bkz. [tipografi sınıfı](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Değişkenler  
 Çeşitler, üst simgeler ve alt simgeler gibi farklı tipografik stilleri işlemek için kullanılır.  
  
### <a name="superscripts-and-subscripts"></a>Üst simgeler ve alt simgeler  
 <xref:System.Windows.Documents.Typography.Variants%2A> özelliği, OpenType yazı tipi için üst simge ve alt simge değerlerini ayarlamanıza olanak sağlar.  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için üst simgeler görüntüler.  
  
 ![OpenType üst simgelerin kullanıldığı metin](./media/opentype-font-features/opentype-superscripts.gif "OpenType üst simgelerin kullanıldığı metin")  
  
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Palatino Linotype yazı tipi için üst simgelerin nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için alt simgeler görüntüler.  
  
 ![OpenType alt simgeleri kullanan metin](./media/opentype-font-features/opentype-subscripts.gif "OpenType alt simgeleri kullanan metin")  
  
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Palatino Linotype yazı tipi için alt simgelerin nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Üst simgelerin ve alt simgelerin dekoratif kullanımları  
 Ayrıca, karışık büyük/küçük harf metin etkileri oluşturmak için üst simgeler ve alt simgeler de kullanabilirsiniz. Aşağıdaki metin Palatino Linotype yazı tipi için üst simge ve alt simge metnini görüntüler. Büyük harflerin etkilenmediğini unutmayın.  
  
 ![OpenType üst ve alt simgeler kullanan metin](./media/opentype-font-features/opentype-superscripts-subscripts.gif "OpenType üst ve alt simgeler kullanan metin")  

 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak bir yazı tipi için üst simgelerin ve alt simgelerin nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Büyük  
 Büyük harfler, büyük harf stilli Glifler halinde metin işleyen bir tipografik form kümesidir. Genellikle metin tüm büyük harfler olarak işlendiğinde, harfler arasındaki Aralık çok sıkı görünebilir ve harflerin ağırlığı ve oranı çok ağır olabilir. OpenType Küçük harfler, görüntülemeyi büyük harfler, başlık ve büyük Aralık gibi büyük harfler için çok sayıda stil biçimini destekler. Bu stil formatları, büyük harflerin görünümünü denetlemenize olanak tanır.  
  
 Aşağıdaki metin Pescadero yazı tipi için standart büyük harfleri, ardından "SmallCaps" ve "AllSmallCaps" olarak stillendirilmiş harfleri görüntüler. Bu durumda, üç sözcük için de aynı yazı tipi boyutu kullanılır.  
  
 ![OpenType büyük harflerin kullanıldığı metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerin kullanıldığı metin")  
  
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Pescadero yazı tipi için büyük harflerin nasıl tanımlanacağı gösterilmektedir. "SmallCaps" biçimi kullanıldığında, önde gelen büyük harf yok sayılır.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Başlık büyük harfleri  
 Başlık büyük harfleri ağırlığa göre daha hafif ve orantısız ve normal büyük harfler daha zarif bir görünüm sağlamak için tasarlanmıştır. Başlık harfleri genellikle daha büyük yazı tipi boyutlarında başlık olarak kullanılır. Aşağıdaki metin Pescadero yazı tipi için normal ve başlık büyük harfler görüntüler. İkinci satırdaki metnin daha dar olan genişliğini fark edin.  
  
 ![OpenType başlık büyük harflerin kullanıldığı metin](./media/opentype-font-features/opentype-titling-capitals.gif "OpenType başlık büyük harflerin kullanıldığı metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Pescadero yazı tipi için başlık yazılanın nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Sermaye aralığı  
 Sermaye aralığı, metinde tüm büyük harfleri kullanırken daha fazla boşluk sağlamanıza olanak tanıyan bir özelliktir. Büyük harfler genellikle küçük harflerle Blend için tasarlanmıştır. Büyük harf ve küçük harf arasında çekici görünen aralıklar, tüm büyük harfler kullanıldığında çok sıkı görünebilir. Aşağıdaki metin Pescadero yazı tipi için normal ve büyük harf aralıklarını görüntüler.  
  
 ![OpenType büyük aralıklarını kullanan metin](./media/opentype-font-features/opentype-capital-spacing.gif "OpenType büyük aralıklarını kullanan metin")  
 
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Pescadero yazı tipi için sermaye aralıklarının nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatürleri görüntülemeyi etkinleştirir  
 Bitişik harfler, daha okunaklı veya etkileyici metin oluşturmak için tek bir glifde biçimlendirilmiş iki veya daha fazla karakter. OpenType yazı tipleri dört tür ligatür destekler:  
  
- **Standart ligatür**. Okunabilirliğini geliştirmek için tasarlanmıştır. Standart ligatür "Fi", "fl" ve "FF" içerir.  
  
- **Bağlamsal ligatür**. Ligatürü oluşturan karakterler arasında daha iyi birleştirme davranışı sağlayarak okunabilirliği artırmak için tasarlanmıştır.  
  
- **Isteğe bağlı ligatür**. Süslü olacak şekilde tasarlanmıştır ve özellikle okunabilirlik için tasarlanmamıştır.  
  
- **Geçmiş ligatür**. Geçmişe göre tasarlanan ve özellikle okunabilirlik için tasarlanmayan.  
  
 Aşağıdaki metin Pericles yazı tipi için standart ligatür glifleri görüntüler.  
  
 ![OpenType standart ligatür kullanan metin](./media/opentype-font-features/opentype-standard-ligatures.gif "OpenType standart ligatür kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Pericles yazı tipi için standart ligatür karakterlerinin nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Aşağıdaki metin Pericles yazı tipi için isteğe bağlı ligatür glifleri görüntüler.  
  
 ![OpenType isteğe bağlı ligatür kullanan metin](./media/opentype-font-features/opentype-discretionary-ligatures.gif "OpenType isteğe bağlı ligatür kullanan metin")  
  
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Pericles yazı tipi için isteğe bağlı ligatür karakterlerinin nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Varsayılan olarak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] OpenType yazı tipleri standart ligatürleri etkinleştirir. Örneğin, Palatino Linotype yazı tipini kullanırsanız standart ligatür "Fi", "FF" ve "fl" Birleşik karakter karakteri olarak görünür. Her standart ligatür için karakter çiftinin birbirlerine dokunduğuna dikkat edin.  
  
 ![Palatino Linotype ile OpenType standart ligatür kullanan metin](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Palatino Linotype ile OpenType standart ligatür kullanan metin")    
   
 Ancak standart ligatür özelliklerini devre dışı bırakarak "FF" gibi standart bir ligatür, Birleşik bir karakter karakteri yerine iki ayrı karakter olarak görüntülenir.  
  
 ![Devre dışı OpenType standart ligatür kullanan metin](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Devre dışı OpenType standart ligatür kullanan metin")  
    
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Palatino Linotype yazı tipi için standart ligatür karakterlerinin nasıl devre dışı bırakılacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Lemeler  
 Süslemeler, kaligrafi ile sık kullanılan süslemeler ile ilişkili olan dekoratif karakterlerdir. Aşağıdaki metin Pescadero yazı tipi için standart ve dalgalı glifleri görüntüler.  
  
 ![OpenType standart ve dalgalı glifleri kullanan metin](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "OpenType standart ve dalgalı glifleri kullanan metin")  

 Dalgalı karakterler genellikle olay duyuruları gibi kısa tümceciklere dekoratif öğeler olarak kullanılır. Aşağıdaki metin, olayın adının büyük harflerini vurgulamak için süslemeler kullanır.  
  
 ![OpenType dalgalı karakterlerinin kullanıldığı metin](./media/opentype-font-features/opentype-swashes.gif "OpenType dalgalı karakterlerinin kullanıldığı metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak bir yazı tipi için süslemeleri nasıl tanımlayacağınızı gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Bağlamsal süslemeler  
 Dalgalı karakterlerin belirli birleşimleri, bitişik harfler üzerinde çakışan ligatür gibi etkileyici bir görünüme neden olabilir. Bağlamsal dalgalı bir değer kullanmak daha iyi bir görünüm üreten bir alternatif dalgalı karakter kullanmanıza olanak sağlar. Aşağıdaki metin, bağlamsal bir süs uygulandıktan önceki ve sonraki aynı kelimeyi gösterir.  
  
 ![OpenType bağlamsal dalgalı karakterlerinin kullanıldığı metin](./media/opentype-font-features/opentype-contextual-swashes.gif "OpenType bağlamsal dalgalı karakterlerinin kullanıldığı metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Pescadero yazı tipi için bağlamsal bir süs nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Bağlamsal  
 Alternatifler, standart bir karakter yerine kullanılabilecek karakterlerdir. Aşağıdaki örneklerde kullanılan Pericles yazı tipi gibi OpenType yazı tipleri, metin için farklı görünümler oluşturmak üzere kullanabileceğiniz alternatif glifler içerebilir. Aşağıdaki metin Pericles yazı tipi için standart glifleri görüntüler.  
  
 ![OpenType standart karakterlerinin kullanıldığı metin](./media/opentype-font-features/opentype-standard-glyphs.gif "OpenType standart karakterlerinin kullanıldığı metin")  

 Pericles OpenType yazı tipi, standart glif kümesine stil alternatifleri sağlayan ek glifler içerir. Aşağıdaki metin, biçimsel alternatif glifleri görüntüler.  
  
 ![OpenType biçimsel alternatif glifleri kullanan metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "OpenType biçimsel alternatif glifleri kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Pericles yazı tipi için biçimsel alternatif karakterlerin nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Aşağıdaki metin Pericles yazı tipi için diğer biçimsel diğer glifleri görüntüler.  
  
 ![Pericles yazı tipi için OpenType biçimsel alternatif glifleri kullanan metin](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Pericles yazı tipi için OpenType biçimsel alternatif glifleri kullanan metin")

 Aşağıdaki biçimlendirme örneği, bu diğer biçimsel diğer karakterlerin nasıl tanımlanacağını göstermektedir.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Rastgele bağlamsal alternatifler  
 Rastgele bağlamsal alternatifler, tek bir karakter için birden çok yedek karakter sağlar. Betik türü yazı tipleriyle uygulandığında, bu özellik, görünümde hafif farklılıklar bulunan rastgele seçilmiş karakterlerin bir kümesini kullanarak el yazısını taklit edebilir. Aşağıdaki metin Lindsey yazı tipi için rastgele bağlamsal alternatifleri kullanır. "A" harfinin görünümde biraz farklılık gösterdiğinden emin olun  
  
 ![OpenType rastgele bağlamsal alternatifleri kullanan metin](./media/opentype-font-features/opentype-random-contextual-alternates.gif "OpenType rastgele bağlamsal alternatifleri kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Lindsey yazı tipi için rastgele bağlamsal alternatiflerini nasıl tanımlayacağınızı gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Geçmiş formları  
 Geçmiş formları geçmişte ortak olan tipografik kurallardır. Aşağıdaki metin Palatino Linotype yazı tipi için bir karakter geçmiş biçimi kullanarak "Boston, Massachusetts" ifadesini görüntüler.  
  
 ![OpenType geçmiş formlarını kullanan metin](./media/opentype-font-features/opentype-historical-forms.gif "OpenType geçmiş formlarını kullanan metin")  
   
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Palatino Linotype yazı tipi için geçmiş formlarının nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Sayısal stiller  
 OpenType yazı tipleri, metindeki sayısal değerlerle kullanılabilecek çok sayıda özelliği destekler.  
  
### <a name="fractions"></a>Kesirli  
 OpenType yazı tipleri, eğik çizgili ve yığılmış dahil olmak üzere kesirler için stilleri destekler.  
  
 Aşağıdaki metin Palatino Linotype yazı tipi için kesir stillerini görüntüler.  
  
 ![OpenType eğik çizgili ve yığılmış kesirler kullanan metin](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "OpenType eğik çizgili ve yığılmış kesirler kullanan metin")  
   
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Palatino Linotype yazı tipi için kesir stillerinin nasıl tanımlanacağı gösterilmektedir.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Eski stil rakamları  
 OpenType yazı tipleri eski bir stil rakamı biçimini destekler. Bu biçim, artık standart olmayan stillerdeki rakamları görüntülemek için yararlıdır. Aşağıdaki metin Palatino Linotype yazı tipi için standart ve eski stil sayısal biçimlerinde bir 18 yüzyıl tarihi görüntüler.  
  
 ![OpenType eski stil rakamlarını kullanan metin](./media/opentype-font-features/opentype-old-style-numerals.gif "OpenType eski stil rakamlarını kullanan metin")  
    
 Aşağıdaki metin Palatino Linotype yazı tipi için standart rakamları ve ardından eski stil rakamlarını görüntüler.  
  
 ![OpenType eski stil sayısal kümelerini kullanan metin](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "OpenType eski stil sayısal kümelerini kullanan metin")  
  
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Palatino Linotype yazı tipi için eski stil rakamlarını nasıl tanımlayacağınızı gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Orantılı ve tablo rakamları  
 OpenType yazı tipleri, rakamlar kullanılırken genişlerinin hizalamasını denetlemek için orantılı ve tablolu şekil özelliğini destekler. Orantılı rakamlar her rakamı farklı genişliğe sahip olacak şekilde değerlendirir — "1", "5" değerinden daha dar. Tablo rakamları, finansal tür bilgilerinin okunabilirliğini artıran, dikey olarak hizalanabilmesi için eşit genişlik rakamları olarak değerlendirilir.  
  
 Aşağıdaki metin, Miramonte yazı tipini kullanarak ilk sütunda iki orantılı rakamları görüntüler. "5" ve "1" rakamları arasındaki genişlik farkını dikkate alın. İkinci sütunda, tablolu şekil özelliği kullanılarak ayarlanan genişlikler ile aynı iki sayısal değer gösterilir.  
  
 ![OpenType orantılı & Tablolu rakamları kullanan metin](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "OpenType orantılı ve tablo rakamlarını kullanan metin")  
    
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Miramonte yazı tipi için orantılı ve tablo rakamlarını nasıl tanımlayacağınızı gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Eğik çizgili sıfır  
 OpenType yazı tipleri, "O" harfi ve "0" rakamı arasındaki farkı vurgulamak için eğik çizgili sıfır rakamı biçimini destekler. Eğik çizgili sıfır rakamı genellikle finansal ve iş bilgileri tanımlayıcıları için kullanılır.  
  
 Aşağıdaki metin, Miramonte yazı tipini kullanarak örnek bir sıra tanımlayıcısı görüntüler. İlk satır standart rakamları kullanır. İkinci satır, büyük harfli "O" harfle daha iyi bir kontrast sağlamak için eğik çizgili sıfır rakamları kullandı.  
  
 ![OpenType eğik çizgili sıfır rakamlarını kullanan metin](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "OpenType eğik çizgili sıfır rakamlarını kullanan metin")  
    
 Aşağıdaki biçimlendirme örneği, <xref:System.Windows.Documents.Typography> nesnesinin özelliklerini kullanarak Miramonte yazı tipi için eğik çizgili sıfır rakamları nasıl tanımlayacağınızı gösterir.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Tipografi sınıfı  
 <xref:System.Windows.Documents.Typography> nesnesi, OpenType yazı tipinin desteklediği özellikler kümesini kullanıma sunar. Biçimlendirme içinde <xref:System.Windows.Documents.Typography> ' ın özelliklerini ayarlayarak OpenType özelliklerinden faydalanan belgeleri kolayca yazabilirsiniz.  
  
 Aşağıdaki metin Pescadero yazı tipi için standart büyük harfleri, ardından "SmallCaps" ve "AllSmallCaps" olarak stillendirilmiş harfleri görüntüler. Bu durumda, üç sözcük için de aynı yazı tipi boyutu kullanılır.  
  
 ![OpenType büyük harflerin kullanıldığı metin](./media/opentype-font-features/opentype-capitals.gif "OpenType büyük harflerin kullanıldığı metin")  
    
 Aşağıdaki biçimlendirme örneğinde, <xref:System.Windows.Documents.Typography> nesnesinin özellikleri kullanılarak Pescadero yazı tipi için büyük harflerin nasıl tanımlanacağı gösterilmektedir. "SmallCaps" biçimi kullanıldığında, önde gelen büyük harf yok sayılır.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Aşağıdaki kod örneği, önceki biçimlendirme örneği ile aynı görevi gerçekleştirir.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Tipografi sınıfı özellikleri  
 Aşağıdaki tabloda <xref:System.Windows.Documents.Typography> nesnesinin özellikleri, değerleri ve varsayılan ayarları listelenmektedir.  
  
|Özellik|Değer (ler)|Varsayılan Değer|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Sayısal değer-bayt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; 0 &#124; 2|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Sayısal değer-bayt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124;<xref:System.Windows.FontEastAsianLanguage.Jis04>&#124;<xref:System.Windows.FontEastAsianLanguage.Jis78>&#124;<xref:System.Windows.FontEastAsianLanguage.Jis83>&#124;<xref:System.Windows.FontEastAsianLanguage.Jis90>&#124;<xref:System.Windows.FontEastAsianLanguage.NlcKanji>&#124;<xref:System.Windows.FontEastAsianLanguage.Normal>&#124;<xref:System.Windows.FontEastAsianLanguage.Simplified>&#124;<xref:System.Windows.FontEastAsianLanguage.Traditional>&#124;<xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; 0|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; 0|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.Typography>
- [OpenType belirtimi](https://go.microsoft.com/fwlink/?LinkId=96731)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Örnek OpenType Yazı Tipi Paketi](sample-opentype-font-pack.md)
- [Uygulamalarla Yazı Tiplerini Paketleme](packaging-fonts-with-applications.md)
