---
title: "#<a name=\"error-c-reference\"></a>hata (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#error'
helpviewer_keywords: '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a>#error (C# Başvurusu)
`#error`belirli bir konumdan, kodunuzda bir hata oluştur olanak sağlar. Örneğin:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yaygın kullanımı `#error` koşullu yönergesinde değil.  
  
 Kullanıcı tanımlı bir uyarıyla oluşturmak mümkündür [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
## <a name="example"></a>Örnek  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
