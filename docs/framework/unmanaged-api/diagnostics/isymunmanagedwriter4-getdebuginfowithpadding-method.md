---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 4ac2cccfb17d82d8c62ad7db89161aa794825ae5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678283"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu

Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` . Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .  
  
 Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Dönüş Değeri  

 `HRESULT` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter4 Arabirimi](isymunmanagedwriter4-interface.md)
