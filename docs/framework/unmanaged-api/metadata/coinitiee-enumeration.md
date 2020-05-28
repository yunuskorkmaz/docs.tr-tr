---
title: COINITIEE Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005914"
---
# <a name="coinitiee-enumeration"></a>COINITIEE Numaralandırması
Ortak dil çalışma zamanı başlatılırken [Coınitialeee](../hosting/coinitializeee-function.md) tarafından kullanılan sabitleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Varsayılan başlatma modu. Bu, çalışma zamanını başlatır ve varsayılan olarak oluşturur <xref:System.AppDomain> .|  
|`COINITEE_DLL`|Yönetilen DLL çalıştırmak için başlatılır.|  
|`COINITEE_MAIN`|Yönetilen bir EXE çalıştırmak için başlatılır. Bu, çalışma zamanını başlatır, ancak varsayılan <xref:System.AppDomain> olarak exe 'nin ana yordamını girdikten sonra oluşturulur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
