---
title: "let tümcesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 077c5178946b85d0fb85aa8da94966e4c5821736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-c-reference"></a>let tümcesi (C# Başvurusu)
Bir sorgu ifadesinde bazen sonraki yan tümcelerinde kullanmak için bir alt ifade sonucunu depolamak yararlıdır. Bunu yapmak `let` yeni bir aralık değişkeni oluşturan ve sağladığınız ifade sonucuyla başlatır anahtar sözcüğü. Bir değerle başlatıldıktan sonra aralık değişkeni başka bir değeri depolamak için kullanılamaz. Ancak, aralık değişkeni sorgulanabilir bir tür barındırıyorsa, sorgulanabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `let` iki yolla kullanılır:  
  
1.  Kendisini sorgulanabilir bir numaralandırma türü oluşturmak için.  
  
2.  Aranacak sorgu etkinleştirmek için `ToLower` aralık değişkeni üzerinde yalnızca bir kez `word`. Kullanmadan `let`, çağrı zorunda `ToLower` her koşulda içinde `where` yan tümcesi.  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Nasıl yapılır: Sorgu ifadelerinde özel durumları işleme](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
