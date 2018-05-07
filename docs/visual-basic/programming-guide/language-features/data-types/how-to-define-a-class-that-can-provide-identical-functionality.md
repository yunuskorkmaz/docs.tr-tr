---
title: 'Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)'
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
ms.openlocfilehash: 3570a1c851bb8fead33f4cd208489c4ae087a68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama (Visual Basic)
Bir sınıf tanımlama öğesinden farklı veri türlerinde aynı işlevselliği sağlayan nesneleri oluşturabilirsiniz. Bunu yapmak için bir veya daha fazla belirttiğiniz *tür parametrelerindeki* tanımında. Sınıf çeşitli veri türlerini kullanan nesneler için bir şablon olarak hizmet verebilir. Bu şekilde tanımlanmış bir sınıf olarak adlandırılan bir *genel bir sınıf*.  
  
 Genel bir sınıf tanımlama avantajı, yalnızca bir kez tanımlayın ve kodunuzu çok çeşitli veri türleri kullanan çok sayıda nesne oluşturmak için kullanabilirsiniz olmasıdır. Bu sınıfı tanımlayan daha iyi performans sonuçları `Object` türü.  
  
 Sınıfları yanı sıra tanımlayabilir ve genel yapılar, arabirimler, yordamlar ve temsilciler kullanın.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Tür parametresi bir sınıfla tanımlamak için  
  
1.  Sınıf normal şekilde tanımlayın.  
  
2.  Ekleme `(Of` *typeparameter* `)` sonra hemen bir tür parametresi belirlemek için sınıf adı.  
  
3.  Birden fazla tür parametresi varsa parantez içinde virgülle ayrılmış bir liste olun. Yineleme `Of` anahtar sözcüğü.  
  
4.  Kodunuzu bir tür parametresi basit atama dışındaki işlemleri gerçekleştirirse, o tür parametresi ile izleyin bir `As` bir veya daha fazla eklemek için yan tümcesi *kısıtlamaları*. Bu tür parametresi için sağlanan türü aşağıdaki gibi bir gereksinimini karşılayan bir kısıtlama garanti eder:  
  
    -   Bir işlem gibi destekleyen `>`, kodunuzu gerçekleştiren  
  
    -   Kodunuzu erişen bir yöntem gibi bir üye destekler  
  
    -   Parametresiz bir kurucusu gösterir  
  
     Kısıtlamalar belirtmezseniz, yalnızca operations ve kodunuzu kullanabilirsiniz üyeleri tarafından desteklenen olanlardır [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Daha fazla bilgi için bkz: [türü listesinde](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Sağlanan türüyle belirtilecek olan her sınıf üyesi tanımlamak ve bildirirken `As` `typeparameter`. Bu, dahili depolama, parametreler ve dönüş değerleri için geçerlidir.  
  
6.  Kodunuzu, yalnızca operations ve sağlamak için herhangi bir veri türü tarafından desteklenen yöntemleri kullandığından emin olmanız `itemType`.  
  
     Aşağıdaki örnek çok basit bir liste yöneten bir sınıfı tanımlar. İç dizisinde listesini tutar `items`ve kod kullanarak veri türü liste öğelerini bildirebilirsiniz. Parametreli Oluşturucusu kullanılarak sağlar üst sınırının ayarlamak için kod `items`, ve bu ayarlar varsayılan oluşturucu ile 9 (için 10 öğe toplamı).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Öğesinden bir sınıf bildirme `simpleList` listesini tutmak için `Integer` değerleri, listesini tutmak için başka bir sınıf `String` değerleri ve başka tutmak için `Date` değerleri. Üyeleri listeleme veri türünü hariç, tüm bu sınıflardan oluşturulan nesneler aynı şekilde davranır.  
  
     Kod kullanarak tür bağımsız değişkeni için sağladığı `itemType` geçerli bir tür gibi olabilir `Boolean` veya `Double`, bir yapı, numaralandırma veya sınıf, uygulamanızın tanımlayan bir de dahil olmak üzere herhangi bir türde.  
  
     Sınıfı test `simpleList` aşağıdaki kod ile.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)  
 [,](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Tür Listesi](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
