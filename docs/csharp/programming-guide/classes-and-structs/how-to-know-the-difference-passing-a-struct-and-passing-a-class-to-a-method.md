---
title: "Nasıl yapılır: Yapı Geçirme ile Metoda Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b989c3cefe72c6c17d10dd91005dcecbfc84e389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Nasıl yapılır: Yapı Geçirme ile Metoda Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme (C# Programlama Kılavuzu)
Aşağıdaki örnekte nasıl geçirme gösteren bir [yapısı](../../../csharp/language-reference/keywords/struct.md) bir yönteme geçirme öğesinden farklı bir [sınıfı](../../../csharp/language-reference/keywords/class.md) bir yönteme örnek. Örnekte, bağımsız değişkenler (yapısı ve sınıf örneği) her ikisi de değeriyle geçirilir ve her iki yöntem bağımsız değişkeninin bir alanın değerini değiştirin. Yapı geçirdiğinizde ne geçirilen bir sınıfın örneğini geçirdiğinizde ne geçirilen gelen değiştiğinden ancak, iki yöntem sonuçlarını aynı değildir.  
  
 Bir yapı olduğundan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md), ne zaman, [yapı değeriyle geçirmek](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) bir yöntem için yöntemi alır ve yapı bağımsız değişkeni bir kopyası üzerinde çalışır. Yöntemi arama yönteminde özgün yapısı hiçbir erişimi vardır ve bu nedenle herhangi bir şekilde değiştiremezsiniz. Yöntem yalnızca kopya değiştirebilirsiniz.  
  
 Sınıf örneği bir [başvuru türüne](../../../csharp/language-reference/keywords/reference-types.md), değer türü. Zaman [bir başvuru türü değeri tarafından geçirilen](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) bir yönteme yöntemi sınıf örneği referansı kopyasını alır. Diğer bir deyişle, yöntem adresi olmayan örneğin kopyası örneğinin bir kopyasını alır. Arama yönteminde sınıf örneği bir adresi olduğundan, çağrılan yöntem parametresinde adresi bir kopyası bulunur ve her iki adres aynı nesneye başvuruyor. Parametresi yalnızca bir kopya adresinin içerdiğinden, çağrılan yöntemin arama yönteminde sınıf örneğinin adresi değiştiremezsiniz. Ancak, çağrılan yöntemin adresi özgün adresini ve kopya başvuru sınıf üyeleri erişmek için kullanabilirsiniz. Çağrılan yöntemi bir sınıf üyesi değişirse, özgün sınıf örneği arama yönteminde da değişir.  
  
 Aşağıdaki örnek çıkış fark gösterilmektedir. Değeri `willIChange` alan sınıf örneğinin yöntemine yönelik çağrı değiştiren `ClassTaker` yöntemi adresi parametresinde belirtilen alanın sınıf örneğinin bulmak için kullandığından. `willIChange` Arama yöntemi yapıda alanının, yöntem çağrısı değişmez `StructTaker` bağımsız değişkeninin değeri yapısı kendisini adresini değil bir kopyasını bir kopyası olduğundan. `StructTaker`kopyalama ve kopyalama kayboluyor ne zaman değişiklikleri çağrısı `StructTaker` tamamlandı.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
