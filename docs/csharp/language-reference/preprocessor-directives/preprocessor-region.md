---
title: '#Bölge (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 88632b04ec8932e22f5bf7a23b8f0edf14d89f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region` Genişlet veya daralt kullanırken kod bloğu belirtmenizi sağlar [anahat oluşturma](/visualstudio/ide/outlining) özelliği Visual Studio Kod Düzenleyicisi'nin. Uzun kod dosyalarında daraltın veya üzerinde çalışmakta olduğunuz dosya bölümüne odaklanabiliriz bir veya daha fazla bölge gizlemek uygundur. Aşağıdaki örnek, bir bölge tanımlamasına gösterilmektedir:  
  
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
  
 A `#region` bloğu ile örtüşemez bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloğu. Ancak, bir `#region` bloğu iç içe geçirilemez içinde bir `#if` bloğu ve `#if` bloğu iç içe geçirilemez içinde bir `#region` blok.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
