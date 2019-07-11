---
title: ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 525ec4828fb942aeb447940ea68a523cd7c69140
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736732"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
Mevcut simge deposu delta sembol deposu ile değiştirir. Bu yöntem benzer [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemi dışında verilen delta güncelleştirme yerine tam değiştirme olarak görev yapar.  
  
> [!NOTE]
>  Yalnızca birini belirtmeniz gerekir `filename` veya `pIStream` parametreleri, her ikisini birden değil. Varsa `filename` belirtilirse, bu dosyada simgelerle sembol deposundaki güncelleştirilir. Varsa `pIStream` belirtilirse, depolama, verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parametreler  
 `filename`  
 [in] Sembol deposu içeren dosyanın adı.  
  
 `pIStream`  
 [in] Alternatif olarak kullanılan dosya akışı `filename` parametresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
