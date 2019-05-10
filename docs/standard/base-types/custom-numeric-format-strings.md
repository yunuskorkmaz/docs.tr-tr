---
title: Özel Sayısal Biçim Dizeleri
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab06c2d87de9483d7a3e9eb810f4be1f3278ddc2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634519"
---
# <a name="custom-numeric-format-strings"></a>Özel sayısal biçim dizeleri

Sayısal verinin nasıl biçimlendirileceğini tanımlamak için bir veya daha fazla özel sayısal tanımlayıcıdan oluşan özel bir sayısal biçim dizesi oluşturabilirsiniz. Bir özel sayısal biçim dizesi değil herhangi bir biçim dizesi olan bir [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md).  

 Özel sayısal biçim dizeleri, bazı aşırı yüklemeleri tarafından desteklenir `ToString` tüm sayısal türlerin yöntemi. Örneğin, bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%29> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemlerinin <xref:System.Int32> türü. Özel sayısal biçim dizeleri de .NET tarafından desteklenen [bileşik biçimlendirme özelliği](../../../docs/standard/base-types/composite-formatting.md), yarafında kullanılır `Write` ve `WriteLine` yöntemlerinin <xref:System.Console> ve <xref:System.IO.StreamWriter> sınıfları, <xref:System.String.Format%2A?displayProperty=nameWithType>yöntemi ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi. [Dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) özelliği özel sayısal biçim dizeleri de destekler.  
  
> [!TIP]
>  İndirebileceğiniz [biçimlendirme yardımcı programı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), biçim sağlayan bir uygulama dizeleri sayısal veya tarih ve saat değerleri ve sonuç dizeyi görüntülemenizi.  
  
