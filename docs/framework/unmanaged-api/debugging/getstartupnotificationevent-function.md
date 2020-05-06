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
ms.openlocfilehash: 3377dcd5d45ca8e31a57a75bd81366d41837c12c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860708"
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
 `phStartupEvent`null veya `debuggeePID` Şu anda çalışan bir işleme başvurmuyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Başlangıç bildirimi olayının tanıtıcısı alınamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Windows işletim sisteminde bir IŞLETIM sistemi `debuggeePID` işlem tanımlayıcısına eşlenir.  
  
 Olaya, olayı gösteren CLR tarafından yönetilen herhangi bir kod yürütülmeden önce sinyal gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
