---
title: 'Nasıl yapılır: Bir struct geçirme ve bir yöntem C# programlama kılavuzuna sınıf başvurusu geçirme arasındaki farkı öğrenin'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 889e1f5719e094d02f0cc27256e1c430ffce0b8e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596791"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Nasıl yapılır: Bir struct geçirme ve bir yönteme sınıf başvurusu geçirme arasındaki farkı öğrenin (C# Programlama Kılavuzu)
Aşağıdaki örnek bir [yapının](../../language-reference/keywords/struct.md) bir yönteme nasıl geçtiğini gösterir bir yönteme nasıl bir [sınıf](../../language-reference/keywords/class.md) örneği geçirmekten farklıdır. Örnekte, bağımsız değişkenlerin (struct ve sınıf örneği) her ikisi de değere göre geçirilir ve her iki yöntem de bağımsız değişkenin bir alanının değerini değiştirir. Ancak, bir yapı geçirdiğinizde geçirilen özellikler, bir sınıfın örneğini geçirdiğinizde geçirilen verilerden farklı olduğundan, iki yöntemin sonuçları aynı değildir.  
  
 Bir struct bir [değer türü](../../language-reference/keywords/value-types.md)olduğundan, bir yapıya [değere göre](./passing-value-type-parameters.md) bir yönteme geçirdiğinizde, yöntemi struct bağımsız değişkeninin bir kopyası üzerinde alır ve çalışır. Yöntemi çağıran yöntemde orijinal yapıya erişemez ve bu nedenle herhangi bir şekilde değiştirilemez. Yöntemi yalnızca kopyayı değiştirebilir.  
  
 Bir sınıf örneği, bir değer türü değil [başvuru türüdür](../../language-reference/keywords/reference-types.md). Bir [başvuru türü değere göre](./passing-reference-type-parameters.md) bir yönteme geçirildiğinde, yöntemi sınıf örneğine başvurunun bir kopyasını alır. Diğer bir deyişle, yöntemi örneğinin bir kopyasını değil, örneğin adresinin bir kopyasını alır. Çağıran yöntemdeki sınıf örneği bir adrese sahiptir, çağrılan yöntemdeki parametresi adresin bir kopyasına sahiptir ve her iki adres de aynı nesneye başvurur. Parametresi yalnızca adresin bir kopyasını içerdiğinden, çağrılan yöntem çağıran yöntemde sınıf örneğinin adresini değiştiremiyor. Ancak çağrılan yöntem, hem özgün adresin hem de kopyalama başvurusunun sınıf üyelerine erişmek için adresini kullanabilir. Çağrılan yöntem bir sınıf üyesini değiştirirse, çağıran yöntemdeki özgün sınıf örneği de değişir.  
  
 Aşağıdaki örnek çıktıda fark gösterilmektedir. Sınıf örneği `willIChange` alanının değeri, metodu, sınıf örneğinin belirtilen alanını bulmak için parametresindeki adresi kullandığından `ClassTaker` yöntemi çağrısıyla değiştirilir. Bağımsız değişkenin değeri, kendi adresinin bir kopyası değil, yapısının bir kopyası olduğundan, çağırma yöntemindeki `StructTaker` yapının alanı,yöntemiçağrısıyladeğiştirilmez.`willIChange` `StructTaker`kopyayı değiştirir ve çağrısı `StructTaker` tamamlandığında kopya kaybedilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yapılar](./structs.md)
- [Parametreleri Geçirme](./passing-parameters.md)