<a name="table"></a> Aşağıdaki tablo özel sayısal biçim belirteçlerini açıklar ve her biçim Belirleyicisinin ürettiği örnek çıktıları görüntüler. Bkz: [notları](#NotesCustomFormatting) özel sayısal biçim dizeleri kullanma hakkında ek bilgi bölümü ve [örnek](#example) kullanımlarının kapsamlı anlatımı için bölüm.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"0"|Sıfır yer tutucu|Eğer varsa, karşılık gelen rakamı sıfır ile değiştirir; aksi halde sonuç dizesinde sıfır görünür.<br /><br /> Daha fazla bilgi: ["0" özel Belirleyicisi](#Specifier0).|1234.5678 ("00000") -> 01235<br /><br /> 0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0,46 0.45678 ("0,00", fr-FR) ->|  
|"#"|Basamak yer tutucusu|Eğer varsa, karşılık gelen rakamı "#" sembolü ile değiştirir; aksi halde sonuç dizesinde hiçbir rakam gözükmez.<br /><br /> Giriş dizesindeki karşılık gelen rakamı önemli olmayan 0 ise sonuç dizesinde hiçbir rakam göründüğünü unutmayın. Örneğin, 0003 ("###") -> 3.<br /><br /> Daha fazla bilgi: ["#" Özel Belirleyicisi](#SpecifierD).|1234.5678 ("#####") -> 1235<br /><br /> 0.45678 ("#.##", en-US) -> .46<br /><br /> 0.45678 ("#.##", fr-FR) -> ,46|  
|"."|Ondalık noktası|Sonuç dizesindeki ondalık ayracının konumunu belirler.<br /><br /> Daha fazla bilgi: ["." Özel belirleyici](#SpecifierPt).|0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0,46 0.45678 ("0,00", fr-FR) ->|  
|","|Grup ayırıcısı ve numara ölçekleme|Hem bir grup ayracı, hem de sayı ölçekleme tanımlayıcısı olarak kullanılır. Grup ayracı olarak, her grup arasında yerelleştirilmiş bir grup ayracı karakteri ekler. Sayı ölçekleme tanımlayıcısı olarak, bir sayıyı belirtilen her virgül için 1000'e böler.<br /><br /> Daha fazla bilgi: ["," Özel Belirleyicisi](#SpecifierTh).|Grup ayracı tanımlayıcısı:<br /><br /> 2147483647 ("##, #", en-US) -> 2.147.483.647<br /><br /> 2147483647 ("##, #", es-ES) 2.147.483.647 -><br /><br /> Ölçekleme tanımlayıcısı:<br /><br /> 2147483647 ("#, #," en-US) -> 2,147<br /><br /> 2.147 2147483647'ye ("#, #,", es-ES) ->|  
|"%"|Yüzde yer tutucu|Sayıyı 100 ile çarpar ve sonuç dizesine yerelleştirilmiş bir yüzde simgesi ekler.<br /><br /> Daha fazla bilgi: ["%" Özel Belirleyicisi](#SpecifierPct).|% 36.97 0.3697 ("% #0.00" en-US) -><br /><br /> % 36,97 0.3697 ("% #0.00" el-GR) -><br /><br /> 0.3697 ("##.0%", en-US) -> %37.0<br /><br /> 0.3697 ("##.0%", el-GR) 37,0 -> %|  
|"‰"|Her mille yer tutucu|Sayıyı 1000 ile çarpar ve sonuç dizesine yerelleştirilmiş bir binde simgesi ekler.<br /><br /> Daha fazla bilgi: ["‰" Özel Belirleyicisi](#SpecifierPerMille).|0.03697 ("#0.00‰" en-US) -> 36.97‰<br /><br /> 0.03697 ("#0.00‰", ru-RU) 36 97‰ ->|  
|"E0"<br /><br /> "E+0"<br /><br /> "E-0"<br /><br /> "e0"<br /><br /> "e+0"<br /><br /> "e-0"|Üstel simgeleme|Eğer ardından en az bir 0 (sıfır) geliyorsa, sonucu üstel gösterim kullanarak biçimlendirir. "E" veya "e" harfi üs sembolünün sonuç dizesinde büyük veya küçük harf olduğunu belirtir. "E" veya "e" karakterini izleyen sıfır sayısı üsteki en az basamak sayısını belirler. Artı işareti (+) üsten önce her zaman bir işaret karakterinin bulunacağını belirtir. Eksi işareti (-), işaret karakterinin yalnızca negatif üslerin önünde bulunacağını belirtir.<br /><br /> Daha fazla bilgi: ["E" ve "e" özel tanımlayıcıları](#SpecifierExponent).|987654 ("#0.0e0") -> 98.8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|  
|"\\"|Atlatma karakteri|Sonraki karakterin özel biçim tanımlayıcısı yerine bir sabit karakter olarak yorumlanmasını sağlar.<br /><br /> Daha fazla bilgi: ["\\" Kaçış karakteri](#SpecifierEscape).|987654 ("\\###00\\#") -> #987654#|  
|'*dize*'<br /><br /> "*dize*"|Değişmez dize sınırlayıcısı|İçinde bulunan karakterlerin sonuç dizesine değiştirilmeden kopyalanacağını belirtir.<br/><br/>Daha fazla bilgi: [Karakter değişmez değerleri](#character-literals).|68 derece 68 ("# ' derece'") -><br /><br /> 68 ("#' derece") 68 derece ->|  
|;|Bölüm ayırıcı|Pozitif, negatif ve sıfır değerine sahip sayılar için ayrı biçim dizeleri tanımlar.<br /><br /> Daha fazla bilgi: [";" Bölüm ayırıcı](#SectionSeparator).|12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#);-\0-") -> -0-<br /><br /> -12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0.0<br /><br /> -12.345 ("#0.0#;(#0.0#)") -> (12.35)|  
|Diğer|Diğer karakterler|Karakter, değişmeyen sonuç dizesine kopyalanır.<br/><br/>Daha fazla bilgi: [Karakter değişmez değerleri](#character-literals).|68 ("# °") -> 68 °|  
  
 Aşağıdaki bölümler her özel sayısal biçim tanımlayıcısı hakkında ayrıntılı bilgi sağlar.  

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)] 
  
<a name="Specifier0"></a>   
## <a name="the-0-custom-specifier"></a>"0" özel Belirleyicisi  
 "0" özel biçim tanımlayıcısı sıfır için yer tutucu sembol olarak kullanılır. Eğer biçimlendirilen değerin, biçim dizesinde sıfırın bulunduğu konumunda bir sayı varsa o sayı sonuç dizesine kopyalanır, aksi halde sonuç dizesinde sıfır görünür. Ondalık noktasından önceki en sol sıfır ve ondalık noktasından sonraki en sağ sıfır, sonuç dizesinde her zaman bulunacak basamak aralığını belirler.  
  
 "00" tanımlayıcısı değerin ondalıktan önceki en yakın sayıya yuvarlanmasını sağlar ve her zaman sıfırdan öteye yuvarlama uygulanır. Örneğin, 34.5 değeri "00" ile biçimlendirildiğinde 35 olur.  
  
 Aşağıdaki örnek sıfır yer tutucu karakterleri içeren özel biçim dizelerini kullanarak biçimlendirilen birkaç değeri gösterir.  
  
 [!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
 [!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
 [!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierD"></a>   
## <a name="the--custom-specifier"></a>"#" Özel Belirleyicisi  
 "#" özel biçim tanımlayıcısı basamak için yer tutucu sembol olarak kullanılır. Eğer biçimlendirilen değerin, biçim dizesinde "#" sembolünün bulunduğu konumunda bir sayı varsa o sayı sonuç dizesine kopyalanır. Aksi halde, sonuç dizesinin o konumuna hiçbir şey tutulmaz.  
  
 Bu tanımlayıcının önemli basamak olmayan bir sıfırı, sıfır dizedeki tek basamak olsa bile asla göstermediğini unutmayın. Sıfırı ancak sayıdaki gösterilen bir önemli basamak olduğunda gösterir.  
  
 "##" tanımlayıcısı değerin ondalıktan önceki en yakın sayıya yuvarlanmasını sağlar ve her zaman sıfırdan öteye yuvarlama uygulanır. Örneğin, 34.5 değeri "##" ile biçimlendirildiğinde 35 olur.  
  
 Aşağıdaki örnek basamak yer tutucu karakterleri içeren özel biçim dizelerini kullanarak biçimlendirilen birkaç değeri gösterir.  
  
 [!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
 [!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
 [!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]  
  
 Basamak yok, bir sonuç dizesi veya 2f3b boşluk ile değiştirilir döndürmek için [bileşik biçimlendirme özelliği](../../../docs/standard/base-types/composite-formatting.md) ve aşağıdaki örnekte gösterildiği gibi bir alan genişliğini belirtin.  
  
 [!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
 [!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierPt"></a>   
## <a name="the--custom-specifier"></a>"." Özel Belirleyicisi  
 "." özel biçim tanımlayıcısı sonuç dizesine yerelleştirilmiş bir ondalık ayracı ekler. Biçim dizesindeki ilk nokta biçimlendirilen değerdeki ondalık ayracının konumunu belirler; diğer ek noktalar göz ardı edilir.  
  
 Sonuç dizesinde ondalık ayracı olarak kullanılan karakter her zaman nokta değildir; tarafından belirlenen <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliği <xref:System.Globalization.NumberFormatInfo> biçimlendirmeyi denetleyen nesne.  
  
 Aşağıdaki örnek birkaç sonuç dizesindeki ondalık noktasının konumunu tanımlamak için "." biçim tanımlayıcısını kullanır.  
  
 [!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
 [!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
 [!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierTh"></a>   
## <a name="the--custom-specifier"></a>"," Özel Belirleyicisi  
 "," karakteri hem bir grup ayracı, hem de sayı ölçekleme tanımlayıcısı olarak kullanılır.  
  
- Grup ayracı: İki basamak yer tutucu arasında bir veya daha fazla virgül belirtilirse (0 veya #), tamsayı basamaklarını bir sayının, çıktının tamsayı bölümündeki her sayı grubunun arasında bir grup ayracı karakteri eklenir.  
  
     <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> Ve <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> özelliklerinden <xref:System.Globalization.NumberFormatInfo> nesne belirlemek her sayı grubunun boyutu ve sayı grubu ayracı kullanılan karakter. Örneğin, 1000 sayısını biçimlendirmek için "#,#" dizesi ve sabit kültür kullanılırsa, çıktı "1,000" olur.  
  
- Sayı ölçekleme tanımlayıcısı: Açık veya örtülü ondalık noktasının solunda hemen bir veya daha fazla virgül belirtilirse, biçimlendirilen sayı her virgül için 1000'e bölünür. Örneğin, eğer 100 milyon sayısını biçimlendirmek için "0,," dizesi kullanılırsa, çıktı "100" olur.  
  
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
 Biçim dizesindeki bir yüzde işareti (%) sayının biçimlendirilmeden önce 100 ile çarpılmasına neden olur. Sayıya, % karakterinin biçim dizesinde bulunduğu konumda yerelleştirilmiş bir yüzde sembolü eklenir. Kullanılan yüzde karakteri tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> özelliği geçerli <xref:System.Globalization.NumberFormatInfo> nesne.  
  
 Aşağıdaki örnek "%" özel tanımlayıcısını içeren birkaç özel biçim dizesini tanımlar.  
  
 [!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
 [!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
 [!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierPerMille"></a>   
## <a name="the--custom-specifier"></a>"‰" Özel Belirleyicisi  
 Biçim dizesindeki binde bir karakteri (‰ veya \u2030) sayının biçimlendirilmeden önce 1000 ile çarpılmasına neden olur. Dönüş dizesine, ‰ karakterinin biçim dizesinde bulunduğu konumda uygun bir binde bir karakteri eklenir. Mille kullanılan karakter tarafından tanımlanan <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> özelliği kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
 Aşağıdaki örnek "‰" özel tanımlayıcısını içeren bir özel biçim dizesi tanımlar.  
  
 [!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
 [!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
 [!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierExponent"></a>   
## <a name="the-e-and-e-custom-specifiers"></a>"E" ve "e" özel Belirleyicileri  
 Eğer biçim dizesinde "E", "E+", "E-", "e", "e+" veya "e-" dizelerinden herhangi biri bulunuyorsa ve hemen ardından en az bir sıfır geliyorsa, sayı bilimsel gösterim kullanılarak biçimlendirilir ve sayı ile üs arasına bir "E" veya "e" eklenir. Bilimsel gösterim göstergesinin ardından gelen sıfırların sayısı üs için çıktıda bulunacak en az basamak sayısını belirler. "E+" ve "e+" biçimleri üssün önünde her zaman bir artı veya eksi işareti bulunacağını belirtir. "E", "E-", "e" veya "e-" biçimleri işaret karakterinin yalnızca negatif üslerin önünde bulunacağını belirtir.  
  
 Aşağıdaki örnek bilimsel gösterim tanımlayıcılarını kullanarak birkaç sayısal değeri biçimlendirir.  
  
 [!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
 [!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
 [!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]  
  
 [Tabloya dön](#table)  
  
<a name="SpecifierEscape"></a>   
## <a name="the--escape-character"></a>"\\" Kaçış karakteri  
 Biçimlendirme dizesindeki "#", "0", ".", ",", "%" ve "‰" sembolleri sabit karakterler yerine biçim tanımlayıcıları olarak yorumlanır. Özel biçim dizesindeki konumlarına göre, büyük / küçük harf "E" ve + ve - sembolleri de biçim tanımlayıcıları olarak yorumlanabilir.  
  
 Bir karakterin biçim belirleyicisi olarak yorumlanmasını önlemek için önüne kaçış karakteri olan ters eğik çizgi koyabilirsiniz. Çıkış karakteri, aşağıdaki karakterin değiştirilmeden sonuç dizesini dahil edilmesi gereken bir karakter sabiti olduğunu belirtir.  
  
 Sonuç dizesine ters eğik çizgi dahil etmek için bunu başka bir ters eğik çizgiyle kaçışını yapmanız gerekir (`\\`).  
  
> [!NOTE]
>  C++ ve C# derleyicileri gibi bazı derleyiciler, tek bir ters eğik çizgiyi çıkış karakteri olarak yorumlayabilir. Bir dizenin yalnızca düzgün biçimlendirildiğinde yorumlanmasını sağlamak için C# içinde dizeden önce değişmez değer karakterini (@ karakteri) kullanabilirsiniz veya C# ve C++ içinde her ters eğik çizgiden önce bir ters eğik çizgi daha ekleyebilirsiniz. Aşağıdaki C# örneği her iki yaklaşımı da gösterir.  
  
 Aşağıdaki örnek, biçimlendirme işleminin "#", "0" yorumlamasını önlemek için kaçış karakterini kullanır ve "\\" karakter kaçış karakterleri veya biçim tanımlayıcıları olarak. C# örnekleri ters eğik çizginin sabit karakter olarak yorumlanması için ek bir ters eğik çizgi kullanır.  
  
 [!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
 [!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]  
  
 [Tabloya dön](#table)  
  
<a name="SectionSeparator"></a>   
## <a name="the--section-separator"></a>";" Bölüm ayırıcı  
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

## <a name="character-literals"></a>Karakter değişmez değerleri  
 
Özel sayısal biçim dizesinde görünmesi biçim belirticileri her zaman biçimlendirme ve hiçbir zaman olarak değişmez karakterler yorumlanır. Bu karakterleri içerir:  

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- [E veya e](#SpecifierExponent)biçim dizesindeki konumuna bağlı olarak.

Diğer tüm karakterler, her zaman karakter değişmez değer olarak yorumlanır ve bir biçimlendirme işleminde değiştirilmeden sonuç dizesine eklenir.  Bir ayrıştırma işleminde Bunlar giriş dizesindeki bir karakter tam olarak eşleşmelidir; Karşılaştırma büyük/küçük harf duyarlıdır.  
  
Aşağıdaki örnekte, (Bu durumda, binlerce) değişmez değer birimlerinin yaygın olarak kullanıldığı gösterilmektedir:
  
 [!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
 [!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]  
  
 Sonuç dizesinde veya bir giriş dizesinde başarıyla ayrıştırıldı sabit değeri, gibi biçimlendirme karakter yorumlanması için karakter olduğunu belirtmek için iki yolu vardır:  
  
- Biçimlendirme bir karakter kaçış tarafından. Daha fazla bilgi için ["\\" kaçış karakteri](#SpecifierEscape).
  
- Tüm sabit dizesini tırnak işaretleri içinde kapsayan tarafından.

Aşağıdaki örnek, bir özel sayısal biçim dizesinde ayrılmış karakterleri eklemek için her iki yaklaşım kullanır.  
  
 [!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
 [!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]  
    
<a name="NotesCustomFormatting"></a>   
## <a name="notes"></a>Notlar  
  
### <a name="floating-point-infinities-and-nan"></a>Kayan nokta sonsuz ve NaN  
 Biçim dizesine bakılmaksızın, değeri bir <xref:System.Single> veya <xref:System.Double> kayan nokta türü, Pozitif sonsuz, negatif sonsuz veya sayı olmayan (NaN), biçimlendirilmiş dize ilgili değeri <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, veya <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> şu anda geçerli belirtilen özellik <xref:System.Globalization.NumberFormatInfo> nesne.  
  
### <a name="control-panel-settings"></a>Denetim Masası Ayarları  
 Ayarlarında **bölge ve Dil Seçenekleri** öğesinde bir biçimlendirme işlemiyle oluşturulan Sonuç dizesini Denetim Masası etkiler. Bu ayarları başlatmak için kullanılan <xref:System.Globalization.NumberFormatInfo> nesne, geçerli iş parçacığı kültürüyle ilişkilendirilen ve geçerli iş parçacığı kültürü biçimlendirmeyi yönetmek için değerler sunar. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.  
  
 Ayrıca kullandığınız, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> yeni bir örneğini oluşturmak için oluşturucu <xref:System.Globalization.CultureInfo> yapılan her özelleştirme mevcut sistem kültürüyle aynı kültürü temsil eden nesne **bölge ve Dil Seçenekleri** Denetim Masası'ndaki öğesi uygulanacak yeni <xref:System.Globalization.CultureInfo> nesne. Kullanabileceğiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturmak için bir <xref:System.Globalization.CultureInfo> sistem özelleştirmelerini içermeyen bir nesne.  
  
### <a name="rounding-and-fixed-point-format-strings"></a>Yuvarlama ve sabit nokta biçim dizeleri  
 Sabit nokta biçim dizeleri için (yani, bilimsel gösterim biçim karakterleri içermeyen biçim dizeleri için), sayılar ondalık noktasının sağındaki basamak yer tutucuları sayısı kadar ondalık konuma yuvarlanır. Eğer biçim dizesi bir ondalık noktası içermiyorsa, sayı en yakın tamsayıya yuvarlanır. Eğer sayının, ondalık noktanın solundaki basamak yer tutucularından daha çok basamağı var ise, ek basamaklar sonuç dizesine ilk basamak yer tutucusundan hemen önce kopyalanır.  
  
 [Tabloya dön](#table)  
  
<a name="example"></a>   
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki özel sayısal biçim dizesini gösterir. Her iki durumda da basmak yer tutucusu (`#`) sayısal veriyi ve tüm diğer karakterler sonuç dizesine kopyalanır görüntüler.  
  
 [!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
 [!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]  
  
 [Tabloya dön](#table)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Nasıl yapılır: Bir sayı önünde sıfır ile doldurur.](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Örnek: .NET Framework 4 biçimlendirme yardımcı](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
