---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetSourceStartEnd yöntemi'
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
ms.openlocfilehash: 0d247427998970d86c1ad1ec37f5b32a846a6f7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709990"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>ISymUnmanagedMethod::GetSourceStartEnd Yöntemi

Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır. İlk dizi konumu başlangıç ' dir ve ikinci dizi konumu son ' dır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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

- [ISymUnmanagedMethod Arabirimi](isymunmanagedmethod-interface.md)
