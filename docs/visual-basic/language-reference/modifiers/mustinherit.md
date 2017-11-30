---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Bir sınıf yalnızca bir temel sınıf olarak kullanılabilir ve doğrudan bir nesne oluşturamazsınız belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Amacı bir *temel sınıfı* (olarak da bilinen bir *soyut sınıf*) ondan türetilmiş tüm sınıflar ortak işlevselliği tanımlamaktır. Bu türetilmiş sınıfları ortak öğeler tanımlanacak gereğini ortadan kaldırır. Bazı durumlarda, bu ortak işlevselliği kullanılabilir bir nesne için tam değil ve eksik işlev her türetilmiş bir sınıf tanımlar. Böyle bir durumda, yalnızca türetilmiş sınıflarından nesneleri oluşturmak için kullanıcı kodu istiyor. Kullandığınız `MustInherit` bu zorlamak için temel sınıfı.  
  
 Başka bir kullanımını bir `MustInherit` sınıfı, bir dizi ilgili sınıflar için bir değişken kısıtlamak için. Bu ilgili sınıfları bu sınıftan türetilen ve bir taban sınıf tanımlayın. Türetilen sınıflar için ortak olan herhangi bir işlevsellik sağlamak temel sınıf gerekmez, ancak değişkenlere değerler atama için bir filtre olarak hizmet verebilir. Süren kodunuzu bir değişken temel sınıf olarak bildirirse, Visual Basic, yalnızca bir nesne türetilmiş sınıflarından biri için bu değişkeni atamanıza olanak sağlar.  
  
 .NET Framework birkaç tanımlar `MustInherit` sınıfları, aralarında <xref:System.Array>, <xref:System.Enum>, ve <xref:System.ValueType>. <xref:System.ValueType>bir değişken kısıtlayan bir taban sınıf örnektir. Tüm değer türlerini türetmek <xref:System.ValueType>. Bir değişken olarak bildirirseniz <xref:System.ValueType>, bu değişken yalnızca değer türleri atayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `MustInherit` yalnızca bir `Class` deyimi.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `MustInherit` ile birlikte `NotInheritable` aynı bildirimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zorla devralma ve geçersiz kılma zorlanmış gösterilmektedir. Taban sınıfı `shape` bir değişkeni `acrossLine`. Sınıfları `circle` ve `square` öğesinden türetilen `shape`. Tanımını devral `acrossLine`, ancak işlev tanımlamalısınız `area` Bu hesaplamayı şekli her tür için farklı olduğu için.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Bildirebilirsiniz `shape1` ve `shape2` türünde olması `shape`. Ancak, bir nesneden oluşturamazsınız `shape` işlevi işlevselliğini eksik olduğundan `area` ve işaretlenmiş `MustInherit`.  
  
 Olarak bildirilen çünkü `shape`, değişkenleri `shape1` ve `shape2` nesnelere türetilmiş sınıflarından kısıtlanmıştır `circle` ve `square`. Visual Basic bu değişkenleri için herhangi bir nesneye atamak yüksek düzeyde bir tür güvenliği sağlayan izin vermez.  
  
## <a name="usage"></a>Kullanım  
 `MustInherit` Bu bağlamda değiştirici kullanılabilir:  
  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Devralma temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
