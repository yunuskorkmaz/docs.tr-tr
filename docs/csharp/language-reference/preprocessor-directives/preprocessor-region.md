---
title: '#bölge - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173399"
---
# <a name="region-c-reference"></a>#region (C# Başvurusu)
`#region`Visual Studio Code Editor'un [anahat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenizi sağlar. Uzun kod dosyalarında, şu anda üzerinde çalıştığınız dosya parçasına odaklanabilmeniz için bir veya daha fazla bölgeyi daraltmak veya gizlemek uygundur. Aşağıdaki örnek, bir bölgenin nasıl tanımlandığını gösterir:  
  
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
 Bir `#region` blok [#endregion](./preprocessor-endregion.md) bir yönerge ile sonlandırılmalıdır.  
  
 Bir `#region` blok [#if](./preprocessor-if.md) bir blokla çakışamaz. Ancak, `#region` bir blok bir `#if` blok iç içe `#if` olabilir ve bir `#region` blok bir blok iç içe olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
