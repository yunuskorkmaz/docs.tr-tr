---
title: '#endif- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712552"
---
# <a name="endif-c-reference"></a>#endif (C# Başvurusu)
`#endif`, [#if](./preprocessor-if.md) yönergesiyle başlayan bir koşul yönergesinin sonunu belirtir. Örneğin,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `#if` yönergesiyle başlayan koşullu yönerge, açıkça bir `#endif` yönergesi ile sonlandırılmalıdır. `#endif`nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
