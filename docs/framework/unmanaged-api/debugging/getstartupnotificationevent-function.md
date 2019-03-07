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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487336"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent İşlevi
Oluşturur veya üzerine belirtilen hedef işlemde yüklenmekte olan tüm ortak dil çalışma zamanı (CLR) tarafından sinyal bir olay işleyici açılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parametreler  
 `debuggeePID`  
 [in] CLR başlatma bildirimlerini almak üzere hedef işlemin işlem tanımlayıcısı.  
  
 `phStartupEvent`  
 [out] Başlangıçta bir CLR tarafından sinyal bir tanıtıcı bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başlangıç bildirim olayı tanıtıcısını başarıyla aldı.  
  
 E_INVALIDARG  
 `phStartupEvent` null veya `debuggeePID` şu anda çalışan bir işleme başvurmuyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Başlangıç bildirim olay tanıtıcısı alınamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanımlayıcısı.  
  
 Olay herhangi önce yönetilen kod olayın sinyal CLR tarafından yürütülen işaret bildirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
