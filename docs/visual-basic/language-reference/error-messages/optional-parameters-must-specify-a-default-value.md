---
description: 'Şu konuda daha fazla bilgi edinin: BC30812: Isteğe bağlı parametreler varsayılan bir değer belirtmelidir'
title: İsteğe bağlı parametreler varsayılan bir değer belirtmelidir
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 1cbed1c0f1297ecacdae94d9234d18a3d268f487
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795540"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a>BC30812: Isteğe bağlı parametreler varsayılan bir değer belirtmelidir

İsteğe bağlı parametreler, bir çağıran yordam tarafından hiçbir parametre sağlanmadığında kullanılabilecek varsayılan değerler sağlamalıdır.

**Hata kimliği:** BC30812

## <a name="example"></a>Örnek

Aşağıdaki örnek BC30812 oluşturur:

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

İsteğe bağlı parametreler için varsayılan değerleri belirtin:

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a>Ayrıca bkz.

- [İsteğe bağlı](../modifiers/optional.md)
