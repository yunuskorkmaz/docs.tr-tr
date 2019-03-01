---
title: AddFile Yöntemi
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
ms.openlocfilehash: c04bc008d0279601e90d13e6a57c52a458fca1d7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967886"
---
# <a name="addfile-method"></a>AddFile Yöntemi
Dosyaları derlemesine ekler. Ayrıca ilişkisiz modüller oluşturmak için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme genişletilmesi için benzersiz kimliği.  
  
 `pszFilename`  
 Eklenecek dosyasının tam adı.  
  
 `dwFlags`  
 COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`. `dwFlags` geçirilen [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) meta veriler yaymak için gerekiyorsa, kullanılacak arabirimi.  
  
 `pFileToken`  
 Eklenen dosyanın benzersiz kimliği depolanacağı için işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
