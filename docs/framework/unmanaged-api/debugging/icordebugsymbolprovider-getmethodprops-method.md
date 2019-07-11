---
title: ICorDebugSymbolProvider::GetMethodProps yöntemi
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6971c7991f5e54973d96d9b3f662b54be564d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771338"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps yöntemi
Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri belirteci ve kendi genel parametreler hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `codeRVA`  
 [in] Göreli sanal adres hakkında bilgi alınacak yöntemi içinde.  
  
 `pMethodToken`  
 [out] Yöntemin meta veri belirteci için bir işaretçi.  
  
 `pcGenericParams`  
 [out] Bu yöntemle ilişkili genel parametre sayısı için bir işaretçi.  
  
 `cbSignature`  
 [in] Boyutu `signature` dizisi. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 [out] Boyut döndürülen işaretçi `signature` dizisi.  
  
 `signature`  
 [out] Tüm genel parametreler TypeSpec'te imzalarını tutan arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemin gerekli boyutunu almak için `signature` ayarlayın, dizi `cbSignature` bağımsız değişkeni 0 ve `signature` için **null**. Yöntem döndürüldüğünde `pcbSignature` için gereken bayt sayısını içerir `signature` dizisi.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
