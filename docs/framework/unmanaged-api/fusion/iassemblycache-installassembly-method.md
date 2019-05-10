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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 953a3123b00280484dd71965c34119e8eeacaf47
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623769"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly Yöntemi
Belirtilen derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Fusion.idl içinde tanımlanan bayraklar. Aşağıdaki değerleri desteklenir:  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)  
  
 `pszManifestFilePath`  
 [in] Yüklenecek derlemenin bildirimi yolu.  
  
 `pRefData`  
 [in] A [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) içeren yüklemesi için veri yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyCache Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
