---
description: 'Daha fazla bilgi edinin: ISymUnmanagedReader2:: GetSymAttributePreRemap yöntemi'
title: ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 843a3d2d2a568fdff83d2e416fff426daad14645
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763637"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap Metodu

Özel bir özniteliği adına göre alır. Meta veri özel özniteliklerinin aksine, bu öznitelikler sembol deposunda tutulur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `parent`  
 'ndaki Üst öğenin meta veri belirteci.  
  
 `name`  
 'ndaki Adını içeren bir işaretçisi `WCHAR` .  
  
 `cBuffer`  
 'ndaki `ULONG32` Dizi boyutunu belirten bir `buffer` .  
  
 `pcBuffer`  
 dışı `ULONG32` Öznitelik baytlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.  
  
 `buffer`  
 dışı Öznitelik baytlarını alan arabelleğin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedReader2 Arabirimi](isymunmanagedreader2-interface.md)
