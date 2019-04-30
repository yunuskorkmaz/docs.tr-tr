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
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700949"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize Yöntemi
İle bu yazıcısı ilişkilendirilecek olan meta veri verici arabirimi ayarlar ve hata ayıklama sembolleri yazılacağı çıktı dosyası adını ayarlar.  
  
 Bu yöntem yalnızca bir kez çağrılabilir ve diğer yazıcısı metotlarını önce çağrılmalıdır. Bazı yazarları, bir dosya adı gerektirebilir. Ancak, bu yönteme dosya adını kullanmayın yazıcılar negatif herhangi bir etkisi olmadan her zaman bir dosya adı geçirebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Parametreler  
 `emitter`  
 [in] Meta veri verici arayüzü işaretçisi.  
  
 `filename`  
 [in] Hata ayıklama sembolleri yazıldığı dosyanın adı. Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse bu parametre yoksayılır.  
  
 `pIStream`  
 [in] Belirtilmişse, simge yazıcı sembolleri yayar verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi. `pIStream` Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` bu tam yeniden derleme; ise `false` bu artımlı bir derleme ise.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
