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
ms.openlocfilehash: 07d2de5d12fd769cb5cce243d9e721bb6fc185a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615481"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize Yöntemi
Sembol okuyucuyu, bu okuyucunun ilişkilendirildiği meta veri alma arabirimiyle birlikte modülün dosya adı ile başlatır.  
  
> [!NOTE]
> Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir okuyucu yönteminden önce çağrılmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
