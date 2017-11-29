---
title: "new Kısıtlaması (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a>new Kısıtlaması (C# Başvurusu)
`new` Kısıtlaması, hiçbir tür bağımsız değişkeni genel bir sınıf bildirimindeki genel bir parametresiz oluşturucuya sahip gerektiğini belirtir. New kısıtlaması kullanmak için türü soyut olamaz.  
  
## <a name="example"></a>Örnek  
 Uygulama `new` kısıtlaması aşağıdaki örnekte gösterildiği gibi genel bir sınıf türünün yeni örneklerini oluşturduğunda, bir tür parametresi için:  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a>Örnek  
 Kullandığınızda `new()` kısıtlaması diğer kısıtlamalarla son belirtilmelidir:  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 Daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Genel türler](../../../csharp/programming-guide/generics/index.md)
