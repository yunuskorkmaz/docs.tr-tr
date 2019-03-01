---
title: AssemblyAttributesGoHere sınıfı (System.Runtime.CompilerServices)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968126"
---
# <a name="assemblyattributesgohere-class"></a>AssemblyAttributesGoHere sınıfı

ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.

## <a name="syntax"></a>Sözdizimi

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a>Açıklamalar

Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması. Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır. Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.

Bu tür başvurularını güvenlikle ilgili olmayan özel öznitelikleri belirtmek ve çoklu kullanım değildir.

Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices> ad alanı.

## <a name="requirements"></a>Gereksinimler

mscorlib.dll

## <a name="see-also"></a>Ayrıca bkz.

- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
