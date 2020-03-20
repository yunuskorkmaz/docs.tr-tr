---
title: ISymUnmanagedWriter3::OpenMethod2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178323"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a>ISymUnmanagedWriter3::OpenMethod2 Yöntemi
Bir yöntem açar ve görüntüde gerçek bölüm ofset sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `method`  
 [içinde] Açılacak yöntem için meta veri belirteci.  
  
 `isect`  
 [içinde] Görüntüdeki bölüm ofset.  
  
 `offset`  
 [içinde] Görüntüdeki ofset.  
  
## <a name="return-value"></a>Dönüş Değeri  
 yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [OpenMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
