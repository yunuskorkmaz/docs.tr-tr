---
description: '#endif-C# başvurusu'
title: '#endif-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 0ccc00ceab2aa67c77140e3ef09907ba260d7e9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168640"
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

 Yönergeyle başlayan koşullu yönerge `#if` , açıkça bir `#endif` yönergeyle sonlandırılmalıdır. Öğesinin nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) `#endif` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
