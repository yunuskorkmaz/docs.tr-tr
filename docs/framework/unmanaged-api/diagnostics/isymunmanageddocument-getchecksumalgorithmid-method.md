---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c5861f598a653f433ffaa611d6f1be3ba6f69a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585610"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a>ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu
Sağlama algoritması tanımlayıcısını alır veya hiç sağlama toplamı sıfırlardan GUİD'sini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 [out] Sağlama algoritması tanıtıcısını alan bir değişken için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
