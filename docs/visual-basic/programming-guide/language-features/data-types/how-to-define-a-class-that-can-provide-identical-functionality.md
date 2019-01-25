---
title: 'Nasıl yapılır: (Visual Basic) farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama'
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
ms.openlocfilehash: 9f6faf7b9ba2338784fda2cec2efc2b3991d415e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667485"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Nasıl yapılır: (Visual Basic) farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama
Bir sınıf tanımlayabilir, farklı veri türlerinde aynı işlevselliği sağlayan nesneleri oluşturabileceğiniz öğesinden. Bunu yapmak için bir veya daha fazla belirttiğiniz *tür parametrelerindeki* tanımında. Sınıf çeşitli veri türlerini kullanan nesneler için bir şablon olarak hizmet verebilir. Bu şekilde tanımlanan bir sınıfa bir *genel sınıf*.  
  
 Genel bir sınıf tanımlamanın yararı, yalnızca bir kez tanımlayın ve kodunuzu çok çeşitli veri türleri kullanan birçok nesneler oluşturmak için kullanabilirsiniz ' dir. Sınıf ile daha iyi performans sonuçlanır `Object` türü.  
  
 Sınıflara ek olarak tanımlayabilir ve genel yapılar, arabirimler, yordamları ve temsilciler kullanın.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Bir tür parametresi ile bir sınıf tanımlamak için  
  
1.  Normal bir şekilde tanımlayan sınıf.  
  
2.  Ekleme `(Of` *typeparameter* `)` sonrasında hemen bir tür parametresi belirtmek için sınıf adı.  
  
3.  Birden fazla tür parametresi varsa, parantez içinde virgülle ayrılmış bir liste olun. Yineleme `Of` anahtar sözcüğü.  
  
4.  Kodunuzu basit atama dışında bir tür parametresi üzerinde işlemler gerçekleştirirse, o tür parametreyle izleyin bir `As` yan tümcesi bir veya daha fazla eklemek için *kısıtlamaları*. Kısıtlama türü, tür parametresi için sağlanan aşağıdaki gibi bir gereksinimi karşılayan garanti eder:  
  
    -   Bir işlem gibi destekleyen `>`, kodunuzu gerçekleştiren  
  
    -   Kodunuzu erişen bir yöntemi gibi bir üye destekler  
  
    -   Parametresiz bir Oluşturucu  
  
     Kısıtlamalardan belirtmezseniz, yalnızca işlemler ve kodunuzu kullanabileceğiniz üyeleri tarafından desteklenen olanlardır [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Daha fazla bilgi için [tür listesi](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Sağlanan türüyle belirtilecek olan her sınıf üyesi tanımlamak ve bildirirken `As` `typeparameter`. Bu, iç depolama alanı, yordam parametreleri ve dönüş değerleri için geçerlidir.  
  
6.  Kodunuzun kullandığı yalnızca işlemler ve için sağlayabilirler herhangi bir veri türü tarafından desteklenen yöntemleri mutlaka `itemType`.  
  
     Aşağıdaki örnek çok basit bir listeyi yöneten bir sınıf tanımlar. İç dizide listesini tutar `items`ve kod kullanarak liste öğelerini veri türünü bildirebilirsiniz. Parametreli bir kurucu kullanarak sağlayan çokluğun ayarlamak üzere kod `items`, ve varsayılan oluşturucu, bu ayarlar 9 (için toplam 10 öğe).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Bir sınıftan bildirebilirsiniz `simpleList` listesini tutmak için `Integer` değerleri, bir listesi için başka bir sınıf `String` değerleri ve başka tutacak `Date` değerleri. Üyeleri listele veri türünü hariç, tüm bu sınıflardan oluşturulan nesnelerin aynı şekilde davranır.  
  
     Kod kullanarak tür bağımsız değişkeni için sağladığı `itemType` iç bir tür gibi olabilir `Boolean` veya `Double`, bir yapı, bir numaralandırma veya sınıf, uygulamanızı tanımlayan bir dahil olmak üzere herhangi bir türde.  
  
     Sınıf sınayabilirsiniz `simpleList` aşağıdaki kod ile.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../standard/language-independence-and-language-independent-components.md)
- [,](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Tür Listesi](../../../../visual-basic/language-reference/statements/type-list.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
