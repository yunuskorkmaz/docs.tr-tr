---
title: "Nasıl yapılır: bool? Değerinden bool Değerine Güvenli bir Şekilde Atama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>Nasıl yapılır: bool? Değerinden bool Değerine Güvenli bir Şekilde Atama (C# Programlama Kılavuzu)
`bool?` Boş değer atanabilir tür üç farklı değerler içerebilir: `true`, `false`, ve `null`. Bu nedenle, `bool?` türü ile gibi koşulları kullanılamaz `if`, `for`, veya `while`. Örneğin, aşağıdaki kod derleyici hatasına neden olur.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 Ne belirsiz olmasından dolayı buna izin verilmiyor `null` koşullu bağlamında anlamına gelir. Kullanmak için bir `bool?` koşullu bir deyimde ilk denetleyin, <xref:System.Nullable%601.HasValue%2A> değerini olmadığından emin olmak için özellik `null`ve ardından hangisine `bool`. Daha fazla bilgi için bkz: [bool](../../../csharp/language-reference/keywords/bool.md). Cast gerçekleştirirseniz bir `bool?` değerini `null`, <xref:System.InvalidOperationException> koşullu testinde oluşturulur. Aşağıdaki örnek, gelen güvenli bir şekilde atama yollarından biri gösterir `bool?` için `bool`:  
  
## <a name="example"></a>Örnek  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Literal anahtar sözcükleri](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
 [?? İşleci](../../../csharp/language-reference/operators/null-conditional-operator.md)
