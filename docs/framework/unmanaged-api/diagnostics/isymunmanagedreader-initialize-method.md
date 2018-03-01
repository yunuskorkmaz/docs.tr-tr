---
title: "ISymUnmanagedReader::Initialize Yöntemi"
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
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize Yöntemi
Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.  
  
> [!NOTE]
>  Bu yöntem yalnızca bir kez çağrılabilir ve herhangi bir okuyucu yöntem önce çağrılmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `importer`  
 [in] İle bu okuyucu ilişkili olacağı meta verileri alma arabirimi.  
  
 `filename`  
 [in] Modülün dosya adı. Kullanabileceğiniz `pIStream` parametre yerine.  
  
 `searchPath`  
 [in] Arama yolu. Bu parametre isteğe bağlıdır.  
  
 `pIStream`  
 [in] Alternatif bir filename parametresi olarak kullanılan dosya akışı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca birini belirtmek zorunda `filename` veya `pIStream` parametreleri, her ikisini birden değil. `searchPath` Parametresi isteğe bağlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
