---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 811106216e1e454ddf342af1578f74c80ba2acc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138825"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider:: GetMethodProps Yöntemi
Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.  
  
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
 'ndaki Hangi bilgilerin alınacağı konusunda yöntemde göreli bir sanal adres.  
  
 `pMethodToken`  
 dışı Metodun meta veri belirtecine yönelik bir işaretçi.  
  
 `pcGenericParams`  
 dışı Bu metotla ilişkili genel parametre sayısına yönelik bir işaretçi.  
  
 `cbSignature`  
 'ndaki `signature` dizisinin boyutu. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 dışı Döndürülen `signature` dizisinin boyutuna yönelik bir işaretçi.  
  
 `signature`  
 dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemin `signature` dizisinin gereken boyutunu almak için, `cbSignature` bağımsız değişkenini 0 olarak ayarlayın ve **null**olarak `signature`. Yöntemi döndürüldüğünde, `pcbSignature` `signature` dizisi için gerekli olan bayt sayısını içerir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
