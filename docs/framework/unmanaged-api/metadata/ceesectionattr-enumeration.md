---
description: 'Daha fazla bilgi edinin: CeeSectionAttr numaralandırması'
title: CeeSectionAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 13cfb635aaa606905745146d7c3caae3f9162e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678880"
---
# <a name="ceesectionattr-enumeration"></a>CeeSectionAttr Numaralandırması

[ICeeGen](iceegen-interface.md) arabirimi tarafından kullanılmak üzere bir bölümün özniteliklerini belirten değerler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`sdNone`|Bölümünde hiç öznitelik yok.|  
|`sdReadOnly`|Bölüm yalnızca okunabilir, güncelleştirilmemiş, başlatılmamış verileri içerir.|  
|`sdReadWrite`|Bölüm, okunabilecek veya güncelleştirilebilen başlatılmış verileri içerir.|  
|`sdExecute`|Bölüm, okunve yürütülmesine izin verilen yürütülebilir kodu içerir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
