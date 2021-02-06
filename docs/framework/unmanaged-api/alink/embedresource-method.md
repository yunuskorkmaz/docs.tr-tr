---
description: 'Daha fazla bilgi edinin: EmbedResource yöntemi'
title: EmbedResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: f7896172e7416048352788caf7e092096924b7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638359"
---
# <a name="embedresource-method"></a>EmbedResource Yöntemi

Gömülü bir kaynak bildirir. Bu yöntem, kaynağı aslında eklemez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `FileToken`  
 Kaynağı içeren dosyanın belirteç veya derleme KIMLIĞI.  
  
 `pszResourceName`  
 Kaynağın adı.  
  
 `dwOffset`  
 Kaynak RVA 'dan konum.  
  
 `dwFlags`  
 Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` . Bu bayraklar [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
