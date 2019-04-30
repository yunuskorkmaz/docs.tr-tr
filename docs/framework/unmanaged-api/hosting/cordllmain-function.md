---
title: _CorDllMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666927"
---
# <a name="cordllmain-function"></a>\_CorDllMain işlevi

Ortak dil çalışma zamanı (CLR) başlatır, DLL derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hInst`  
 [in] Yüklenen bir modülün örneği tanıtıcısı.  
  
 `dwReason`  
 [in] DLL giriş noktası işlevini neden çağrılan gösterir. Bu parametre aşağıdaki değerlerden biri olabilir: DLL\__DllMainCRTStartup, DLL\_iş PARÇACIĞI\_ATTACH, DLL\_iş PARÇACIĞI\_Ekle veya DLL\_işlem\_ayırma. Bu değerleri açıklamaları için bkz. `DllMain` Platform SDK belgelerinde.  
  
 `lpReserved`  
 [in] Kullanılmayan.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem döndürür `true` başarı için ve `false` hata oluşması durumunda.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, DLL derlemeler için işletim sistemi yükleyicisi tarafından çağrılır. Yürütülebilir derlemeler için yükleyici çağırır [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini.  
  
 İşletim sistemi yükleyicisi DLL dosyası içinde belirtilen giriş noktası bakılmaksızın bu yöntemi çağırır.  
  
`_CorDllMain` İşlevi, doğrudan işletim sistemi yükleyicisi tarafından çağrılır.
  
 Ek bilgi için bkz açıklamalar bölümünde [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
