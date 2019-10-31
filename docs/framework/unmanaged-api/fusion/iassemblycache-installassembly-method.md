---
title: IAssemblyCache::InstallAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
ms.openlocfilehash: ec08c786992996ec6f44038ff3c1596cada88484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127077"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly Yöntemi
Belirtilen derlemeyi genel derleme önbelleğine yüklenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwFlags`  
 'ndaki Fusion. IDL içinde tanımlanan bayraklar. Aşağıdaki değerler desteklenir:  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pszManifestFilePath`  
 'ndaki Yüklenecek derleme için bildirimin yolu.  
  
 `pRefData`  
 'ndaki Yükleme için veri içeren bir [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyCache Arabirimi](iassemblycache-interface.md)
