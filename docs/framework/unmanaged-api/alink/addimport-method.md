---
description: 'Daha fazla bilgi edinin: AddImport yöntemi'
title: AddImport Metodu
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 9dca26501e66313b0932caf1288db7c909154e1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638606"
---
# <a name="addimport-method"></a>AddImport Metodu

Derlemeye içeri aktarmalar ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Artırılması için derlemenin benzersiz KIMLIĞI.  
  
 `ImportToken`  
 İçeri aktarılacak dosyanın [ImportFile yönteminden](importfile-method.md)ALıNAN benzersiz kimliği.  
  
 `dwFlags`  
 Ve gibi COM+ FileDef bayrakları `ffContainsNoMetaData` `ffWriteable` . `dwFlags`[DefineFile yöntemine](../metadata/imetadataassemblyemit-definefile-method.md)geçirilir.  
  
 `pFileToken`  
 Elde edilen dosyanın KIMLIĞINI alan belirteç işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
