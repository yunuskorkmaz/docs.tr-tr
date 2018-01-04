---
title: "ICorDebugSymbolProvider::GetTypeProps yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 118ae3991ea19b3158f4787a9944c28fb8208cbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider::GetTypeProps yöntemi
Göreli sanal adres (RAV) bir vtable verilen imza genel parametrelerinin sayısı gibi bir tür özellikleri hakkında bilgi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tableRva`  
 [in] Bir vtable'de göreli sanal adres (RAV).  
  
 `cbSignature`  
 [in] Boyutunu `signature` dizi. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 [out] [out] Döndürülen boyutu gösteren bir işaretçi `signature` dizi.  
  
 `signature`  
 [out] Tüm genel parametreler TypeSpec'te imzalarını tutan bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Tür gerekli boyutunu almak için `signature` dizisindeki, ayarlamak `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**. Yöntem döndüğünde `pcbSignature` için gereken bayt sayısını içerecektir `signature` dizi.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetMethodProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
