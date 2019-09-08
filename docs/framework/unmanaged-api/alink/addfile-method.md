---
title: AddFile Metodu
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787693"
---
# <a name="addfile-method"></a>AddFile Metodu
Derlemeye dosya ekler. , İlişkisiz modüller oluşturmak için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Artırılması için derlemenin benzersiz KIMLIĞI.  
  
 `pszFilename`  
 Eklenecek dosyanın tam adı.  
  
 `dwFlags`  
 `ffContainsNoMetaData` Ve`ffWriteable`gibi com+ FileDef bayrakları. `dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.  
  
 `pEmitter`  
 Gerekirse meta verileri yayan için kullanılacak [ımetadatayayma arabirimi](../metadata/imetadataemit-interface.md) arabirimi.  
  
 `pFileToken`  
 Eklenen dosyanın benzersiz KIMLIĞININ depolanacağı işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
