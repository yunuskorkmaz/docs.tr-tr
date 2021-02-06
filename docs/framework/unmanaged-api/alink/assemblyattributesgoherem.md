---
description: 'Daha fazla bilgi edinin: AssemblyAttributesGoHereM Class'
title: AssemblyAttributesGoHereM sınıfı (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 9afa72e5adbd539acaf8dfe45b446a61862df49e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638580"
---
# <a name="assemblyattributesgoherem-class"></a>AssemblyAttributesGoHereM sınıfı

ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.

## <a name="syntax"></a>Syntax

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a>Açıklamalar

Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir. Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır. Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.

Bu türe başvurular, güvenlikle ilgili olmayan ancak birden çok kullanımda olan özel öznitelikleri belirtir.

Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.

## <a name="requirements"></a>Gereksinimler

mscorlib.dll

## <a name="see-also"></a>Ayrıca bkz.

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
