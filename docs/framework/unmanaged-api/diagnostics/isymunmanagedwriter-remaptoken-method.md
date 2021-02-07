---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedwriter:: RemapToken Yöntemi'
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
ms.openlocfilehash: c065d42c3d2749f0262fdd81a74de918274ba67d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762090"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>ISymUnmanagedWriter::RemapToken Yöntemi

Meta veri yayıldığından, meta veri belirtecinin yeniden eşlenme olduğunu sembol yazıcısına bildirir. Sembol yazıcısı eski belirteci sembol deposu içinde depolamışsa, bu, saklı belirteci yeni değerle güncelleştirmeli ya da okuma aşamasında yeniden eşlemek üzere ilgili sembol okuyucusunun eşlemesini kaydetmesi gerekir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Parametreler  

 `oldToken`  
 'ndaki Yeniden eşlenen meta veri belirteci.  
  
 `newToken`  
 'ndaki Yeniden eşlenen yeni meta veri belirteci `oldToken` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
