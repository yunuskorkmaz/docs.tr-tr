---
title: "sizeof (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords: sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a>sizeof (C# Başvurusu)
Yönetilmeyen bir tür için bayt cinsinden boyutu almak için kullanılır. Yönetilmeyen türleri, aşağıdaki tabloda, aşağıdaki yanı sıra listelenen yerleşik türleri şunlardır:  
  
-   Numaralandırma türleri  
  
-   İşaretçi türleri  
  
-   Herhangi bir alan veya başvuru türleri olan özellikler içermeyen kullanıcı tanımlı yapılar  
  
 Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Açıklamalar  
 C# 2.0 sürümünden başlayarak, uygulama `sizeof` için yerleşik türler artık gerektiren [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) modu kullanılabilir.  
  
 `sizeof` İşleci olamaz aşırı yüklenebilir. Tarafından döndürülen değer `sizeof` işleci türündedir `int`. İçin yerine sabit değerleri aşağıdaki tabloda gösterilmektedir `sizeof` işlenen olarak yerleşik belirli türlerine sahip bir ifade.  
  
|İfade|Sabit değer|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1.|  
|`sizeof(byte)`|1.|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1.|  
  
 Yapılar, diğer tüm türler için dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir. Kullanabilirsiniz ancak <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman tarafından döndürülen değer ile aynı `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>türü sıralanmış sonra ancak boyutunu döndüren `sizeof` herhangi bir doldurmaya dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılmış olarak boyutu döndürür.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Enum](../../../csharp/language-reference/keywords/enum.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md)
