---
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: d9a7b18e90a3038c1ffb634ccc7315143875c809
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441922"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
Bir uzaklığa ilişkin satır bilgilerini alır. Eğer fark parametresi ( `dwOffset` ) bir sıra noktası değilse, bu yöntem önceki uzaklığa ilişkin satır bilgilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwOffset`  
 'ndaki `ULONG32`Bu, sapmayı içeren bir.  
  
 `pline`  
 dışı Satırı alan bir işaretçisi `ULONG32` .  
  
 `pcolumn`  
 dışı Sütununu alan öğesine yönelik bir işaretçi `ULONG32` .  
  
 `pendLine`  
 dışı `ULONG32`Bitiş satırını alan bir işaretçisi.  
  
 `pendColumn`  
 dışı Bitiş sütununu alan öğesine yönelik bir işaretçi `ULONG32` .  
  
 `pdwStartOffset`  
 dışı `ULONG32`İlişkili dizi noktasını alan öğesine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](isymencunmanagedmethod-interface.md)
