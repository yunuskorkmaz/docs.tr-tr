---
title: "in (Genel Değiştirici) (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a>in (Genel Değiştirici) (C# Başvurusu)
Genel tür parametreleri için `in` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir. Kullanabileceğiniz `in` anahtar sözcüğü genel arabirimler ve temsilciler.  
  
 Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar. Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar. Kovaryans ve kontravaryans genel tür parametrelerindeki referans türleri için desteklenir, ancak değer türlerinde desteklenmez.  
  
 Yalnızca bir tür yöntemi bağımsız değişken olarak kullanılan ve yöntemin dönüş türü olarak kullanılmayan bir türü karşıtı genel arabirim veya temsilci olarak bildirilebilir. `Ref`ve `out` parametreleri değişken olamaz.  
  
 Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar. Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Employee` devralır `Person`.  
  
 Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.  
  
 Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir. Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir. Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [çıkışı](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
