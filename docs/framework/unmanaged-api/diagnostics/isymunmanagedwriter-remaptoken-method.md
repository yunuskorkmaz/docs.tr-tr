---
title: ISymUnmanagedWriter::RemapToken Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ec3f94d290423130e3718b32cd8058f59d797d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694522"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>ISymUnmanagedWriter::RemapToken Yöntemi
Sembol yazıcı meta veriler gösteriliyordu gibi meta veri belirteci eşleştirilmiş bildirir. Sembol yazıcı, sembol deposundaki eski belirteç saklanan güncelleştirmek ya da yeni bir değer veya saklı belirteciyle okuma aşamasında yeniden eşlemek karşılık gelen sembol Okuyucu için haritada kaydetmelisiniz gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `oldToken`  
 [in] Eşlendi meta veri belirteci.  
  
 `newToken`  
 [in] Hangi yeni meta veri belirteci `oldToken` eşlendi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
