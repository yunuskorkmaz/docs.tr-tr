---
title: '#pragma uyarısı - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712474"
---
# <a name="pragma-warning-c-reference"></a>#pragma uyarısı (C# Başvurusu)
`#pragma warning`bazı uyarıları etkinleştirebilir veya devre dışı kılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametreler  
 `warning-list`  
 Uyarı numaralarının virgülden ayrılmış bir listesi. "CS" öneki isteğe bağlıdır.  
  
 Uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre `restore` dışı katanır ve tüm uyarıları etkinleştirilir.  
  
> [!NOTE]
> Visual Studio'da uyarı numaralarını bulmak için projenizi oluşturun ve **çıktı** penceresindeuyarı numaralarını arayın.  
  
## <a name="example"></a>Örnek  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
- [C# Derleyici Hataları](../compiler-messages/index.md)
