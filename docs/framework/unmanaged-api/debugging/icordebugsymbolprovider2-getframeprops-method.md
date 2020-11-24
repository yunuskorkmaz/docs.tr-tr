---
title: 'ICorDebugSymbolProvider2:: GetFrameProps yöntemi'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ba1fd104c35b6e6dfdfd771f71eb19f8d532a1d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672017"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2:: GetFrameProps yöntemi

Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `codeRva`  
 'ndaki Kod göreli sanal adresi.  
  
 `pCodeStartRva`  
 dışı Metodun başlangıç göreli sanal adresine yönelik bir işaretçi.  
  
 `pParentFrameStartRva`  
 dışı Çerçevenin başlangıç göreli sanal adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider2 Arabirimi](icordebugsymbolprovider2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
