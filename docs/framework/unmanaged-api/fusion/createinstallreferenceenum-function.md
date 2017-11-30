---
title: "CreateInstallReferenceEnum İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateInstallReference
helpviewer_keywords: CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07c7ec72a66b37798e6e2af523bb024e9dd63d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum İşlevi
Bir işaretçi alır bir [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) belirtilen derleme uygulamanın başvurular listesini temsil eden örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppRefEnum`  
 [out] Döndürülen `IInstallReferenceEnum` işaretçi.  
  
 `pName`  
 [in] [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) derleme başvurularını numaralandırmak için için tanımlar.  
  
 `dwFlags`  
 [in] Numaralandırıcının davranışını etkilemek bayraklar.  
  
 `pvReserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış. `pvReserved`bir null başvuru olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve Mscorwks.dll. Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iınstallreferenceenum arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [Iassemblyname arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Fusion genel statik işlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
