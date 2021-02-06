---
description: 'Daha fazla bilgi edinin: AddFile yöntemi'
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
ms.openlocfilehash: 5e1253587298b2c1559c72dced43ec70dc169090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638632"
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
 Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` . `dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.  
  
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
