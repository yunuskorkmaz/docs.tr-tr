---
title: ISymUnmanagedReader::GetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: b7e2814e56765037b69c6ef7ca0ba610dd7d3c95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614935"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>ISymUnmanagedReader::GetSymAttribute Yöntemi
Özel bir özniteliği adına göre alır. Meta veri özel özniteliklerinin aksine, bu özel öznitelikler sembol deposunda tutulur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki Özniteliği istenen nesnenin meta veri belirteci.  
  
 `name`  
 'ndaki Alınacak özniteliği belirten değişkene yönelik bir işaretçi.  
  
 `cBuffer`  
 'ndaki `buffer`Dizinin boyutu.  
  
 `pcBuffer`  
 dışı Öznitelik verilerinin uzunluğunu alan değişkene yönelik bir işaretçi.  
  
 `buffer`  
 dışı Öznitelik verilerini alan değişkene yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
