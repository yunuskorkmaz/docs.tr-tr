---
title: "typeof (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a>typeof (C# Başvurusu)
Elde etmek için kullanılan `System.Type` nesne türü için. A `typeof` ifade aşağıdaki formu alır:  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı tür ifade elde etmek için .NET Framework yöntemini kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` İşleci olamaz aşırı yüklenebilir.  
  
 `typeof` İşleci açık genel türler üzerinde de kullanılabilir. Birden fazla tür parametresi türleriyle virgül uygun sayıda belirtiminde olması gerekir. Aşağıdaki örnek, bir yöntemin dönüş türünü genel olup olmadığını belirlemek gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601>. Yöntem MethodInfo türünün bir örneği olduğunu varsayın:  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Object.GetType%2A> yöntemi sayısal hesaplamanın sonucu kapsamak için kullanılmış türü belirlenemiyor. Bu sonuç sayısı depolama gereksinimlerine bağlıdır.  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type?displayProperty=nameWithType>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [değil](../../../csharp/language-reference/keywords/is.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
