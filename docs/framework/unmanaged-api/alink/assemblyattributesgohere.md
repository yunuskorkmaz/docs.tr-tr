---
title: AssemblyAttributesGoHere
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: c24ca43f35e237b6387e108563b1f9c9ed432242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402401"
---
# <a name="assemblyattributesgohere"></a>AssemblyAttributesGoHere
ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış. Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır. Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.  
  
 Bu tür başvuruları güvenlikle ilgili olmayan özel öznitelikleri belirtmek ve çoklu kullanım değildir.  
  
 Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Gereksinimler  
 mscorlib.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [AssemblyAttributesGoHereS](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
