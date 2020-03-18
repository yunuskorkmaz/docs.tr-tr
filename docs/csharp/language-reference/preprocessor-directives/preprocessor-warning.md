---
title: '#uyarı - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715063"
---
# <a name="warning-c-reference"></a>#warning (C# Başvurusu)
`#warning`kodunuzda belirli bir konumdan [bir CS1030](../../misc/cs1030.md) düzey bir derleyici uyarısı oluşturmanıza olanak tanır. Örnek:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar
 Yaygın bir `#warning` kullanım koşullu bir yönergede yer alan bir durumdur. [#error](./preprocessor-error.md)ile kullanıcı tanımlı bir hata oluşturmak da mümkündür.  
  
## <a name="example"></a>Örnek  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
