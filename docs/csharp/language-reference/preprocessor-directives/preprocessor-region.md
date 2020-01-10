---
title: '#Bölge C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 723a904d18955caceea9e0d485ab51f84366c66e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715126"
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region`, Visual Studio Code düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir. Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:  
  
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
 Bir `#region` bloğunun [#endregion](./preprocessor-endregion.md) yönergesiyle sonlandırılması gerekir.  
  
 `#region` bloğu bir [#if](./preprocessor-if.md) bloğuyla çakışamaz. Ancak, bir `#region` bloğu bir `#if` bloğunda iç içe olabilir ve bir `#if` bloğu bir `#region` bloğunda iç içe geçmiş olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
