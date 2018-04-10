---
title: where (genel tür kısıtlaması) (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)
Genel tür tanımında `where` yan tümcesi genel bildiriminde tanımlanan bir tür parametresi için bağımsız değişken olarak kullanılan türleri kısıtlamaları belirtmek için kullanılır. Örneğin, genel bir sınıf bildirebilir `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  Daha fazla bilgi için bir sorgu ifadesinde yan tümcesine bakın [burada yan tümcesi](../../../csharp/language-reference/keywords/where-clause.md).  
  
 Arabirim kısıtlamaları yanı sıra bir `where` yan tümcesi bir türü belirtilen sınıf bir temel sınıf olarak (veya bu sınıfı) sahip belirten bir temel sınıf kısıtlaması içerebilir genel türü için tür bağımsız değişkeni olarak kullanılması için. Böyle bir kısıtlama kullanılırsa, bu tür parametre diğer kısıtlamalar önce görünmelidir.  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` Yan tümcesi Oluşturucusu kısıtlaması de içerebilir. Yeni işlecini kullanan bir tür parametresi bir örneğini oluşturmak mümkündür; Ancak, bunu yapmak için tür parametresi gerekir kısıtlı Oluşturucusu kısıtlaması tarafından `new()`. [New() kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini biliyor derleyici sağlar parametresiz--veya varsayılan--oluşturucusu. Örneğin:  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` Kısıtlaması görünür içinde son `where` yan tümcesi.  
  
 Birden çok tür parametreleri ile kullanmayı `where` yan tümcesi örneğin her tür parametresi için:  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Tür parametreleri bu gibi genel yöntemlerin kısıtlamaları da ekleyebilirsiniz:  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Temsilciler üzerinde türü parametresi kısıtlamaları tanımlamak üzere sözdizimini aynı yöntemleri olduğuna dikkat edin:  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [New kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
