---
title: sizeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
 Yapılar, diğer tüm türler için dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir. Kullanabilirsiniz ancak <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman tarafından döndürülen değer ile aynı `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> türü sıralanmış sonra ancak boyutunu döndüren `sizeof` herhangi bir doldurmaya dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılmış olarak boyutu döndürür.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [enum](../../../csharp/language-reference/keywords/enum.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)
