---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetMethodsFromDocumentPosition yöntemi'
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 033bdce2cd70e578ebd3be8a187d983a2c58b99d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764040"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi

Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `document`  
 'ndaki Belirtilen belge.  
  
 `line`  
 'ndaki Belirtilen belgenin satırı.  
  
 `column`  
 'ndaki Belirtilen belgenin sütunu.  
  
 `cMethod`  
 'ndaki `pRetVal` Dizinin boyutu.  
  
 `pcMethod`  
 dışı Dizide döndürülen öğelerin sayısını alan bir değişken işaretçisi `pRetVal` .  
  
 `pRetVal`  
 dışı Her biri, kesme noktasını içeren bir yöntemi temsil eden bir [ıstreamunmanagedmethod](isymunmanagedmethod-interface.md) nesnesine işaret eden bir işaretçiler dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
