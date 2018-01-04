---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
Aynı işlevleri [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verilerini yapmak için bir sonlandırma null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`. Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen değerinden `MAX_PATH`.  
  
 Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Dönüş Değeri  
 Döndürür `HRESULT`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter4 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
