---
title: "IAssemblyCacheItem::CreateStream Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a24d9732a8e413b3cde0ac1c622743153ff6fd01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream Yöntemi
Belirtilen ada ve biçimi ile bir akış oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Fusion.idl içinde tanımlı bayrak.  
  
 `pszStreamName`  
 [in] Oluşturulacak Akış adı.  
  
 `dwFormat`  
 [in] Akışını dosya biçimi.  
  
 `dwFormatFlags`  
 [in] Fusion.idl içinde tanımlanan biçimi özgü bayraklar.  
  
 `ppIStream`  
 [out] Döndürülen adresini gösteren bir işaretçi <xref:IStream> örneği.  
  
 `puliMaxSize`  
 [isteğe bağlı] En büyük boyutu tarafından başvuruda bulunulan akışın `ppIStream`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IAssemblyCacheItem Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
