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
ms.openlocfilehash: 3fa94094ad066496cc8a1fc4dd2ccb0ee16b5aac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675847"
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
