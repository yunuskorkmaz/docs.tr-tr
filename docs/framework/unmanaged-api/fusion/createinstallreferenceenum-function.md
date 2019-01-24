---
title: CreateInstallReferenceEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ec212bd999fe32e56a272c9bc3f39e19617a250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547780"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum İşlevi
Bir işaretçi alır bir [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) uygulamanın belirtilen bütünleştirilmiş kod başvuruları listesini temsil eden örneği.  
  
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
 [in] [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) derleme referanslarını listelemek istediğiniz tanımlar.  
  
 `dwFlags`  
 [in] Numaralandırıcının davranışını etkileyen bayraklar.  
  
 `pvReserved`  
 [in] Sonra genişletilebilmek için ayrılmış. `pvReserved` null bir başvuru olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye. Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IInstallReferenceEnum Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
