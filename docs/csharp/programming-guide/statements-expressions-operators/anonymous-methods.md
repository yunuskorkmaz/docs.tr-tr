---
title: "Anonim Yöntemler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96e78257c5aab84562cd8cdb336bb5a91ba59534
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="anonymous-methods-c-programming-guide"></a>Anonim Yöntemler (C# Programlama Kılavuzu)
Sürümlerinde C# 2.0, bildirmek için tek yolu önce bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) kullanılmasıydır [yöntemleri adlı](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). C# 2.0 anonim yöntemler açıklanmıştır ve C# 3.0 ve sonraki sürümlerinde, lambda ifadeleri anonim yöntemler satır içi kod yazmak için tercih edilen yol geçersiz kılar. Ancak, bu konudaki anonim yöntemler hakkında bilgi lambda ifadeleri için de geçerlidir. Adsız bir yöntem lambda ifadelerini bulunamadı işlevselliği sağlayan bir durumda değil. Anonim yöntemler parametre listesi atlamak etkinleştirin. Bu, adsız bir yöntem imzaları çeşitli temsilcilere dönüştürülebilir anlamına gelir. Bu lambda ifadeleri ile mümkün değildir. Lambda ifadeleri özellikle hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Anonim yöntemler oluşturma kod bloğu temsilci parametre olarak geçirmek için temel bir yoludur. Aşağıda, iki örnek verilmiştir:  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Anonim yöntemler kullanarak ek yükü temsilciler örneği ayrı bir yöntem oluşturmak olmadığından kodlama azaltın.  
  
 Örneğin, bir temsilci yerine kod bloğu bir yöntem oluşturmak zorunda kalmadan bir durumda kullanışlı olabilir belirtme gereksiz bir ek yük görünebilir. Yeni bir iş parçacığı başlattığınızda güzel bir örnek olacaktır. Bu sınıf, bir iş parçacığı oluşturur ve ayrıca iş parçacığı temsilci için ek bir yöntem oluşturmadan yürütülen kodu içerir.  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim bir yöntemin parametrelerini kapsamı *yöntem bloğu anonim*.  
  
 Atlama deyimi gibi sağlamak için bir hata olduğunu [goto](../../../csharp/language-reference/keywords/goto.md), [sonu](../../../csharp/language-reference/keywords/break.md), veya [devam](../../../csharp/language-reference/keywords/continue.md), hedef blok dışında ise adsız yöntem bloğu içinde. Ayrıca bir atlama deyimi gibi sağlamak için bir hata olduğunu `goto`, `break`, veya `continue`, hedef blok içinde ise adsız yöntem bloğu dışında.  
  
 Yerel değişkenleri ve parametreleri, kapsam içeren bir anonim yöntem bildirimi adlı *dış* anonim yöntemin değişkenlerinin. Örneğin, aşağıdaki kod parçası olarak `n` bir dış değişken:  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Dış değişken başvuru `n` olarak kabul edilir *yakalanan* temsilci oluşturulduğunda. Anonim yöntemler başvuru temsilcileri atık toplama için uygun olana kadar yerel değişkenler, yakalanan bir değişken ömrü genişletir.  
  
 Adsız bir yöntem erişemiyor [içinde](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) bir dış kapsam parametreleri.  
  
 Güvenli olmayan kod içinde erişilebilir *yöntem bloğu anonim*.  
  
 Anonim yöntemler sol tarafında verilmez [olan](../../../csharp/language-reference/keywords/is.md) işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir temsilci başlatmasını iki yolu gösterir:  
  
-   Temsilci anonim yöntemi ile ilişkilendirme.  
  
-   Temsilci adlandırılmış bir yöntem ile ilişkilendirme (`DoWork`).  
  
 Temsilci çağrıldığında her durumda, bir ileti görüntülenir.  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
