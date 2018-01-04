---
title: "GetStartupNotificationEvent İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 809f34d265e0a1677d8b7fc78515b20df7353968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent İşlevi
Sonra belirtilen hedef işleminde yüklenen tüm ortak dil çalışma zamanı (CLR) tarafından bildirim yapılan bir olay tanıtıcısı açar veya oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `debuggeePID`  
 [in] CLR başlatma bildirimlerini almak üzere hedef işlemini işlem tanıtıcısı.  
  
 `phStartupEvent`  
 [out] Bir işaretçi bir CLR başlangıçta tarafından işaret işlenecek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başlangıç bildirim olayı tanıtıcısını başarıyla aldı.  
  
 E_INVALIDARG  
 `phStartupEvent`null veya `debuggeePID` şu anda çalışan bir işlemin başvurmuyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Başlangıç bildirim olayı tanıtıcısını elde edilemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanıtıcısı.  
  
 Olay herhangi önce yönetilen kod olay işareti CLR tarafından yürütülen verdi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
