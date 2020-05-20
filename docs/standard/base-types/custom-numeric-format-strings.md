---
title: Özel sayısal biçim dizeleri
ms.date: 06/25/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- format strings
- custom numeric format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- formatting numbers [.NET Framework]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
ms.openlocfilehash: 1e2456da9fd1b9bd26d0317c0d04c6d1b61cf16d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440922"
---
# <a name="custom-numeric-format-strings"></a>Özel sayısal biçim dizeleri

Sayısal verinin nasıl biçimlendirileceğini tanımlamak için bir veya daha fazla özel sayısal tanımlayıcıdan oluşan özel bir sayısal biçim dizesi oluşturabilirsiniz. Özel bir sayısal biçim dizesi, [Standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md)olmayan herhangi bir biçim dizesidir.

Özel sayısal biçim dizeleri, `ToString` tüm sayısal türdeki metodun bazı aşırı yüklemeleri tarafından desteklenir. Örneğin, <xref:System.Int32.ToString%28System.String%29> türünün ve yöntemlerine bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> <xref:System.Int32> . Özel sayısal biçim dizeleri, [composite formatting feature](../../../docs/standard/base-types/composite-formatting.md) `Write` ve sınıflarının bazı ve `WriteLine` yöntemleri <xref:System.Console> <xref:System.IO.StreamWriter> , yöntemi ve <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi tarafından kullanılan .net Composite biçimlendirme özelliği tarafından da desteklenir. [Dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) özelliği de özel sayısal biçim dizelerini destekler.

