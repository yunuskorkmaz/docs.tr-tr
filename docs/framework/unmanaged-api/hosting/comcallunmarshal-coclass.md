---
description: 'Daha fazla bilgi edinin: ComCallUnmarshal coclass'
title: ComCallUnmarshal Coclass’ı
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
ms.openlocfilehash: 508c1183e2862a286e9db0390bc0348629a9db8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799843"
---
# <a name="comcallunmarshal-coclass"></a>ComCallUnmarshal Coclass’ı

Arabirim işaretçilerinin sıralamasını yönetmek için arabirimler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a>Arabirimler  
  
|Arabirim|Description|  
|---------------|-----------------|  
|`IMarshal`|İstemci işleminde bir proxy oluşturmak, başlatmak ve yönetmek için yöntemler sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yardımcı Sınıfları](hosting-coclasses.md)
