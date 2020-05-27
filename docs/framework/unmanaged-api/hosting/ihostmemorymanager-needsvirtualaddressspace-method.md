---
title: IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804520"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi
Ana bilgisayarı ortak dil çalışma zamanının (CLR) belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `startAddress`  
 'ndaki Belleğin başlangıç adresi.  
  
 `size`  
 'ndaki Belleğin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 `NeedsVirtualAddressSpace`Yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır. CLR tarafından çağırılır.  
  
 Ana bilgisayar CLR 'nin belirtilen belleği kullanmasını istemiyor bir HRESULT E_OUTOFMEMORY döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
