---
title: "ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppAssemblies`  
 [out] Numaralayıcı bir Icordebugassemblyenum arabirimi nesne adresini gösteren bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Bu `ICorDebugAssembly3` nesnesi bir kapsayıcıdır; Aksi halde, `S_FALSE`, ve numaralandırma boştur.  
  
## <a name="remarks"></a>Açıklamalar  
 Simgeler kapsanan derlemeleri numaralandırmak için gereklidir. Bunlar mevcut değil ise, yöntem döndürür `S_FALSE`, ve hiçbir geçerli Numaralandırıcı sağlanır.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugassembly3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
