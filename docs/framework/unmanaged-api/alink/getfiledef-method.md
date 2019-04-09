---
title: GetFileDef Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184502"
---
# <a name="getfiledef-method"></a>GetFileDef Yöntemi
(Aksine ALink tarafından atanan simgesi) meta verilerinde kullanılan gerçek FileDef belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme kimliği.  
  
 `TargetFile`  
 Belirteç eklenen dosyanın AddFile yöntemi veya Addımport yöntemi alınan gibi.  
  
 `pScope`  
 FileDef belirtecini alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
