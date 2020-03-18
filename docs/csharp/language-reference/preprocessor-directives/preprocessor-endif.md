---
title: '#endif - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712552"
---
# <a name="endif-c-reference"></a>#endif (C# Başvurusu)
`#endif`[#if](./preprocessor-if.md) yönergesi ile başlayan koşullu bir direktifin sonunu belirtir. Örneğin,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `#if` yönergeyle başlayan koşullu bir yönerge, `#endif` bir yönergeyle açıkça sonlandırılmalıdır. Nasıl [#if](./preprocessor-if.md) kullanılacağına bir örnek `#endif`için #if bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
