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
ms.openlocfilehash: a3ae474a73f4c8e4b98c4b2bc5d04e55bcae6874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128661"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>IHostMemoryManager::NeedsVirtualAddressSpace Yöntemi
Ana bilgisayarı ortak dil çalışma zamanının (CLR) belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 `NeedsVirtualAddressSpace` yöntemi bir geri çağırma yöntemidir ve barındırma uygulamasının yazarı tarafından uygulanmalıdır. CLR tarafından çağırılır.  
  
 Ana bilgisayar CLR 'nin belirtilen belleği kullanmasını istemiyorsanız, bir E_OUTOFMEMORY HRESULT döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
