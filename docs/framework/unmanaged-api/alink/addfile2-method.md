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
ms.openlocfilehash: cff6707496c7d9657796deb8bf6fa9165ff295a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717090"
---
# <a name="addfile2-method"></a>AddFile2 Yöntemi

Derlemeye dosya ekler. , İlişkisiz modüller oluşturmak için de kullanılabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Ve gibi COM+ `FileDef` bayrakları `ffContainsNoMetaData` `ffWriteable` . `dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.  
  
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
