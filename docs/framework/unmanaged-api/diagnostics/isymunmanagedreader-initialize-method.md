---
title: ISymUnmanagedReader::Initialize Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669981"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize Yöntemi
Bu okuyucu modülü dosya adının yanı sıra, ile ilişkili meta verileri alma arabirimiyle sembol okuyucu başlatır.  
  
> [!NOTE]
>  Bu yöntem yalnızca bir kez çağrılabilir ve diğer okuyucu yöntemleri önce çağrılmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parametreler  
 `importer`  
 [in] İle bu okuyucu ilişkilendirilecek olan meta verileri alma arabirim.  
  
 `filename`  
 [in] Modül dosya adı. Kullanabileceğiniz `pIStream` parametresi yerine.  
  
 `searchPath`  
 [in] Arama yolu. Bu parametre isteğe bağlıdır.  
  
 `pIStream`  
 [in] Filename parametresi bir alternatif olarak kullanılan dosya akışı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca birini belirtmeniz gereken `filename` veya `pIStream` parametreleri, her ikisini birden değil. `searchPath` Parametresi isteğe bağlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
