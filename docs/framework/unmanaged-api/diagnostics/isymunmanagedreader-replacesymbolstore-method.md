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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615455"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
Var olan sembol deposunu bir Delta sembol deposu ile değiştirir. Bu yöntem [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.  
  
> [!NOTE]
> Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` . `filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir. `pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parametreler  
 `filename`  
 'ndaki Sembol deposunu içeren dosyanın adı.  
  
 `pIStream`  
 'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)
