---
title: '#hata - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559350"
---
# <a name="error-c-reference"></a>#error (C# Başvurusu)
`#error` oluşturmanıza olanak sağlar. bir [CS1029](../compiler-messages/cs1029.md) kodunuzda belirli bir konumdan kullanıcı tanımlı hata. Örneğin:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yaygın `#error` bir koşullu yönergesiyse.  
  
 Kullanıcı tanımlı bir uyarı ile oluşturmak mümkündür [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
