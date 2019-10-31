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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136973"
---
# <a name="_cordllmain-function"></a>\_CorDllMain Işlevi

Ortak dil çalışma zamanını (CLR) başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hInst`  
 'ndaki Yüklenen modülün örnek tanıtıcısı.  
  
 `dwReason`  
 'ndaki DLL giriş noktası işlevinin neden çağrıldığını gösterir. Bu parametre aşağıdaki değerlerden biri olabilir: DLL\_PROCESS_ATTACH, DLL\_Iş parçacığı\_ILIŞTIRME, DLL\_Iş parçacığı\_ILIŞTIRME veya DLL\_Işlem\_AYıRMA. Bu değerlerin açıklamaları için Platform SDK 'sindeki `DllMain` belgelerine bakın.  
  
 `lpReserved`  
 'ndaki Kullanılmayan.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, hata oluşursa `true` başarılı ve `false` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, DLL derlemeleri için işletim sistemi yükleyicisi tarafından çağırılır. Yürütülebilir derlemeler için yükleyici bunun yerine [\_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini çağırır.  
  
 İşletim sistemi yükleyicisi, DLL dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.  
  
`_CorDllMain` işlevi, işletim sistemi yükleyicisi tarafından doğrudan çağırılır.
  
 Daha fazla bilgi için [\_Corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
