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
ms.openlocfilehash: 1553e616f60b4f05c06b6457d47454dfb4bc2eb7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614779"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize Yöntemi
Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.  
  
 Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir yazıcı yönteminden önce çağrılmalıdır. Bazı yazarlar bir dosya adı gerektirebilir. Ancak, dosya adını kullanmayan yazarlar üzerinde herhangi bir olumsuz etkisi olmadan bu yönteme her zaman bir dosya adı geçirebilirsiniz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Parametreler  
 `emitter`  
 'ndaki Meta veri verici arabirimine yönelik bir işaretçi.  
  
 `filename`  
 'ndaki Hata ayıklama simgelerinin yazıldığı dosya adı. Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.  
  
 `pIStream`  
 'ndaki Belirtilmişse, sembol yazıcı sembolleri <xref:System.Runtime.InteropServices.ComTypes.IStream> parametresinde belirtilen dosya yerine verilen öğesine yayar `filename` . `pIStream`Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` Bu bir tam yeniden oluşturma ise `false`Bu bir artımlı derleme ise.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [Initialize2 Yöntemi](isymunmanagedwriter-initialize2-method.md)
