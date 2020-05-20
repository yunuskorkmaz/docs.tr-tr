---
title: ISymUnmanagedMethod::GetSourceStartEnd Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 25e797fdf563a01ab727f16e7173eec2552eeb27
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614428"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>ISymUnmanagedMethod::GetSourceStartEnd Yöntemi
Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır. İlk dizi konumu başlangıç ' dir ve ikinci dizi konumu son ' dır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
 `docs`  
 'ndaki Başlangıç ve bitiş kaynak belgeleri.  
  
 `lines`  
 'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş satırları.  
  
 `columns`  
 'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş sütunları.  
  
 `pRetVal`  
 [out] `true` pozisyonlar tanımlanmışsa; Aksi takdirde, `false` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedMethod Yöntemi](isymunmanagedmethod-interface.md)
