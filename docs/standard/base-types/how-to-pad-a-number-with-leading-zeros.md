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
ms.openlocfilehash: 8ce3b59db027ffebf616a035b018629cb7aed30c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma
"D" kullanarak bir tamsayı baştaki sıfırlarla ekleyebilirsiniz [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md) duyarlık Belirleyicisi ile. Tamsayı ve kayan nokta sayıları baştaki sıfırlarla kullanarak ekleyebileceğiniz bir [özel sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md). Bu konu, her iki yöntem sayıyı baştaki sıfırlarla paneli için nasıl kullanılacağını gösterir.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Baştaki sıfırlarla belirli bir süre için bir tamsayı doldurulacak  
  
1.  Tamsayı değeri görüntülemek istediğiniz basamak sayısı alt sınırını belirler. Tüm önde gelen basamak bu numarayı içerir.  
  
2.  Tamsayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.  
  
    -   Tamsayı ondalık bir değeri görüntülemek için arama kendi `ToString(String)` yöntemi ve geçişi dizesi "D*n*" değeri olarak `format` parametresi, burada *n* en az dize uzunluğu temsil eder.  
  
    -   Tamsayı bir onaltılık değer olarak görüntülemek için arama kendi `ToString(String)` yöntemi ve geçişi dizesi "X*n*" değeri olarak `format` parametresi, burada *n* minimum uzunluğu temsil eder dize.  
  
     Biçim dizesi bir yöntemde gibi kullanabilirsiniz <xref:System.String.Format%2A> veya <xref:System.Console.WriteLine%2A>, kullanan [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz karakter sıfırları ile birkaç tamsayı değerlerini biçimlendirir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Öndeki sıfırların belirli bir sayısı bir tamsayı doldurulacak  
  
1.  Kaç tane öndeki sıfırların istediğiniz görüntülemek için tamsayı değeri belirleyin.  
  
2.  Tamsayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin. Ondalık değer olarak biçimlendirme "D" standart biçim belirticisi kullanmanızı gerektirir; bir onaltılık değer olarak biçimlendirme "X" standart biçim belirticisi kullanmanızı gerektirir.  
  
3.  Tamsayı değerinin çağırarak unpadded sayısal dize uzunluğu belirlemek `ToString("D").Length` veya `ToString("X").Length` yöntemi.  
  
4.  Unpadded sayısal dize uzunluğu biçimlendirilmiş dizeye dahil etmek istediğiniz öndeki sıfırların sayısı ekleyin. Bu, toplam doldurulan dize uzunluğu tanımlar.  
  
5.  Tamsayı değerinin çağrısı `ToString(String)` yöntemi ve geçişi dizesi "D*n*" ondalık dizeleri ve "X*n*" onaltılık dizeler için burada *n* toplam temsil eder doldurulan dize uzunluğu. Aynı zamanda "D*n*" veya "X*n*" format dize bileşik biçimlendirme destekleyen bir yöntem.  
  
 Aşağıdaki örnek, bir tamsayı değeri beş baştaki sıfırlarla pads.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Baştaki sıfırlarla belirli bir süre için sayısal bir değer yazma  
  
1.  Ondalık konumun soluna kaç basamağa sahip üzere numarasını dize gösterimini istediğinizi belirleyin. Bu toplam basamak sayısı önde gelen tüm sıfırları içerir.  
  
2.  En az sayıda sıfır göstermek için sıfır yer tutucusu ("0") kullanan bir özel sayısal biçim dizesi tanımlayın.  
  
3.  Sayının çağrı `ToString(String)` yöntemi ve özel biçim dizesi geçirin. Bileşik biçimlendirme destekleyen bir yöntemle özel biçim dizesi de kullanabilirsiniz.  
  
 Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz basamağa ondalık konumun soluna sıfırları ile birkaç sayısal değerleri biçimlendirir.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Öndeki sıfırların belirli sayıda sayısal bir değer yazma  
  
1.  Kaç tane öndeki sıfırların sayısal değerin olmasını istediğinizi belirleyin.  
  
2.  Sol tarafındaki unpadded sayısal dize ondalık basamak sayısını belirler. Bunu yapmak için:  
  
    1.  Bir sayı dize gösterimini bir ondalık ayırıcısı simge içerip içermediğini belirler.  
  
    2.  Bir ondalık ayırıcısı simge dahil ederseniz, Ondalık ayırıcının solundaki karakter sayısını belirler.  
  
         -veya-  
  
         Bir ondalık ayırıcısı simge içermiyorsa dizenin uzunluğunu belirler.  
  
3.  Her basamakta varsayılan dizesini temsil etmek için sıfır yer tutucusu veya basamak yer tutucusu ("#") kullanan ve sıfır yer tutucusu ("0") her öndeki sıfırların dizesinde görünmesi kullanan özel bir biçim dizesi oluşturun.  
  
4.  Özel biçim dizesi parametre olarak ya da sayının tedarik `ToString(String)` yöntemi veya bileşik biçimlendirme destekleyen bir yöntem.  
  
 Aşağıdaki örnekte iki pads <xref:System.Double> beş baştaki sıfırlarla değerleri.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Bileşik Biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)
