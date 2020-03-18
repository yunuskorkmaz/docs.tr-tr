---
title: Bir yapıyı geçmekle bir yönteme sınıf başvurusu aktarmak arasındaki farkı nasıl anlarsın - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: a280a6df873d7c03c204bc5c86468e7e7298d723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673439"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Bir yapıyı geçmekle bir yönteme sınıf başvurusu geçmek arasındaki farkı nasıl anlarsın (C# Programlama Kılavuzu)
Aşağıdaki örnek, bir [struct'u](../../language-reference/builtin-types/struct.md) bir metyönteme geçirmenin [sınıf](../../language-reference/keywords/class.md) örneğini bir yönteme geçirmekten nasıl farklı olduğunu gösterir. Örnekte, bağımsız değişkenlerin her ikisi de (struct ve class instance) değere göre geçirilir ve her iki yöntem de bağımsız değişkenin bir alanının değerini değiştirir. Ancak, bir yapıyı geçtiğinizden geçenler, bir sınıfın örneğini geçtiğinizden farklı olduğundan, iki yöntemin sonuçları aynı değildir.  
  
 Yapı bir [değer türü](../../language-reference/builtin-types/value-types.md)olduğundan, [bir struct'u bir](./passing-value-type-parameters.md) yönteme göre değere göre geçtiğinde, yöntem yapı bağımsız değişkeninin bir kopyasını alır ve çalışır. Yöntem, arama yönteminde özgün yapıya erişimi yoktur ve bu nedenle hiçbir şekilde değiştiremez. Yöntem yalnızca kopyayı değiştirebilirsiniz.  
  
 Sınıf örneği bir [başvuru türüdür,](../../language-reference/keywords/reference-types.md)değer türü değildir. Bir başvuru türü değer olarak bir yönteme [geçirildiğinde,](./passing-reference-type-parameters.md) yöntem sınıf örneğine başvurunun bir kopyasını alır. Diğer bir süre, çağrılan yöntem örneğin adresinin bir kopyasını alır ve arama yöntemi örneğin özgün adresini korur. Arama yöntemindeki sınıf örneğinin bir adresi vardır, çağrılan yöntemdeki parametrede adresin bir kopyası vardır ve her iki adres de aynı nesneye başvurur. Parametre yalnızca adresin bir kopyasını içerdiğinden, çağrılan yöntem arama yönteminde sınıf örneğinin adresini değiştiremez. Ancak, çağrılan yöntem, hem özgün adreshem de adres başvurusu kopyası olan sınıf üyelerine erişmek için adres kopyasını kullanabilir. Çağrılan yöntem bir sınıf üyesini değiştirirse, arama yöntemindeki özgün sınıf örneği de değişir.  
  
 Aşağıdaki örneğin çıktısı farkı göstermektedir. Yöntem, sınıf `willIChange` örneğinin belirtilen alanını bulmak için `ClassTaker` parametredeki adresi kullandığından, sınıf örneğinin alanının değeri çağrı ile yönteme değiştirilir. Çağırma `willIChange` yöntemindeki yapının alanı, sözcük değeri, adresinin `StructTaker` bir kopyası değil, yapının bir kopyası olduğundan, çağrı yöntemiyle değiştirilmez. `StructTaker`kopyayı değiştirir ve çağrı `StructTaker` tamamlandığında kopya kaybolur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Parametreleri Geçirme](./passing-parameters.md)
