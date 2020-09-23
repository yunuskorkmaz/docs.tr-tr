---
title: 'Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 268daf333dc5463e5436304cec188a9e6d477166
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077130"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)

Farklı veri türleri üzerinde özdeş işlevsellik sağlayan nesneler oluşturabileceğiniz bir sınıf tanımlayabilirsiniz. Bunu yapmak için tanımda bir veya daha fazla *tür parametresi* belirtirsiniz. Sınıf daha sonra çeşitli veri türlerini kullanan nesneler için bir şablon işlevi görebilir. Bu şekilde tanımlanan bir sınıfa *Genel sınıf*denir.  
  
 Genel bir sınıf tanımlamanın avantajı bunu yalnızca bir kez tanımlamanız, kodunuzun çok çeşitli veri türlerini kullanan birçok nesne oluşturmak için bunu kullanmasını sağlayabilirsiniz. Bu, sınıfının türüyle tanımlanması gerekenden daha iyi performans elde ediyor `Object` .  
  
 Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Bir tür parametresiyle bir sınıf tanımlamak için  
  
1. Sınıfı normal şekilde tanımlayın.  
  
2. `(Of` *typeparameter* `)` Bir tür parametresi belirtmek için sınıf adından hemen sonra typeparameter ekleyin.  
  
3. Birden fazla tür parametreye sahipseniz, parantez içinde virgülle ayrılmış bir liste oluşturun. Anahtar sözcüğünü tekrarlamayın `Of` .  
  
4. Kodunuz basit atama haricinde bir tür parametresinde işlemler gerçekleştiriyorsa, `As` bir veya daha fazla *kısıtlama*eklemek için bu tür parametresini yan tümcesiyle birlikte izleyin. Bir kısıtlama, bu tür parametresi için sağlanan türün aşağıdakiler gibi bir gereksinime uygun olmasını sağlar:  
  
    - Kodunuzun gerçekleştirdiği gibi bir işlemi destekler `>`  
  
    - , Kodunuzun eriştiği, yöntemi gibi bir üyeyi destekler  
  
    - Parametresiz bir Oluşturucu sunar  
  
     Herhangi bir kısıtlama belirtmezseniz, kodunuzun kullanabileceği tek işlemler ve Üyeler [nesne veri türü](../../../language-reference/data-types/object-data-type.md)tarafından desteklenenler olabilir. Daha fazla bilgi için bkz. [tür listesi](../../../language-reference/statements/type-list.md).  
  
5. Sağlanan türle belirtilecek her sınıf üyesini tanımlayın ve bunu bildirin `As` `typeparameter` . Bu iç depolama, yordam parametreleri ve dönüş değerleri için geçerlidir.  
  
6. Kodunuzun yalnızca, sağlayatabileceği herhangi bir veri türü tarafından desteklenen işlemler ve Yöntemler kullandığından emin olun `itemType` .  
  
     Aşağıdaki örnek, çok basit bir listeyi yöneten bir sınıfı tanımlar. İç dizide listesini barındırır `items` ve using kodu liste öğelerinin veri türünü bildirebilir. Parametreli bir Oluşturucu, kodunun üst sınırı ayarlamasına olanak tanır `items` ve parametresiz Oluşturucu bunu 9 ' a (Toplam 10 öğe için) ayarlar.  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     ' Dan bir sınıf, bir değer listesi tutan `simpleList` başka bir `Integer` sınıf ve değerleri tutmak için başka bir sınıf bildirebilirsiniz `String` `Date` . Liste üyelerinin veri türü dışında, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.  
  
     Using kodunun sağladığı tür bağımsız değişkeni `itemType` `Boolean` , ya da `Double` , bir yapı, bir numaralandırma veya uygulamanızın tanımladığı bir sınıf türü gibi bir iç tür olabilir.  
  
     Sınıfı aşağıdaki kodla test edebilirsiniz `simpleList` .  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Visual Basic genel türler](generic-types.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)
- [Durumunu](../../../language-reference/statements/of-clause.md)
- [Tür Listesi](../../../language-reference/statements/type-list.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](how-to-use-a-generic-class.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
