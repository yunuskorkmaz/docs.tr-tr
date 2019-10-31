---
title: GetStartupNotificationEvent İşlevi
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122948"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent İşlevi
Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parametreler  
 `debuggeePID`  
 'ndaki CLR başlangıç bildirimlerinin alınacağı hedef işlemin işlem tanımlayıcısı.  
  
 `phStartupEvent`  
 dışı Başlangıçta CLR tarafından bildirilecektir bir tanıtıcı işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Tanıtıcı, başlangıç bildirimi olayına başarıyla alındı.  
  
 E_INVALIDARG  
 `phStartupEvent` null veya `debuggeePID` Şu anda çalışan bir işleme başvurmuyor.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 Başlangıç bildirimi olayının tanıtıcısı alınamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Windows işletim sisteminde `debuggeePID` bir IŞLETIM sistemi işlem tanımlayıcısına eşlenir.  
  
 Olaya, olayı gösteren CLR tarafından yönetilen herhangi bir kod yürütülmeden önce sinyal gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
