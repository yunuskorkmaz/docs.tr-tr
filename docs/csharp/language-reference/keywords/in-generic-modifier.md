---
title: "in (Genel Değiştirici) (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2af4e27034af0067e81a52c81991edaf5a5415d8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="in-generic-modifier-c-reference"></a>in (Genel Değiştirici) (C# Başvurusu)

Genel tür parametreleri için `in` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir. Kullanabileceğiniz `in` anahtar sözcüğü genel arabirimler ve temsilciler.  
  
 Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar. Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar. Kovaryans ve kontravaryans genel tür parametrelerindeki referans türleri için desteklenir, ancak değer türlerinde desteklenmez.  
  
 Yalnızca bir yöntemin parametre ve bir yöntemin dönüş türü türü tanımlıyorsa türü karşıtı genel arabirim veya temsilci olarak bildirilebilir. `In`, `ref`, ve `out` parametreleri ne oldukları anlamına gelir, sabit olmalıdır eşdeğişken veya karşıtı.
  
 Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar. Örneğin, <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer<Person>` bir nesne türüne `IComparer<Employee>` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Employee` devralır `Person`.  
  
 Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.  
  
 Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="contravariant-generic-interface"></a>Karşıtı genel arabirimi   

 Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir. Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a>Karşıtı Genel temsilci  

 Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir. Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
