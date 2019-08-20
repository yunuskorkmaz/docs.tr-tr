---
title: '#endif- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608574"
---
# <a name="endif-c-reference"></a>#endif (C# Başvurusu)
`#endif`[#if](./preprocessor-if.md) yönergesiyle başlayan bir koşul yönergesinin sonunu belirtir. Örneğin,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `#if` Yönergeyle başlayan koşullu yönerge, açıkça bir `#endif` yönergeyle sonlandırılmalıdır. Öğesinin [](./preprocessor-if.md) nasıl kullanılacağına `#endif`ilişkin bir örnek için bkz. #if.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
