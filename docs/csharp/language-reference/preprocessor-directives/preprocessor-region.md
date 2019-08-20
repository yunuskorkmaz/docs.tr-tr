---
title: '#Bölge C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ba5b47d77c69761a77b05ac6079e1b003af336b3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608758"
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region`Visual Studio Code düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir. Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:  
  
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
  
 Bir `#region` blok [#if](./preprocessor-if.md) bloğuyla çakışamaz. Ancak bir blok bir `#if` blokta iç içe olabilir ve `#if` bir blok bir `#region` blok içinde iç içe olabilir. `#region`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
