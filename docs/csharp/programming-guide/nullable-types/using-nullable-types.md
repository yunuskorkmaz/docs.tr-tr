---
title: "Boş Değer Atanabilir Türleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a>Boş Değer Atanabilir Türleri Kullanma (C# Programlama Kılavuzu)
Boş değer atanabilir türleri bir temel alınan tür ve ek bir tüm değerleri temsil eden [null](../../../csharp/language-reference/keywords/null.md) değeri. Boş değer atanabilir türler iki yoldan biriyle bildirilir:  
  
 `System.Nullable<T> variable`  
  
 veya  
  
 `T? variable`  
  
 `T`boş değer atanabilir tür temel türde değil. `T`olması dahil herhangi bir değer türü `struct`; bir başvuru türü olamaz.  
  
 Boş değer atanabilir bir tür kullandığınızda, bir örnek için nasıl sıradan bir Boolean değişken iki değerlere sahip olabilir göz önünde bulundurun: true ve false. "Tanımsız" belirten değer yoktur. Birçok programlama uygulamalarda değişkenleri tanımlanmamış bir durumda oluşabilir etkileşimleri, özellikle veritabanı. Örneğin, bir veritabanında bir alan true veya false değerleri içerebilir, ancak hiçbir değer hiç ayrıca içerebilir. Başvuru türleri benzer şekilde, ayarlanabilir `null` bunlar başlatılmaz belirtmek için.  
  
 Bu farklılığa fazladan programlama iş durumu bilgileri, özel değerler ve benzeri kullanımını depolamak için kullanılan ek değişkenlerle oluşturabilirsiniz. Boş değer atanabilir tür değiştiricisi tanımlanmamış bir değere gösteren değer türü değişkenleri oluşturmak üzere C# sağlar.  
  
## <a name="examples-of-nullable-types"></a>Boş değer atanabilir türler örnekleri  
 Herhangi bir değer türü null olabilir bir tür için temel olarak kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Boş değer atanabilir türler üyeleri  
 Boş değer atanabilir bir tür her örneğinin iki genel salt okunur özellikler vardır:  
  
-   `HasValue`  
  
     `HasValue`tür `bool`. Ayarlanır `true` değişkeni boş olmayan bir değer içerdiğinde.  
  
-   `Value`  
  
     `Value`temel alınan türü olarak aynı türde değil. Varsa `HasValue` olan `true`, `Value` anlamlı bir değer içeriyor. Varsa `HasValue` olan `false`, erişilirken `Value` özel durum oluşturacak bir <xref:System.InvalidOperationException>.  
  
 Bu örnekte, `HasValue` üye değişkeni bir değeri içerip görüntülenecek denemeden önce test etmek için kullanılır.  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 İçin bir değer sınama aşağıdaki örnekteki yapılabilir:  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>Açık dönüşümler  
 Açıkça bir cast veya kullanarak normal bir türe boş değer atanabilir bir tür atanabilecek `Value` özelliği. Örneğin:  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 İki veri türleri arasında kullanıcı tanımlı bir dönüştürme tanımlanmışsa, bu veri türlerini boş değer atanabilir sürümleriyle aynı dönüştürme de kullanılabilir.  
  
## <a name="implicit-conversions"></a>Örtük dönüşümler  
 Boş değer atanabilir türde bir değişken ayarlanabilir null ile `null` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 Bir sıradan türünden null olabilir bir tür dönüştürme örtük.  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>İşleçler  
 Ayrıca önceden tanımlanmış birli ve ikili işleç ve değer türleri için mevcut kullanıcı tanımlı işleçler boş değer atanabilir türleri tarafından kullanılabilir. Bu işleçlere işlenenler null bir null değer oluşturmaz; Aksi takdirde işleci sonucu hesaplamak için kapsanan değeri kullanır. Örneğin:  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Boş değer atanabilir türler birinin değeri null ise ve diğeri değilse boş değer atanabilir türler ile karşılaştırmaları gerçekleştirdiğinizde, tüm karşılaştırmaları için değerlendirin `false` dışında `!=` (eşit değildir). Belirli bir karşılaştırma döndürdüğünden varsayımında değil önemlidir `false`, aksi durumda döndürür `true`. Aşağıdaki örnekte, 10 değerinden daha büyük değildir ve null değerine eşit. Yalnızca `num1 != num2` değerlendiren `true`.  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Her ikisi de null iki boş değer atanabilir türler bir eşitlik karşılaştırması değerlendiren `true`.  
  
## <a name="the--operator"></a>?? İşleç  
 `??` İşleci, null atanabilir bir tür null türüne atandığında, döndürülen varsayılan bir değer tanımlar.  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Bu işleç birden çok boş değer atanabilir türler ile de kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>Bool? türü  
 `bool?` Boş değer atanabilir tür üç farklı değerler içerebilir: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ve [null](../../../csharp/language-reference/keywords/null.md). Bool atama hakkında daha fazla bilgi için? bool için bkz: [nasıl yapılır: güvenli bir şekilde bool dönüştürme? değerinden bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Boş değer atanabilir Boole değerlerini SQL'de kullanılan Boole değişken türü gibidir. Tarafından üretilen sonuçları emin olmak için `&` ve `|` işleçleri üç değerli Boole türü ile tutarlı SQL'de aşağıdaki önceden tanımlanmış işleçleri sağlanır:  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 Bu işleçlere sonuçları aşağıdaki tabloda listelenmiştir:  
  
|X|y|x ve y|x &#124; y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Boş değer atanabilir türleri kutulama](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [Boş değer atanabilen değer türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
