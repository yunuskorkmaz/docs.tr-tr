---
title: '#Uyarı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268189"
---
# <a name="warning-c-reference"></a>#warning (C# Başvurusu)
`#warning` kodunuzda belirli bir konumdan bir düzey bir uyarı üretir olanak sağlar. Örneğin:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yaygın kullanımı `#warning` koşullu yönergesinde değil. Kullanıcı tanımlı bir hata ile oluşturmak mümkündür [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
## <a name="example"></a>Örnek  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
