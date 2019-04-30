---
title: '#Bölge - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: adaa58fc47da557a31270e99ff8a1dae3d0731bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659988"
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region` Genişlet veya daralt kullanarak bir kod bloğunu belirtmenizi sağlar [anahat oluşturma](/visualstudio/ide/outlining) özelliği, Visual Studio Kod Düzenleyicisi. Uzun kod dosyalarında Daralt veya, üzerinde çalıştığınız dosya yoluna odaklanabilmeniz için bir veya daha fazla bölgede gizlemek uygundur. Aşağıdaki örnek, bir bölge tanımlamasına gösterilmektedir:  
  
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
 A `#region` blok sonlandırıldı, ile bir [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) yönergesi.  
  
 A `#region` blok ile örtüşemez bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) blok. Ancak, bir `#region` blok iç içe geçirilemez içinde bir `#if` bloğu ve `#if` blok iç içe geçirilemez bir `#region` blok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
