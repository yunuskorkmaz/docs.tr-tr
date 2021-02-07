---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: Initialize yöntemi'
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
ms.openlocfilehash: cf7f5df3efed7823fc36bd6c9fc56e0c49d17443
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763884"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize Yöntemi

Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.  
  
> [!NOTE]
> Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir okuyucu yönteminden önce çağrılmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parametreler  

 `importer`  
 'ndaki Bu okuyucunun ilişkilendirileceği meta veri alma arabirimi.  
  
 `filename`  
 'ndaki Modülün dosya adı. `pIStream`Bunun yerine parametresini kullanabilirsiniz.  
  
 `searchPath`  
 'ndaki Arama yolu. Bu parametre isteğe bağlıdır.  
  
 `pIStream`  
 'ndaki Dosya akışı, filename parametresine alternatif olarak kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  

 Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` . `searchPath`Parametresi isteğe bağlıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
