---
title: 'Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3cc6e4d96378cfd8c065a3b04aab865f9b787438
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086728"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma
"D"'ı kullanarak bir tamsayıya baştaki sıfırlar ekleyebilirsiniz [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md) bir duyarlık belirtici ile. Tamsayı ve kayan nokta sayıları baştaki sıfırlar ekleyebilirsiniz bir [özel sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md). Bu konuda, her iki yöntem de sıfırları bir sayının paneli için nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Bir tamsayı, belirli bir süre için sıfırları ile doldurulacak  
  
1.  Tamsayı değeri görüntülemek istediğiniz basamak sayısı alt sınırını belirler. Bu sayıda önde gelen tüm basamaklar içerir.  
  
2.  Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.  
  
    -   Tam sayı ondalık bir değeri görüntülemek için arama, `ToString(String)` yöntemi ve pass dize "D*n*" değeri olarak `format` parametresi, burada *n* dize en küçük uzunluğunu temsil eder.  
  
    -   Tamsayı bir onaltılık değer görüntülemek için arama, `ToString(String)` yöntemi ve pass dize "X*n*" değeri olarak `format` parametresi, burada *n* en küçük uzunluğunu temsil eder dize.  
  
     Biçim dizesi bir yöntemde, aşağıdaki gibi kullanabilirsiniz <xref:System.String.Format%2A> veya <xref:System.Console.WriteLine%2A>, kullanan [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz karakter ile sıfırları birkaç tamsayı değeri biçimlendirir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Belirli sayıda önünde sıfır ile tamsayı yazma  
  
1.  Kaç tane baştaki sıfırlar istediğiniz görüntülemek için tamsayı değeri belirleyin.  
  
2.  Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin. Ondalık değer olarak biçimlendirme, "D" standart biçim tanımlayıcısı kullanmanızı gerektirir; bir onaltılık değer biçimlendirme "X" standart biçim tanımlayıcısı kullanmanızı gerektirir.  
  
3.  Tamsayı değerinin çağırarak unpadded sayısal dize uzunluğunu belirlemek `ToString("D").Length` veya `ToString("X").Length` yöntemi.  
  
4.  Biçimlendirilen dizesinde unpadded sayısal dize uzunluğu dahil etmek istediğiniz baştaki sıfırlar sayısı ekleyin. Bu, toplam uzunluğu doldurulan dize tanımlar.  
  
5.  Tamsayı değerinin çağrı `ToString(String)` yöntemi ve pass dize "D*n*" ondalık dizeleri ve "X*n*" onaltılık dizeler için burada *n* toplam temsil eder doldurulan dize uzunluğu. Ayrıca "D*n*" veya "X*n*" biçimlendirme dizesi bileşik biçimlendirmeyi destekleyen bir yöntem.  
  
 Aşağıdaki örnek bir tamsayı değeri beş önünde sıfır ile sıfır ekleyerek doldurur.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Belirli bir süre için sıfırları ile sayısal bir değer yazma  
  
1.  Küsur işaretinin solundaki kaç basamağa sahip bir sayının dize gösterimini istediğinizi belirleyin. Bu basamakların toplam sayısı, baştaki sıfırları içerir.  
  
2.  Sıfır en az sayısını temsil etmek için sıfır yer tutucusu ("0") kullanan bir özel sayısal biçim dizesi tanımlar.  
  
3.  Sayının çağrı `ToString(String)` yöntemi ve özel biçim dizesi geçirin. Özel biçim dizesi bileşik biçimlendirmeyi destekleyen bir yöntemle de kullanabilirsiniz.  
  
 Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz küsur işaretinin solundaki basamak ile sıfırları birkaç sayısal değeri biçimlendirir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Baştaki sıfırlar, belirli bir değere sahip bir sayısal değer yazma  
  
1.  Kaç tane baştaki sıfırlar sayısal bir değer olmasını istediğinizi belirleyin.  
  
2.  Sol tarafındaki unpadded sayısal dizesindeki ondalık basamak sayısını belirler. Bunu yapmak için:  
  
    1.  Bir sayının dize gösterimini bir ondalık noktası simgesi içerip içermediğini belirler.  
  
    2.  Ondalık noktası simgesi dahil ederseniz, Ondalık ayırıcının solundaki karakter sayısını belirler.  
  
         veya  
  
         Ondalık noktası simgesi içermez, dizenin uzunluğunu belirler.  
  
3.  Sıfır yer tutucusu ("0") her baştaki sıfırları dizesinde görünmesi için kullanan ve varsayılan dizedeki her basamak temsil etmek için sıfır yer tutucu ya da basmak yer tutucusu ("#") kullanan bir özel biçim dizesi oluşturun.  
  
4.  Özel biçim dizesi bir parametre olarak ya da sayının tedarik `ToString(String)` yöntemi veya bileşik biçimlendirmeyi destekleyen bir yöntem.  
  
 Aşağıdaki örnek iki sıfır ekleyerek doldurur <xref:System.Double> değerlerle beş baştaki sıfırlar.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
- [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
