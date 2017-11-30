---
title: "Nasıl yapılır: Tür için Değer Eşitliği Tanımlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 933be6aa27b5720a9a9d8d7b45e1eed73f9cd60b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Nasıl yapılır: Tür için Değer Eşitliği Tanımlama (C# Programlama Kılavuzu)
Sınıfta veya yapı tanımladığınızda, türü için değer eşitliği (veya eşdeğer) özel bir tanımı oluşturmak için bir anlam olup olmadığını karar. Genellikle, değer eşitliği bazı sıralama koleksiyona eklenecek nesne türü beklenirken ya da kendi birincil amacı, alan veya özellikler kümesi depolamaktır uygulayın. Tüm alanlar ve türü özelliklerinde karşılaştırması için değer eşitliği tanımınız temel ya da bir alt tanımını temel alabilir. Ancak her iki durumda da ve sınıflar ve yapılar, uygulamanızı eşdeğer beş garanti izlemelisiniz:  
  
1.  x`Equals`(x) döndürür `true.` bu Yansımalı özelliği olarak adlandırılır.  
  
2.  x`Equals`y aynı değeri döndürür (y)`Equals`(x). Bu, simetrik özelliği adı verilir.  
  
3.  varsa (x`Equals`(y) & & y`Equals`(z)) döndürür `true`, ardından x`Equals`(z) döndürür `true`. Bu, geçişli özellik adı verilir.  
  
4.  Art arda çağırmaları x.`Equals`nesneleri başvurulan x ve y değiştirilmez sürece aynı değeri (y) döndürür.  
  
5.  x`Equals`(boş) döndürür `false`. Ancak, null. Equals(null) bir özel durum oluşturur; Yukarıdaki iki kural numara uyma değil.  
  
 Öğesinden devralınan değer eşitliği varsayılan uyarlamasını önceden tanımladığınız yapısı sahip <xref:System.ValueType?displayProperty=nameWithType> , geçersiz kılma <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi. Bu uygulama yansıtma alanları ve türü özelliklerinde incelemek için kullanır. Bu uygulama doğru sonuçlar üretir karşın, bu özellikle türü için yazma özel bir uygulama ile karşılaştırıldığında yavaştır.  
  
 Sınıflar ve yapılar için değer eşitliği uygulama ayrıntıları farklıdır. Ancak, sınıflar ve yapılar aynı temel adımları eşitlik uygulamak üzere gerektirir:  
  
1.  Geçersiz kılma [sanal](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi. Çoğu durumda, uygulamanızı `bool Equals( object obj )` türüne özgü yalnızca çağırmalıdır `Equals` uygulamasıdır yöntemi <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi. (Bkz. 2. adım.)  
  
2.  Uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> türüne özgü sağlayarak arabirimi `Equals` yöntemi. Gerçek eşdeğer karşılaştırma gerçekleştirildiği budur. Örneğin, yalnızca bir veya iki alanları türünüz karşılaştırarak eşitliği tanımlama karar verebilirsiniz. Özel durumlar oluşturmayın `Equals`. Yalnızca sınıflar için: Bu yöntem yalnızca sınıfında tanımlanan alanların incelemeniz gerekir. Bunu çağırmalıdır `base.Equals` taban sınıf içinde alanlar incelemek için. (Tür doğrudan devralıyorsa bunu <xref:System.Object>, çünkü <xref:System.Object> uyarlamasını <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> bir referans eşitlik denetimi gerçekleştirir.)  
  
3.  İsteğe bağlı ancak önerilir: aşırı [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) ve [! =](../../../csharp/language-reference/operators/not-equal-operator.md) işleçler.  
  
4.  Geçersiz kılma <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> böylece aynı üretmek değer eşitliği sahip iki nesnesi karma kodu.  
  
5.  İsteğe bağlı: "büyüktür" veya "küçüktür" tanımlarını desteklemek için uygulama <xref:System.IComparable%601> arabirim türünüz için ve ayrıca aşırı [ <= ](../../../csharp/language-reference/operators/less-than-equal-operator.md) ve [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) işleçleri .  
  
 İzleyen ilk örnek bir sınıf uygulama gösterir. İkinci örnek yapı uygulamasını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıfı (başvuru türü) değer eşitliği uygulamak gösterilmiştir.  
  
 [!code-csharp[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 Sınıfları (başvuru türleri), her ikisi de varsayılan uygulaması <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemleri bir referans eşitlik karşılaştırması değeri eşitlik kontrolüne gerçekleştirir. Bir uygulayan sanal yöntemini geçersiz kılar, amaç değeri eşitlik semantiği vermek için değildir.  
  
 `==` Ve `!=` işleçleri sınıfı bunları aşırı yüklemediği olsa bile sınıflarıyla kullanılabilir. Ancak, varsayılan davranışı referans eşitlik kontrolüne gerçekleştirmektir. Aşırı yükleme varsa bir sınıftaki `Equals` yöntemi, aşırı `==` ve `!=` işleçleri, ancak gerekli değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yapı (değer türü) için değer eşitliği uygulanacak gösterilmektedir:  
  
 [!code-csharp[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Yapılar, varsayılan uygulaması için <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (geçersiz kılınan sürümünde olduğu <xref:System.ValueType?displayProperty=nameWithType>) her alan türü değerleri karşılaştırmak için yansıma kullanarak bir değer eşitlik denetimi gerçekleştirir. Ne zaman bir uygulayan geçersiz kılmaları sanal `Equals` yapı yönteminde amacı olan değer eşitlik kontrolüne gerçekleştirmenin daha verimli bir yol sağlar ve isteğe bağlı olarak bazı alt yapı biriminin alan veya özellikleri kümesi üzerinde karşılaştırma taban.  
  
 [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) Ve [! =](../../../csharp/language-reference/operators/not-equal-operator.md) yapısı açıkça bunları overloads sürece işleçleri üzerinde bir yapı çalışamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşitlik karşılaştırmaları](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)
