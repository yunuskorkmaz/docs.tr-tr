---
title: 'ICorDebugSymbolProvider:: GetMethodProps Yöntemi'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791576"
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

- [GetTypeProps Yöntemi](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
