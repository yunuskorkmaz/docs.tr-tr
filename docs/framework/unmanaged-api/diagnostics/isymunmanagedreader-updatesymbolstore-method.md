---
title: ISymUnmanagedReader::UpdateSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: 6670d985eed4c55550b23d3f4110ee20f3b75661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675834"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore Yöntemi

Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir. Bu yöntem, sembol deposunu değişimleri ile orijinal taşınabilir yürütülebilir (PE) dosyası eşleşecek şekilde güncelleştirmek için Düzenle ve devam et senaryolarında kullanılır.  
  
> [!NOTE]
> Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` . `filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir. `pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT UpdateSymbolStore (  
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
