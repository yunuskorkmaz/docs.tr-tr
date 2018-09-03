---
title: sizeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: f2507dd8528e2e66016524873ada890227a74ed8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487201"
---
# <a name="sizeof-c-reference"></a>sizeof (C# Başvurusu)
Yönetilmeyen bir tür için bayt cinsinden boyutunu almak için kullanılır.

Yönetilmeyen türleri şunlardır:

-   Aşağıdaki tabloda listelenen basit türler:
  
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
  
-   Numaralandırma türleri.
  
-   İşaretçi türleri.
  
-   Tüm örnek alanları veya başvuru türleri veya oluşturulan türler otomatik olarak uygulanan örnek özellikler içermeyen kullanıcı tarafından tanımlanan yapılar.
  
 Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Açıklamalar  
 C# 2.0 sürümünden itibaren uygulama `sizeof` basit veya sabit listesi türleri artık gerektirir kod içinde derlenecek bir [güvenli](unsafe.md) bağlamı.
  
 `sizeof` İşleci aşırı yüklenemez. Tarafından döndürülen değerler `sizeof` işleci, tür `int`. Önceki tablonun gösterdiği için yerine sabit değerler `sizeof` işlenen olarak bazı basit türler sahip ifadeler.  
    
 Yapılar, diğer tüm türleri için de dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir. Hizmetini kullanıyor olsanız da <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman aynı tarafından döndürülen değer olarak `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> türü sıralanmış sonra ise boyutunu döndürür `sizeof` herhangi doldurma dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılan boyutunu döndürür.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [enum](../../../csharp/language-reference/keywords/enum.md)  
- [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)
