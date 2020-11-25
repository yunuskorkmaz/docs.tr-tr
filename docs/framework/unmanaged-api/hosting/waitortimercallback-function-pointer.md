---
title: WAITORTIMERCALLBACK İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732820"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK İşlev İşaretçisi

Ana bilgisayarı bir bekleme tutamacının ( <xref:System.Threading.WaitHandle> ) sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.  
  
 Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `lpParameter`  
 'ndaki Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne işaretçisi.  
  
 `TimerOrWaitFired`  
 [in] `true` bekleme işlemi zaman aşımına uğradı veya sinyal edildiyse `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `WAITORTIMERCALLBACK`Noktaların bir geri çağırma işlevi olduğu ve barındırma uygulamasının yazarı tarafından uygulanması gereken işlev.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorWks.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
