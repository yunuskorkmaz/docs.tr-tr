---
title: _EFN_StackTrace İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3187809fadb275ed54a450f456d98d140d1100c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485893"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace İşlevi
Yönetilen yığın izlemesi metin gösterimi ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Client`  
 [in] Hatası ayıklanmakta olan istemci.  
  
 `wszTextOut`  
 [out] Yığın izlemesi metin gösterimi.  
  
 `puiTextLength`  
 [out] Karakter sayısı için bir işaretçi `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Geçiş bağlamları dizisi.  
  
 `puiTransitionContextCount`  
 [out] Dizi bağlamlarda geçiş sayısı için bir işaretçi.  
  
 `uiSizeOfContext`  
 [in] Context yapısını boyutu.  
  
 `Flags`  
 [in] EBP kayıt ve her önüne enter yığın işaretçisi (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlanmış `module!functionname` satır.  
  
## <a name="remarks"></a>Açıklamalar  
 `_EFN_StackTrace` Yapısı WinDbg programlı arabiriminden çağrılabilir. Parametreler şu şekilde kullanılır:  
  
-   Varsa `wszTextOut` null ve `puiTextLength` olduğu null, işlev dize uzunluğunu döndürür `puiTextLength`.  
  
-   Varsa `wszTextOut` olan metin null, işlev depolar `wszTextOut` tarafından belirtilen konum kadar `puiTextLength`. Başarıyla arabellek yeterince uzun değildi, arabellek veya E_OUTOFMEMORY döndürür içinde yeterli yer olduğunu döndürür.  
  
-   İşlev geçişi kısmı yoksayılır `pTransitionContexts` ve `puiTransitionContextCount` her ikisi de null olan. Bu durumda, yalnızca işlev adlarını metin çıktısı ile çağıranlar işlevi sağlar.  
  
-   Varsa `pTransitionContexts` null ve `puiTransitionContextCount` olduğu null, işlev bağlam girişler gerekli sayısını döndürür `puiTransitionContextCount`.  
  
-   Varsa `pTransitionContexts` olduğu null, işlevi, yapıları uzunlukta bir dizi gibi davranır `puiTransitionContextCount`. Yapı boyutu tarafından verilen `uiSizeOfContext`, ve boyutunu olmalıdır [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) veya `CONTEXT` mimarisi.  
  
-   `wszTextOut` şu biçimde yazılır:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Onaltılık uzaklık 0x0 ise, hiçbir uzaklığı yazılır.  
  
-   Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev SOS_E_NOMANAGEDCODE döndürür.  
  
-   `Flags` Parametresi, 0 veya EBP ve ESP her önüne görmek için SOS_STACKTRACE_SHOWADDRESSES `module!functionname` satır. Varsayılan olarak, 0'dır.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
