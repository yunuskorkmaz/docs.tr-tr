---
title: ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939691"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a>ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi
Değil derlendiği ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgileri güncelleniyor sağlar. Her deyim için bir delta izin verilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdMethodToken`  
 [in] Token metody meta veriler.  
  
 `pDeltas`  
 [in] Bir dizi `INT32` yöntem her bir dizi noktası için farkları gösteren değer.  
  
 `cDeltas`  
 [in] A `ULONG` boyutunu içeren `pDeltas` parametresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
