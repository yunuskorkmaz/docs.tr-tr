---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetDocumentVersion yöntemi'
title: ISymUnmanagedReader::GetDocumentVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: e6877a10f0c285186330b320c9b614939f4d9e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800207"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion Metodu

Belirtilen belgenin belirtilen sürümünü alır. Belge sürümü 1 ' de başlar ve belge [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemi kullanılarak her güncelleştirildiği zaman artırılır. `pbCurrent`Parametresi ise `true` , bu belgenin en son sürümüdür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pDoc`  
 'ndaki Belirtilen belge.  
  
 `version`  
 dışı Belirtilen belgenin sürümünü alan bir değişkene yönelik işaretçi.  
  
 `pbCurrent`  
 dışı `true` Belgenin en son sürümü ise veya `false` en son sürüm değilse alan bir değişkene yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
