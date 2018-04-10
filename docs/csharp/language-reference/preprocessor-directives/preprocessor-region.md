---
title: '#Bölge (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region`Genişlet veya daralt kullanırken kod bloğu belirtmenizi sağlar [anahat oluşturma](/visualstudio/ide/outlining) özelliği Visual Studio Kod Düzenleyicisi'nin. Uzun kod dosyalarında daraltın veya üzerinde çalışmakta olduğunuz dosya bölümüne odaklanabiliriz bir veya daha fazla bölge gizlemek uygundur. Aşağıdaki örnek, bir bölge tanımlamasına gösterilmektedir:  
  
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
