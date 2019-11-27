---
title: AddFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446671"
---
# <a name="addfile2-method"></a>AddFile2 Yöntemi
Derlemeye dosya ekler. , İlişkisiz modüller oluşturmak için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dosyanın eklendiği derlemenin KIMLIĞI.  
  
 `pszFilename`  
 Eklenecek dosyanın adı.  
  
 `dwFlags`  
 `ffContainsNoMetaData` ve `ffWriteable`gibi COM+ `FileDef` bayrakları. `dwFlags` [DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.  
  
 `pEmitter`  
 Arabirim arabirimine [IMetaDataEmit2](../metadata/imetadataemit2-interface.md) arabirimi.  
  
 `pFileToken`  
 Eklenmekte olan dosyanın KIMLIĞINI alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
