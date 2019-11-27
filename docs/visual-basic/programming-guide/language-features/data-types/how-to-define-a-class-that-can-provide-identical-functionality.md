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
ms.openlocfilehash: d80623d9e55358d37aa45f11f1525c80a09b91a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350050"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)
Farklı veri türleri üzerinde özdeş işlevsellik sağlayan nesneler oluşturabileceğiniz bir sınıf tanımlayabilirsiniz. Bunu yapmak için tanımda bir veya daha fazla *tür parametresi* belirtirsiniz. Sınıf daha sonra çeşitli veri türlerini kullanan nesneler için bir şablon işlevi görebilir. Bu şekilde tanımlanan bir sınıfa *Genel sınıf*denir.  
  
 Genel bir sınıf tanımlamanın avantajı bunu yalnızca bir kez tanımlamanız, kodunuzun çok çeşitli veri türlerini kullanan birçok nesne oluşturmak için bunu kullanmasını sağlayabilirsiniz. Bu, `Object` türü ile sınıfının tanımlanmasıyla daha iyi performansa neden olur.  
  
 Sınıfların yanı sıra genel yapıları, arabirimleri, yordamları ve temsilcileri de tanımlayabilir ve kullanabilirsiniz.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Bir tür parametresiyle bir sınıf tanımlamak için  
  
1. Sınıfı normal şekilde tanımlayın.  
  
2. Bir tür parametresi belirtmek için sınıf adından hemen sonra `(Of` *typeparameter*`)` ekleyin.  
  
3. Birden fazla tür parametreye sahipseniz, parantez içinde virgülle ayrılmış bir liste oluşturun. `Of` anahtar sözcüğünü tekrarlamayın.  
  
4. Kodunuz basit atama haricinde bir tür parametresinde işlemler gerçekleştiriyorsa, bir veya daha fazla *kısıtlama*eklemek için bu tür parametresini bir `As` yan tümcesiyle izleyin. Bir kısıtlama, bu tür parametresi için sağlanan türün aşağıdakiler gibi bir gereksinime uygun olmasını sağlar:  
  
    - Kodunuzun gerçekleştirdiği `>`gibi bir işlemi destekler  
  
    - , Kodunuzun eriştiği, yöntemi gibi bir üyeyi destekler  
  
    - Parametresiz bir Oluşturucu sunar  
  
     Herhangi bir kısıtlama belirtmezseniz, kodunuzun kullanabileceği tek işlemler ve Üyeler [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)tarafından desteklenenler olabilir. Daha fazla bilgi için bkz. [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5. Sağlanan bir türle bildirildiği her sınıf üyesini tanımlayın ve `typeparameter``As` bildirin. Bu iç depolama, yordam parametreleri ve dönüş değerleri için geçerlidir.  
  
6. Kodunuzun yalnızca `itemType`sağlayabileceğinizden herhangi bir veri türü tarafından desteklenen işlemler ve Yöntemler kullandığından emin olun.  
  
     Aşağıdaki örnek, çok basit bir listeyi yöneten bir sınıfı tanımlar. Bu, listenin iç dizi `items`barındırır ve using kodu, liste öğelerinin veri türünü bildirebilirler. Parametreli bir Oluşturucu, kodun `items`üst sınırı ayarlamasına olanak tanır ve parametresiz Oluşturucu bunu 9 (Toplam 10 öğe için) olarak ayarlar.  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     Bir `simpleList` `Integer` değerlerinin listesini, `String` değerlerinin listesini tutacak başka bir sınıfı ve `Date` değerleri tutmak için başka bir sınıf bildirebilirsiniz. Liste üyelerinin veri türü dışında, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.  
  
     `itemType` kullanan tür bağımsız değişkeni `Boolean` veya `Double`, bir yapı, sabit listesi ya da uygulamanızın tanımladığı bir tür sınıf gibi bir iç tür olabilir.  
  
     Sınıfı `simpleList` aşağıdaki kodla test edebilirsiniz.  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)
- [Durumunu](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Tür Listesi](../../../../visual-basic/language-reference/statements/type-list.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
