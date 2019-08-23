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
ms.openlocfilehash: f2dceeb2f0b3aa9f3147157e77087dffbf2d5f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939021"
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
 'ndaki Modülün dosya adı. Bunun yerine `pIStream` parametresini kullanabilirsiniz.  
  
 `searchPath`  
 'ndaki Arama yolu. Bu parametre isteğe bağlıdır.  
  
 `pIStream`  
 'ndaki Dosya akışı, filename parametresine alternatif olarak kullanılır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  
 `filename` Ya`pIStream` da parametrelerinden yalnızca birini belirtmeniz gerekir. `searchPath` Parametresi isteğe bağlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
