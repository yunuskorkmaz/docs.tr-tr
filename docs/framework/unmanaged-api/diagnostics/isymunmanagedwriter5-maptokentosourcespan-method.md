---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501683"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a>ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.  
  
 [OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a>Dönüş Değeri  
 `HRESULT` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter5 Arabirimi](isymunmanagedwriter5-interface.md)
