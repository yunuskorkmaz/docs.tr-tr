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
ms.openlocfilehash: a725aa2c0f1fdea523bbf7cba880bc805f855782
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860741"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_StackTrace işlevi
Yönetilmeyen ve yönetilen kod arasındaki her geçiş için bir yönetilen yığın izlemenin ve `CONTEXT` bir kayıt dizisinin metin gösterimini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Hata ayıklamakta olan istemci.  
  
 `wszTextOut`  
 dışı Yığın izlemenin metin temsili.  
  
 `puiTextLength`  
 dışı İçindeki `wszTextOut`karakter sayısına yönelik bir işaretçi.  
  
 `pTransitionContexts`  
 dışı Geçiş bağlamlarının dizisi.  
  
 `puiTransitionContextCount`  
 dışı Dizideki geçiş bağlamlarının sayısına yönelik bir işaretçi.  
  
 `uiSizeOfContext`  
 'ndaki Bağlam yapısının boyutu.  
  
 `Flags`  
 'ndaki Her `module!functionname` satırın önünde EBP kaydını ve ENTER yığın IŞARETÇISINI (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  
 `_EFN_StackTrace` Yapı bir WinDbg programlı arabiriminden çağrılabilir. Parametreleri aşağıdaki gibi kullanılır:  
  
- `wszTextOut` Null ise ve `puiTextLength` null değilse, işlev içindeki `puiTextLength`dize uzunluğunu döndürür.  
  
- `wszTextOut` Null değilse, işlev tarafından `wszTextOut` `puiTextLength`belirtilen konuma kadar metni depolar. Arabellekte yeterli yer varsa başarıyla geri döner veya arabellek yeterince uzunsa E_OUTOFMEMORY döndürür.  
  
- İşlevin geçiş bölümü, ve `pTransitionContexts` `puiTransitionContextCount` her ikisi de null ise yoksayılır. Bu durumda, işlev çağıranları yalnızca işlev adlarının metin çıktısı ile birlikte sunar.  
  
- `pTransitionContexts` Null ise ve `puiTransitionContextCount` null değilse, işlev içinde `puiTransitionContextCount`gereken bağlam girişi sayısını döndürür.  
  
- `pTransitionContexts` Null değilse, işlev bunu bir dizi yapının dizisi olarak değerlendirir `puiTransitionContextCount`. Yapı boyutu tarafından `uiSizeOfContext`verilir ve [SimpleContext](stacktrace-simplecontext-structure.md) 'in veya `CONTEXT` mimarinin boyutu olmalıdır.  
  
- `wszTextOut`aşağıdaki biçimde yazılır:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Onaltılı konum 0x0 ise, hiçbir fark yazılmaz.  
  
- Şu anda bağlamda olan iş parçacığında yönetilen kod yoksa, işlev SOS_E_NOMANAGEDCODE döndürür.  
  
- Her `Flags` `module!functionname` satırın önünde ebp ve ESP görmek için parametresi 0 veya SOS_STACKTRACE_SHOWADDRESSES. Varsayılan olarak, 0 ' dır.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
