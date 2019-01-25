---
title: Anonim yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: ba80626a777f9f2d813694abf3deda0ef0c93606
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732528"
---
# <a name="anonymous-methods-c-programming-guide"></a>Anonim Yöntemler (C# Programlama Kılavuzu)
C# ' ın sürümlerinde 2.0, tek yolu bildirmek için önce bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) kullanılmasıydır [yöntemleri adlı](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). Anonim yöntemler C# 2.0 kullanılmaya ve C# 3.0 ve sonraki sürümlerinde, lambda ifadeleri anonim yöntemler satır içi kod yazmak için tercih edilen yol geçersiz kılar. Ancak, bu konudaki anonim yöntemler hakkında bilgi, lambda ifadeleri için de geçerlidir. Anonim bir yöntem lambda ifadelerinde bulunamadı işlevselliği sağlayan bir durum yoktur. Anonim yöntemler parametre listesini atlamak etkinleştirin. Bu, anonim bir yöntem imzaları çeşitli temsilcilere dönüştürülebilir anlamına gelir. Bu, lambda ifadeleri ile mümkün değildir. Özellikle, lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Anonim yöntemler oluşturmak bir kod bloğu bir temsilcinin parametre olarak geçmesine aslında bir yoludur. İki örnek aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Anonim yöntemler kullanarak, ek yükü ayrı bir yöntem oluşturmak olmadığı için temsilciler örnekleme kodlama azaltın.  
  
 Örneğin, bir kod bloğu bir Temsilcinizin yerine bir yöntem oluşturmak zorunda kalmadan bir durumda kullanışlı olabilir belirtme gereksiz bir ek yük görünebilir. Yeni bir iş parçacığı başlatıldığında, iyi bir örnek olacaktır. Bu sınıf, bir iş parçacığı oluşturur ve ayrıca ek bir yöntem için temsilci oluşturmak zorunda kalmadan iş parçacığı yürütülen kod içerir.  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim bir yöntem parametrelerini kapsamı *yöntem bloğu anonim*.  
  
 Bir atlama deyimi sahip bir hata olduğunu [goto](../../../csharp/language-reference/keywords/goto.md), [sonu](../../../csharp/language-reference/keywords/break.md), veya [devam](../../../csharp/language-reference/keywords/continue.md), hedefi blok dışındaysa ise anonim yöntem bloğu içinde. Ayrıca bir atlama deyimi sahip bir hata olduğunu `goto`, `break`, veya `continue`, hedef blok içinde ise anonim yöntem bloğu dışında.  
  
 Yerel değişkenleri ve parametreleri içeren bir anonim yöntem bildiriminde kapsamı adlı *dış* anonim yöntemin değişkenleri. Örneğin, aşağıdaki kod kesimi içinde `n` dış bir değişkendir:  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Bir dış değişkenine başvuru `n` olduğu söylenir *yakalanan* temsilci oluşturulduğunda. Anonim yöntemler başvuran temsilcileri çöp toplama işlemi için uygun olana kadar yerel değişkenler farklı olarak, yakalanan bir değişkenin ömrü genişletir.  
  
 Anonim bir yöntem erişemiyor [içinde](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) bir dış kapsam parametreleri.  
  
 Güvenli olmayan kod içinde erişilebilir *yöntem bloğu anonim*.  
  
 Anonim yöntemler sol tarafında verilmez [olduğu](../../../csharp/language-reference/keywords/is.md) işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir temsilci örnekleme iki yolu gösterir:  
  
-   Temsilci, adsız bir yöntem ile ilişkilendirme.  
  
-   Temsilci adlandırılmış bir yöntem ile ilişkilendirme (`DoWork`).  
  
 Temsilci çağrıldığında her durumda, bir ileti görüntülenir.  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