> [!TIP]
> Sayısal veya tarih ve saat değerlerine biçim dizeleri uygulamanızı sağlayan ve sonuç dizesini görüntüleyen bir .NET Core Windows Forms uygulaması olan **biçimlendirme yardımcı programını**indirebilirsiniz. Kaynak kodu [C#](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs) ve [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb)için kullanılabilir.

<a name="table"></a>Aşağıdaki tabloda özel sayısal biçim belirticileri açıklanmakta ve her biçim belirticisi tarafından üretilen örnek çıktı görüntülenir. Özel sayısal biçim dizeleri kullanma hakkında ek bilgi için [Notlar](#NotesCustomFormatting) bölümüne ve kullanımlarının kapsamlı bir gösterimi için [örnek](#example) bölümüne bakın.

|Biçim belirteci|Name|Açıklama|Örnekler|
|----------------------|----------|-----------------|--------------|
|"0"|Sıfır yer tutucu|Eğer varsa, karşılık gelen rakamı sıfır ile değiştirir; aksi halde sonuç dizesinde sıfır görünür.<br /><br /> Daha fazla bilgi: ["0" özel Belirleyicisi](#Specifier0).|1234,5678 ("00000")-> 01235<br /><br /> 0,45678 ("0,00", en-US)-> 0,46<br /><br /> 0,45678 ("0,00", fr-FR)-> 0, 46|
|"#"|Basamak yer tutucusu|Eğer varsa, karşılık gelen rakamı "#" sembolü ile değiştirir; aksi halde sonuç dizesinde hiçbir rakam gözükmez.<br /><br /> Giriş dizesindeki karşılık gelen basamak, önemli olmayan 0 ise sonuç dizesinde bir basamak göründüğünü unutmayın. Örneğin, 0003 ("# # # #")-> 3.<br /><br /> Daha fazla bilgi: ["#" özel Belirleyicisi](#SpecifierD).|1234,5678 ("# # # # #")-> 1235<br /><br /> 0,45678 ("#. # #", en-US)->.46<br /><br /> 0,45678 ("#. # #", fr-FR)->, 46|
|"."|Ondalık noktası|Sonuç dizesindeki ondalık ayracının konumunu belirler.<br /><br /> Daha fazla bilgi: ["." Özel tanımlayıcı](#SpecifierPt).|0,45678 ("0,00", en-US)-> 0,46<br /><br /> 0,45678 ("0,00", fr-FR)-> 0, 46|
|","|Grup ayırıcısı ve numara ölçekleme|Hem bir grup ayracı, hem de sayı ölçekleme tanımlayıcısı olarak kullanılır. Grup ayracı olarak, her grup arasında yerelleştirilmiş bir grup ayracı karakteri ekler. Sayı ölçekleme tanımlayıcısı olarak, bir sayıyı belirtilen her virgül için 1000'e böler.<br /><br /> Daha fazla bilgi: ["," özel Belirleyicisi](#SpecifierTh).|Grup ayracı tanımlayıcısı:<br /><br /> 2147483647 ("# #, #", en-US)-> 2.147.483.647<br /><br /> 2147483647 ("# #, #", ES-ES)-> 2.147.483.647<br /><br /> Ölçekleme tanımlayıcısı:<br /><br /> 2147483647 ("#, #,,", en-US)-> 2.147<br /><br /> 2147483647 ("#, #,,", ES-ES)-> 2,147|
|"%"|Yüzde yer tutucu|Sayıyı 100 ile çarpar ve sonuç dizesine yerelleştirilmiş bir yüzde simgesi ekler.<br /><br /> Daha fazla bilgi: ["%" özel Belirleyicisi](#SpecifierPct).|0,3697 ("% #0.00", en-US)->% 36,97<br /><br /> 0,3697 ("% #0 00", el-GR)->% 36, 97<br /><br /> 0,3697 ("# #. 0%", en-US)-> 37,0%<br /><br /> 0,3697 ("# #. 0%", el-GR)-> 37, %0|
|"‰"|Her mille yer tutucu|Sayıyı 1000 ile çarpar ve sonuç dizesine yerelleştirilmiş bir binde simgesi ekler.<br /><br /> Daha fazla bilgi: ["‰" özel Belirleyicisi](#SpecifierPerMille).|0,03697 ("#0.00‰", en-US)-> 36,97‰<br /><br /> 0,03697 ("#0 00‰", ru-RU)-> 36, 97‰|
|"E0"<br /><br /> "E+0"<br /><br /> "E-0"<br /><br /> "e0"<br /><br /> "e+0"<br /><br /> "e-0"|Üstel simgeleme|Eğer ardından en az bir 0 (sıfır) geliyorsa, sonucu üstel gösterim kullanarak biçimlendirir. "E" veya "e" harfi üs sembolünün sonuç dizesinde büyük veya küçük harf olduğunu belirtir. "E" veya "e" karakterini izleyen sıfır sayısı üsteki en az basamak sayısını belirler. Artı işareti (+) üsten önce her zaman bir işaret karakterinin bulunacağını belirtir. Eksi işareti (-), işaret karakterinin yalnızca negatif üslerin önünde bulunacağını belirtir.<br /><br /> Daha fazla bilgi: ["e" ve "e" özel belirticileri](#SpecifierExponent).|987654 ("#0.0e0")-> 98.8 E4<br /><br /> 1503,92311 ("0,0 # #e + 00")-> 1.504 e + 03<br /><br /> 1.8901385 e-16 ("0.0 e + 00")-> 1.9 e-16|
|"\\"|Atlatma karakteri|Sonraki karakterin özel biçim tanımlayıcısı yerine bir sabit karakter olarak yorumlanmasını sağlar.<br /><br /> Daha fazla bilgi: [" \\ " kaçış karakteri](#SpecifierEscape).|987654 (" \\ # # #00 \\ #")-> #987654 #|
|'*String*'<br /><br /> "*String*"|Değişmez dize sınırlayıcısı|İçinde bulunan karakterlerin sonuç dizesine değiştirilmeden kopyalanacağını belirtir.<br/><br/>Daha fazla bilgi: [karakter sabit değerleri](#character-literals).|68 ("#" derece ' ")-> 68 derece<br /><br /> 68 ("#" derece ' ")-> 68 derece|
|;|Bölüm ayırıcı|Pozitif, negatif ve sıfır değerine sahip sayılar için ayrı biçim dizeleri tanımlar.<br /><br /> Daha fazla bilgi: [";" Bölüm ayırıcısı](#SectionSeparator).|12,345 ("#0 0 #;(#0.0 #);-\ 0-")-> 12,35<br /><br /> 0 ("#0 0 #;(#0.0 #);-\ 0-")->-0-<br /><br /> -12,345 ("#0 0 #;(#0.0 #);-\ 0-")-> (12,35)<br /><br /> 12,345 ("#0 0 #;(#0.0 #)")-> 12,35<br /><br /> 0 ("#0 0 #;(#0.0 #)")-> 0,0<br /><br /> -12,345 ("#0 0 #;(#0.0 #)")-> (12,35)|
|Diğer|Diğer karakterler|Karakter, değişmeyen sonuç dizesine kopyalanır.<br/><br/>Daha fazla bilgi: [karakter sabit değerleri](#character-literals).|68 ("# °")-> 68 °|

Aşağıdaki bölümler her özel sayısal biçim tanımlayıcısı hakkında ayrıntılı bilgi sağlar.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)]

<a name="Specifier0"></a>

## <a name="the-0-custom-specifier"></a>"0" özel belirticisi

"0" özel biçim tanımlayıcısı sıfır için yer tutucu sembol olarak kullanılır. Eğer biçimlendirilen değerin, biçim dizesinde sıfırın bulunduğu konumunda bir sayı varsa o sayı sonuç dizesine kopyalanır, aksi halde sonuç dizesinde sıfır görünür. Ondalık noktasından önceki en sol sıfır ve ondalık noktasından sonraki en sağ sıfır, sonuç dizesinde her zaman bulunacak basamak aralığını belirler.

"00" tanımlayıcısı değerin ondalıktan önceki en yakın sayıya yuvarlanmasını sağlar ve her zaman sıfırdan öteye yuvarlama uygulanır. Örneğin, 34.5 değeri "00" ile biçimlendirildiğinde 35 olur.

Aşağıdaki örnek sıfır yer tutucu karakterleri içeren özel biçim dizelerini kullanarak biçimlendirilen birkaç değeri gösterir.

[!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
[!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
[!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]

[Tabloya dön](#table)

<a name="SpecifierD"></a>

## <a name="the--custom-specifier"></a>"#" Özel belirticisi

"#" özel biçim tanımlayıcısı basamak için yer tutucu sembol olarak kullanılır. Eğer biçimlendirilen değerin, biçim dizesinde "#" sembolünün bulunduğu konumunda bir sayı varsa o sayı sonuç dizesine kopyalanır. Aksi halde, sonuç dizesinin o konumuna hiçbir şey tutulmaz.

Bu tanımlayıcının önemli basamak olmayan bir sıfırı, sıfır dizedeki tek basamak olsa bile asla göstermediğini unutmayın. Sıfırı ancak sayıdaki gösterilen bir önemli basamak olduğunda gösterir.

"##" tanımlayıcısı değerin ondalıktan önceki en yakın sayıya yuvarlanmasını sağlar ve her zaman sıfırdan öteye yuvarlama uygulanır. Örneğin, 34.5 değeri "##" ile biçimlendirildiğinde 35 olur.

Aşağıdaki örnek basamak yer tutucu karakterleri içeren özel biçim dizelerini kullanarak biçimlendirilen birkaç değeri gösterir.

[!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
[!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
[!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]

Eksik basamakların veya baştaki sıfırların boşluklarla değiştirildiği bir sonuç dizesi döndürmek için, [Bileşik biçimlendirme özelliğini](../../../docs/standard/base-types/composite-formatting.md) kullanın ve aşağıdaki örnekte gösterildiği gibi bir alan genişliği belirleyin.

[!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
[!code-csharp[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
[!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]

[Tabloya dön](#table)

<a name="SpecifierPt"></a>

## <a name="the--custom-specifier"></a>"." Özel Belirleyicisi

"." özel biçim tanımlayıcısı sonuç dizesine yerelleştirilmiş bir ondalık ayracı ekler. Biçim dizesindeki ilk nokta biçimlendirilen değerdeki ondalık ayracının konumunu belirler; diğer ek noktalar göz ardı edilir.

Sonuç dizesinde ondalık ayırıcı olarak kullanılan karakter her zaman bir nokta değildir; <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> <xref:System.Globalization.NumberFormatInfo> biçimlendirmeyi denetleyen nesnenin özelliği tarafından belirlenir.

Aşağıdaki örnek birkaç sonuç dizesindeki ondalık noktasının konumunu tanımlamak için "." biçim tanımlayıcısını kullanır.

[!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
[!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
[!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]

[Tabloya dön](#table)

<a name="SpecifierTh"></a>

## <a name="the--custom-specifier"></a>"," Özel Belirleyicisi

"," karakteri hem bir grup ayracı, hem de sayı ölçekleme tanımlayıcısı olarak kullanılır.

- Grup ayracı: Eğer bir sayının tamsayı basamaklarını biçimlendiren iki basamak yer tutucu karakteri (0 veya #) arasında bir veya daha fazla virgül belirtilirse, çıktının tamsayı bölümündeki her sayı grubunun arasında bir grup ayracı karakteri eklenir.

  <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> Geçerli nesnenin ve özellikleri, <xref:System.Globalization.NumberFormatInfo> sayı Grup ayırıcısı olarak kullanılan karakteri ve her bir sayı grubunun boyutunu belirlemektir. Örneğin, 1000 sayısını biçimlendirmek için "#,#" dizesi ve sabit kültür kullanılırsa, çıktı "1,000" olur.

- Sayı ölçekleme tanımlayıcısı: Eğer açık veya örtülü ondalık noktasının hemen solunda bir veya daha fazla virgül belirtilirse, biçimlendirilen sayı her virgül için 1000 ile bölünür. Örneğin, eğer 100 milyon sayısını biçimlendirmek için "0,," dizesi kullanılırsa, çıktı "100" olur.

Aynı biçim dizesinde grup ayracı ve sayı ölçekleme tanımlayıcılarını kullanabilirsiniz. Örneğin, eğer bir milyar sayısını biçimlendirmek için "#,0,," dizesi ve sabit kültür kullanılırsa, çıktı "1,000" olur.

Aşağıdaki örnek virgülün bir grup ayracı olarak kullanımını gösterir.

[!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
[!code-csharp[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
[!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]

Aşağıdaki örnek virgülün sayı ölçekleme için bir tanımlayıcı olarak kullanımını gösterir.

[!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
[!code-csharp[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
[!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]

[Tabloya dön](#table)

<a name="SpecifierPct"></a>

## <a name="the--custom-specifier"></a>"%" Özel Belirleyicisi

Biçim dizesindeki bir yüzde işareti (%) sayının biçimlendirilmeden önce 100 ile çarpılmasına neden olur. Sayıya, % karakterinin biçim dizesinde bulunduğu konumda yerelleştirilmiş bir yüzde sembolü eklenir. Kullanılan yüzde karakteri <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> geçerli nesnenin özelliği tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo> .

Aşağıdaki örnek "%" özel tanımlayıcısını içeren birkaç özel biçim dizesini tanımlar.

[!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
[!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
[!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]

[Tabloya dön](#table)

<a name="SpecifierPerMille"></a>

## <a name="the--custom-specifier"></a>"‰" Özel Belirleyicisi

Biçim dizesindeki binde bir karakteri (‰ veya \u2030) sayının biçimlendirilmeden önce 1000 ile çarpılmasına neden olur. Dönüş dizesine, ‰ karakterinin biçim dizesinde bulunduğu konumda uygun bir binde bir karakteri eklenir. Kullanılan Mille başına karakter, <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> kültüre özgü biçimlendirme bilgileri sağlayan nesnesinin özelliği tarafından tanımlanır.

Aşağıdaki örnek "‰" özel tanımlayıcısını içeren bir özel biçim dizesi tanımlar.

[!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
[!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
[!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]

[Tabloya dön](#table)

<a name="SpecifierExponent"></a>

## <a name="the-e-and-e-custom-specifiers"></a>"E" ve "e" özel belirticileri

Eğer biçim dizesinde "E", "E+", "E-", "e", "e+" veya "e-" dizelerinden herhangi biri bulunuyorsa ve hemen ardından en az bir sıfır geliyorsa, sayı bilimsel gösterim kullanılarak biçimlendirilir ve sayı ile üs arasına bir "E" veya "e" eklenir. Bilimsel gösterim göstergesinin ardından gelen sıfırların sayısı üs için çıktıda bulunacak en az basamak sayısını belirler. "E+" ve "e+" biçimleri üssün önünde her zaman bir artı veya eksi işareti bulunacağını belirtir. "E", "E-", "e" veya "e-" biçimleri işaret karakterinin yalnızca negatif üslerin önünde bulunacağını belirtir.

Aşağıdaki örnek bilimsel gösterim tanımlayıcılarını kullanarak birkaç sayısal değeri biçimlendirir.

[!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
[!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
[!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]

[Tabloya dön](#table)

<a name="SpecifierEscape"></a>

## <a name="the--escape-character"></a>" \\ " Kaçış karakteri

Biçimlendirme dizesindeki "#", "0", ".", ",", "%" ve "‰" sembolleri sabit karakterler yerine biçim tanımlayıcıları olarak yorumlanır. Özel biçim dizesindeki konumlarına göre, büyük / küçük harf "E" ve + ve - sembolleri de biçim tanımlayıcıları olarak yorumlanabilir.

Bir karakterin biçim belirleyicisi olarak yorumlanmasını önlemek için önüne kaçış karakteri olan ters eğik çizgi koyabilirsiniz. Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.

Bir sonuç dizesinde ters eğik çizgi eklemek için, başka bir ters eğik çizgiyle () kaçış yapmanız gerekir `\\` .

> [!NOTE]
> C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.

Aşağıdaki örnek, biçimlendirme işleminin "#", "0" ve " \\ " karakterlerinin kaçış karakterleri veya biçim belirticileri olarak yorumlanmasını engellemek için kaçış karakterini kullanır. C# örnekleri ters eğik çizginin sabit karakter olarak yorumlanması için ek bir ters eğik çizgi kullanır.

[!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
[!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
[!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]

[Tabloya dön](#table)

<a name="SectionSeparator"></a>

## <a name="the--section-separator"></a>";" Bölüm ayırıcısı

Noktalı virgül (;), sayının değerinin pozitif, negatif veya sıfır olma durumuna göre farklı biçimlendirme işlemi uygulayan bir koşullu biçim tanımlayıcısıdır. Bu davranışı oluşturmak için, bir özel biçim dizesi noktalı virgüllerle ayrılan en çok üç bölüm içerebilir. Bu bölümler aşağıdaki tabloda açıklanır.

|Bölüm sayısı|Açıklama|
|------------------------|-----------------|
|Bir bölüm|Biçim dizesi tüm değerlere uygulanır.|
|İki bölüm|İlk bölüm pozitif değerlere ve sıfırlara, ikinci bölüm de negatif değerlere uygulanır.<br /><br /> Eğer biçimlendirilen değer negatif ise, ama ikinci bölümdeki biçimlendirmeden sonra yuvarlama ile sıfır olursa, sonuçtaki sıfır ilk bölüme göre biçimlendirilir.|
|Üç bölüm|İlk bölüm pozitif değerlere, ikinci bölüm negatif değerlere, ve üçüncü bölüm sıfırlara uygulanır.<br /><br /> İkinci bölüm boş bırakılabilir (noktalı virgüller arasına hiçbir şey konmayarak), ki bu durumda ilk bölüm tüm sıfır olmayan değerlere uygulanır.<br /><br /> Eğer biçimlendirile sayı sıfır değil ise, ama ilk veya ikinci bölümdeki biçimlendirmeden sonra yuvarlama ile sıfır olursa, sonuçtaki sıfır üçüncü bölüme göre biçimlendirilir.|

Bölüm ayıraçları, son değer biçimlendirilirken sayıyla ilişkili önceden bulunan biçimlendirmeyi göz ardı eder. Örneğin, bölüm ayıraçları kullanıldığında negatif değerler her zaman eksi işareti olmadan görüntülenir. Eğer biçimlendirilen son değerin eksi işaretine sahip olmasını istiyorsanız, eksi işaretini özel biçim tanımlayıcısına açıkça eklemeniz gerekir.

Aşağıdaki örnek pozitif, negatif ve sıfır değerine sahip sayıları farklı biçimlendirmek için ";" biçim tanımlayıcısını kullanır.

[!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
[!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
[!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]

[Tabloya dön](#table)

## <a name="character-literals"></a>Karakter sabit değerleri

Özel bir sayısal biçim dizesinde görüntülenen biçim belirticileri her zaman biçimlendirme karakterleri olarak yorumlanır ve hiçbir zaman değişmez karakterler değildir. Bu, aşağıdaki karakterleri içerir:

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- Biçim dizesindeki konumuna bağlı olarak [e veya h](#SpecifierExponent).

Tüm diğer karakterler her zaman karakter değişmezleri olarak yorumlanır ve bir biçimlendirme işleminde, sonuç dizesine değiştirilmeden dahil edilir.  Bir ayrıştırma işleminde, giriş dizesindeki karakterlerle tam olarak eşleşmesi gerekir; Karşılaştırma büyük/küçük harfe duyarlıdır.

Aşağıdaki örnek, değişmez karakter birimlerinin yaygın olarak kullanılan bir kullanımını gösterir (Bu durumda, binlerce):

[!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
[!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]

Karakterlerin, bir sonuç dizesine eklenebilir veya bir giriş dizesinde başarıyla ayrıştırılabilmeleri için, biçimlendirme karakterleri olarak değil, karakterlerin değişmez karakter olarak yorumlanabileceğini belirten iki yol vardır:

- Bir biçimlendirme karakterini kaçış. Daha fazla bilgi için [" \\ " kaçış karakterine](#SpecifierEscape)bakın.

- Tüm sabit değer dizesini tırnak işareti içine alarak.

Aşağıdaki örnek, özel bir sayısal biçim dizesinde ayrılmış karakterleri dahil etmek için her iki yaklaşımı kullanır.

[!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
[!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]

<a name="NotesCustomFormatting"></a>

## <a name="notes"></a>Notlar

### <a name="floating-point-infinities-and-nan"></a>Kayan nokta sonsuz ve NaN

Biçim dizesi ne olursa olsun, bir <xref:System.Single> veya <xref:System.Double> kayan nokta türünün değeri pozitif sonsuzluk, negatif sonsuzluk veya sayı değil (NaN), biçimlendirilen dize <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A> geçerli geçerli <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A> <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> nesne tarafından belirtilen ilgili, veya özelliğin değeridir <xref:System.Globalization.NumberFormatInfo> .

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar <xref:System.Globalization.NumberFormatInfo> , geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmak için kullanılır ve geçerli iş parçacığı kültürü biçimlendirmeyi yönetmek için kullanılan değerleri sağlar. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> <xref:System.Globalization.CultureInfo> geçerli sistem kültürüyle aynı kültürü temsil eden yeni bir nesne oluşturmak için oluşturucuyu kullanırsanız, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesi tarafından belirlenen tüm özelleştirmeler yeni <xref:System.Globalization.CultureInfo> nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29>Oluşturucuyu, <xref:System.Globalization.CultureInfo> sistemin özelleştirmelerini yansıtmayan bir nesne oluşturmak için kullanabilirsiniz.

### <a name="rounding-and-fixed-point-format-strings"></a>Yuvarlama ve sabit nokta biçim dizeleri

Sabit nokta biçim dizeleri için (yani, bilimsel gösterim biçim karakterleri içermeyen biçim dizeleri için), sayılar ondalık noktasının sağındaki basamak yer tutucuları sayısı kadar ondalık konuma yuvarlanır. Eğer biçim dizesi bir ondalık noktası içermiyorsa, sayı en yakın tamsayıya yuvarlanır. Eğer sayının, ondalık noktanın solundaki basamak yer tutucularından daha çok basamağı var ise, ek basamaklar sonuç dizesine ilk basamak yer tutucusundan hemen önce kopyalanır.

[Tabloya dön](#table)

<a name="example"></a>

## <a name="example"></a>Örnek

Aşağıdaki örnek iki özel sayısal biçim dizesini gösterir. Her iki durumda da, basamak yer tutucusu ( `#` ) sayısal verileri, diğer tüm karakterler sonuç dizesine kopyalanır.

[!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
[!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
[!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]

[Tabloya dön](#table)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb)
