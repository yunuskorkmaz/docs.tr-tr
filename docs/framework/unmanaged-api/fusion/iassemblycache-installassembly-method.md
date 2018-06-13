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
ms.openlocfilehash: 726a4ed8ee3d451687e0af671d948eb7648f7f58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430030"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly Yöntemi
Belirtilen derleme genel derleme önbelleğinde yükler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Fusion.idl içinde tanımlı bayrak. Aşağıdaki değerleri desteklenir:  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)  
  
 `pszManifestFilePath`  
 [in] Bildirim yüklemek derleme yolu.  
  
 `pRefData`  
 [in] A [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) yükleme için verileri içeren yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IAssemblyCache Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
