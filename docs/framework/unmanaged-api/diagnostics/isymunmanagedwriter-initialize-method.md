---
title: ISymUnmanagedWriter::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428041"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize Yöntemi
İle bu yazıcısı ilişkili olacağı meta verileri verici arabirimi ayarlar ve hata ayıklama simgeleri yazılacak çıktı dosyası adını ayarlar.  
  
 Bu yöntemi yalnızca bir kez çağrılabilir ve herhangi bir yazıcı yöntem önce çağrılmalıdır. Bazı yazıcıları bir dosya adı gerektirebilir. Ancak, bu yönteme dosya adını kullanmayın yazıcılarının negatif herhangi bir etkisi olmadan her zaman bir dosya adı geçirebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `emitter`  
 [in] Meta veri verici arayüzü için bir işaretçi.  
  
 `filename`  
 [in] Hata ayıklama simgeleri yazılmış olan dosya adı. Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse, bu parametre yoksayılır.  
  
 `pIStream`  
 [in] Belirtilmişse, simge yazan simgeleri yayma verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi. `pIStream` Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` bu tam bir yeniden oluşturma; ise `false` bu artımlı bir derleme ise.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
