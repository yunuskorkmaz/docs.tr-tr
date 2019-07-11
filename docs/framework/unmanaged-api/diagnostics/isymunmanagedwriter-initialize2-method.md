---
title: ISymUnmanagedWriter::Initialize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4087bdd82041152a9946a576e0eb96bf63f177c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777280"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 Yöntemi
İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar ve hata ayıklama sembolleri yazılacağı çıktı dosyası adını ayarlar. Bu yöntem Ayrıca, program veritabanı (PDB) dosyasının son konum ayarlamanıza olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametreler  
 `emitter`  
 [in] Meta veri verici arayüzü işaretçisi.  
  
 `tempfilename`  
 [in] Bir işaretçi bir `WCHAR` hata ayıklama sembolleri yazılır dosya adını içerir. Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse bu parametre yoksayılır.  
  
 `pIStream`  
 [in] Belirtilmişse sembolleri sembol yazıcı yayan verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi. `pIStream` Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` bu tam yeniden derleme; ise `false` bu artımlı bir derleme ise.  
  
 `finalfilename`  
 [in] Bir işaretçi bir `WCHAR` diğer bir deyişle yol dizesi PDB dosyası son konumunu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
