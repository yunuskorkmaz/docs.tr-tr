---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74447f52c75ae22e513c6f07950630d37bad191a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790123"
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS

ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.

## <a name="syntax"></a>Sözdizimi

```
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a>Açıklamalar

Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması. Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır. Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.

Bu tür başvurularını güvenlikle ilgili özel öznitelikleri belirtmek ve çoklu kullanım değildir.

Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices> ad alanı.

## <a name="requirements"></a>Gereksinimler

mscorlib.dll

## <a name="see-also"></a>Ayrıca bkz.

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
