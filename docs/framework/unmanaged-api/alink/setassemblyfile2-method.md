---
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3882998d3155b49251fbe091b72ef11022ebfd2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540214"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 Yöntemi
Yeni bir derleme seçeneklerini ve adını ayarlar. İlişkisiz modüller oluşturmak, bu yöntemi çağırmanız gerekmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFilename`  
 Bildirim dosyasının adı.  
  
 `pEmitter`  
 [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) bu dosya için arabirim.  
  
 `afFlags`  
 Seçenekleri temsil ettiği [AssemblyFlags numaralandırması](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Yapılandırılan bir derleme için benzersiz kimlik alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
