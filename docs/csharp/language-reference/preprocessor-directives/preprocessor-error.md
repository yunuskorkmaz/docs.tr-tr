---
title: '#hata - C# Başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173412"
---
# <a name="error-c-reference"></a>#error (C# Başvurusu)
`#error`kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) kullanıcı tanımlı bir hata oluşturmanıza olanak tanır. Örnek:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yaygın bir `#error` kullanım koşullu bir yönergede yer alan bir durumdur.  
  
 [#warning](./preprocessor-warning.md)ile kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.  
  
## <a name="example"></a>Örnek  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
