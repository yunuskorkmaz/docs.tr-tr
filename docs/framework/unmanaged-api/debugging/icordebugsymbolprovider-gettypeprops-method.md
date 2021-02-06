---
description: ': ICorDebugSymbolProvider:: GetTypeProps yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: b6a4a5a68e1e377fa839940832dfc49574009641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659666"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider:: GetTypeProps yöntemi

Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tableRva`  
 'ndaki Vtable içindeki göreli bir sanal adres (RVA).  
  
 `cbSignature`  
 'ndaki `signature` Dizinin boyutu. Açıklamalar bölümüne bakın.  
  
 `pcbSignature`  
 dışı dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .  
  
 `signature`  
 dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  

 Türün dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın. Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetMethodProps Yöntemi](icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
