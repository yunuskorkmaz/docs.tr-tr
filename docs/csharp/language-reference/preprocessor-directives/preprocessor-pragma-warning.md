---
title: '#pragma uyarı- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: dc221235e78a187f921815ed6e6c7750778014d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922269"
---
# <a name="pragma-warning-c-reference"></a>#pragma uyarısı (C# Başvurusu)
`#pragma warning`Belirli uyarıları etkinleştirebilir veya devre dışı bırakabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametreler  
 `warning-list`  
 Uyarı numaralarının virgülle ayrılmış bir listesi. "CS" ön eki isteğe bağlıdır.  
  
 Hiçbir uyarı numarası belirtilmediğinde, `disable` tüm uyarıları devre dışı bırakır ve `restore` tüm uyarıları etkinleştirilir.  
  
> [!NOTE]
> Visual Studio 'da uyarı numaralarını bulmak için projenizi derleyin ve ardından **Çıkış** penceresinde uyarı numaralarını arayın.  
  
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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
- [C# Derleyici Hataları](../compiler-messages/index.md)
