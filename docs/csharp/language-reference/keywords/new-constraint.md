---
title: new Kısıtlaması (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269002"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)
