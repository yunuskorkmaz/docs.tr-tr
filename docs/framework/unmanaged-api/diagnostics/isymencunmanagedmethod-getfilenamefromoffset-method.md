---
description: 'Şu konuda daha fazla bilgi edinin: ıvmencunmanagedmethod:: Getfilenamefromscope yöntemi'
title: ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 1322e55f115958a2f4b2634dfa25eff127167d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738006"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi

Bir uzaklığa ilişkin dosya adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwOffset`  
 'ndaki `ULONG32` Bu, sapmayı içeren bir.  
  
 `cchName`  
 'ndaki `ULONG32` Arabellek boyutunu belirten bir `szName` .  
  
 `pcchName`  
 dışı `ULONG32` Dosya adlarını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.  
  
 `szName`  
 dışı Dosya adlarını içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](isymencunmanagedmethod-interface.md)
