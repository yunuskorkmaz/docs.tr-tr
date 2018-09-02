---
title: '#Bölge (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 3edc4fe757ab1f5cbf42e67ab74cd8032a82d853
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463279"
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
