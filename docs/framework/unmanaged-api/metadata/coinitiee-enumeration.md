---
title: "COINITIEE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ad117c3efd31cc176281e571b7fde11229c097e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coinitiee-enumeration"></a>COINITIEE Numaralandırması
Tarafından kullanılan sabitlerini belirtir [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ortak dil çalışma zamanı başlatırken.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Varsayılan başlatma modu. Bu çalışma zamanı başlatır ve varsayılan oluşturur <xref:System.AppDomain>.|  
|`COINITEE_DLL`|Yönetilen DLL çalıştırmak için başlatır.|  
|`COINITEE_MAIN`|Yönetilen bir EXE çalıştırmak için başlatır. Bu çalışma zamanı başlatır, ancak varsayılan oluşturmaz <xref:System.AppDomain>, hangi EXE ana yordam girdikten sonra oluşturulur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
