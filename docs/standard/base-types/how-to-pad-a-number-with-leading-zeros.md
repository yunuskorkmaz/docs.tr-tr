---
title: 'Nasıl yapılır: Bir sayı önünde sıfır ile doldurur.'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd016bcb1484f7f94e509e79dbb6b9bb982dd96a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972571"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir sayı önünde sıfır ile doldurur.

"D"'ı kullanarak bir tamsayıya baştaki sıfırlar ekleyebilirsiniz [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md) bir duyarlık belirtici ile. Tamsayı ve kayan nokta sayıları baştaki sıfırlar ekleyebilirsiniz bir [özel sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md). Bu makalede, bir sayı sıfırları ile doldurulacak iki yöntem de kullanmayı gösterir.
  
## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Bir tamsayı, belirli bir süre için sıfırları ile doldurulacak
  
1. Tamsayı değeri görüntülemek istediğiniz basamak sayısı alt sınırını belirler. Bu sayıda önde gelen tüm basamaklar içerir.  
  
1. Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.  
  
    - Tam sayı ondalık bir değeri görüntülemek için arama, `ToString(String)` yöntemi ve pass dize "D*n*" değeri olarak `format` parametresi, burada *n* dize en küçük uzunluğunu temsil eder.  
  
    - Tamsayı bir onaltılık değer görüntülemek için çağrı kendi `ToString(String)` yöntemi ve pass dize "X*n*" biçim parametresinin değeri olarak burada *n* dize en küçük uzunluğunu temsil eder.
  
Biçim dizesi bir aradeğerlendirme dizesinde hem de kullanabilirsiniz [ C# ](../../csharp/language-reference/tokens/interpolated.md) ve [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), veya gibi bir yöntem çağırabilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithtype> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, kullanan [ Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz karakter ile sıfırları birkaç tamsayı değeri biçimlendirir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Belirli sayıda önünde sıfır ile tamsayı yazma  
  
1. Kaç tane baştaki sıfırlar istediğiniz görüntülemek için tamsayı değeri belirleyin.  
  
1. Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.

    - Ondalık değer olarak biçimlendirme "D" standart biçim tanımlayıcısı kullanmanızı gerektirir.

    - Bir onaltılık değer biçimlendirme "X" standart biçim tanımlayıcısı kullanmanızı gerektirir.
  
1. Tamsayı değerinin çağırarak unpadded sayısal dize uzunluğunu belirlemek `ToString("D").Length` veya `ToString("X").Length` yöntemi.
  
1. Biçimlendirilen dizesinde unpadded sayısal dize uzunluğu dahil etmek istediğiniz baştaki sıfırlar sayısı ekleyin. Baştaki sıfırlar sayısını ekleyerek toplam doldurulan bir dizenin uzunluğunu tanımlar.  
  
1. Tamsayı değerinin çağrı `ToString(String)` yöntemi ve pass dize "D*n*" ondalık dizeleri ve "X*n*" onaltılık dizeler için burada *n* toplam temsil eder doldurulan dize uzunluğu. Ayrıca "D*n*" veya "X*n*" biçimlendirme dizesi bileşik biçimlendirmeyi destekleyen bir yöntem.  
  
 Aşağıdaki örnek bir tamsayı değeri beş önünde sıfır ile sıfır ekleyerek doldurur.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Belirli bir süre için sıfırları ile sayısal bir değer yazma  
  
1. Küsur işaretinin solundaki kaç basamağa sahip bir sayının dize gösterimini istediğinizi belirleyin. Bu basamakların toplam sayısı, baştaki sıfırları içerir.  
  
1. Sıfır en az sayısını temsil etmek için sıfır yer tutucu "0" kullanan bir özel sayısal biçim dizesi tanımlar.  
  
1. Sayının çağrı `ToString(String)` yöntemi ve özel biçim dizesi geçirin. Özel biçim dizesi, dize ilişkilendirme ile veya bileşik biçimlendirmeyi destekleyen bir yöntemle de kullanabilirsiniz.  
  
 Aşağıdaki örnek, öndeki ile birkaç sayısal değeri biçimlendirir. Sonuç olarak, biçimlendirilen sayı toplam uzunluğu en az sekiz küsur işaretinin solundaki basamak olabilir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Baştaki sıfırlar, belirli bir değere sahip bir sayısal değer yazma  
  
1. Kaç tane baştaki sıfırlar sayısal bir değer olmasını istediğinizi belirleyin.  
  
1. Sol tarafındaki unpadded sayısal dizesindeki ondalık basamak sayısını belirler:  
  
    1. Bir sayının dize gösterimini bir ondalık noktası simgesi içerip içermediğini belirler.  
  
    1. Ondalık noktası simgesi dahil ederseniz, Ondalık ayırıcının solundaki karakter sayısını belirler.  
  
         -veya-  
  
         Ondalık noktası simgesi içermiyorsa, dizenin uzunluğunu belirler.  
  
1. Kullanan bir özel biçim dizesinde oluşturun:

    - Dizesinde görünmesi için sıfır için yer tutucu "0" her baştaki sıfırlar.

    - Sıfır yer tutucu ya da basmak yer tutucusu "#" varsayılan dizedeki her basamak gösterecek.
  
1. Özel biçim dizesi bir parametre olarak ya da sayının tedarik `ToString(String)` yöntemi veya bileşik biçimlendirmeyi destekleyen bir yöntem.  
  
 Aşağıdaki örnek iki sıfır ekleyerek doldurur <xref:System.Double> değerlerle beş baştaki sıfırlar.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
