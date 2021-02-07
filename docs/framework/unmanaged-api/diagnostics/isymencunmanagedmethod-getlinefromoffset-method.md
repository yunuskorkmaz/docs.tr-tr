---
description: 'Şu konuda daha fazla bilgi edinin: ıvmencunmanagedmethod:: Getlinefromsapmayı yöntemi'
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
ms.openlocfilehash: 18fe942b509340c89a4c3044e02bf8e9d952f91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737967"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi

Bir uzaklığa ilişkin satır bilgilerini alır. Eğer fark parametresi ( `dwOffset` ) bir sıra noktası değilse, bu yöntem önceki uzaklığa ilişkin satır bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki `ULONG32` Bu, sapmayı içeren bir.  
  
 `pline`  
 dışı Satırı alan bir işaretçisi `ULONG32` .  
  
 `pcolumn`  
 dışı Sütununu alan öğesine yönelik bir işaretçi `ULONG32` .  
  
 `pendLine`  
 dışı `ULONG32` Bitiş satırını alan bir işaretçisi.  
  
 `pendColumn`  
 dışı Bitiş sütununu alan öğesine yönelik bir işaretçi `ULONG32` .  
  
 `pdwStartOffset`  
 dışı `ULONG32` İlişkili dizi noktasını alan öğesine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymENCUnmanagedMethod Arabirimi](isymencunmanagedmethod-interface.md)
