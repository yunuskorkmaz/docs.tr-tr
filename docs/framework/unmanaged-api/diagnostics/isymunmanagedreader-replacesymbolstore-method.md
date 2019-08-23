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
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939036"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
Var olan sembol deposunu bir Delta sembol deposu ile değiştirir. Bu yöntem [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.  
  
> [!NOTE]
> `filename` Ya`pIStream` da parametrelerinden yalnızca birini belirtmeniz gerekir. `filename` Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir. Belirtilmişse, mağaza <xref:System.Runtime.InteropServices.ComTypes.IStream>içindeki verilerle güncelleştirilir. `pIStream`  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parametreler  
 `filename`  
 'ndaki Sembol deposunu içeren dosyanın adı.  
  
 `pIStream`  
 'ndaki `filename` Parametresi için alternatif olarak kullanılan dosya akışı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
