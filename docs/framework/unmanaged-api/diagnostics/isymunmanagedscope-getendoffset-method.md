---
title: ISymUnmanagedScope::GetEndOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 14e747e81e467019d464212e75513bdf98344916
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678369"
---
# <a name="isymunmanagedscopegetendoffset-method"></a>ISymUnmanagedScope::GetEndOffset Metodu

Bu kapsamın bitiş sapmasını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRetVal`  
 dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedScope Arabirimi](isymunmanagedscope-interface.md)
- [GetStartOffset Yöntemi](isymunmanagedscope-getstartoffset-method.md)
