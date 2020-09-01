---
description: '#Region-C# başvurusu'
title: '#Region-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ed40d895fedb9be271bb389a4f8de69d7ae3f266
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137948"
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region` kod düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir. Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `#region` blok, bir [#endregion](./preprocessor-endregion.md) yönergesi ile sonlandırılmalıdır.  
  
 Bir `#region` blok [#if](./preprocessor-if.md) bloğuyla çakışamaz. Ancak bir blok `#region` bir blokta iç içe olabilir ve bir blok `#if` bir blok `#if` içinde iç içe olabilir `#region` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
