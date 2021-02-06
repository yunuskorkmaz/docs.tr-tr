---
description: 'Daha fazla bilgi edinin: AssemblyAttributesGoHere Class'
title: AssemblyAttributesGoHere sınıfı (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: b95ff377f7fa0ffc85136dd69eb4a32121a50dc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638593"
---
# <a name="assemblyattributesgohere-class"></a>AssemblyAttributesGoHere sınıfı

ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.

## <a name="syntax"></a>Syntax

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a>Açıklamalar

Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir. Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır. Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.

Bu türe başvurular, güvenlikle ilgili olmayan ve çoklu kullanım olmayan özel öznitelikleri belirtir.

Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.

## <a name="requirements"></a>Gereksinimler

mscorlib.dll

## <a name="see-also"></a>Ayrıca bkz.

- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
