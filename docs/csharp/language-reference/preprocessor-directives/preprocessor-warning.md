---
description: '#Uyarı-C# başvurusu'
title: '#Uyarı-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: ab2cc5120492fc2a4b94296eb85e563c0a1d5ad3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137844"
---
# <a name="warning-c-reference"></a>#warning (C# Başvurusu)
`#warning` kodunuzda belirli bir konumdan bir [CS1030](../../misc/cs1030.md) düzeyinde bir derleyici uyarısı oluşturmanıza olanak sağlar. Örneğin:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Açıklamalar
 Öğesinin yaygın kullanımı `#warning` koşullu bir yönergedir. [#Error](./preprocessor-error.md)ile Kullanıcı tanımlı bir hata oluşturmak da mümkündür.  
  
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

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
