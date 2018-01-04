---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6116ee89cb643cc0010ef2c8a463fa131777584e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>ISymENCUnmanagedMethod::GetSourceExtentInDocument Metodu
Alır en küçük satırı ve en büyük satır sonu yöntemi için özel bir belgede başlatın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `document`  
 [in] Belge için bir işaretçi.  
  
 `pstartLine`  
 [out] Bir işaretçi bir `ULONG32` başlangıç satırını alır.  
  
 `pendLine`  
 [out] Bir işaretçi bir `ULONG32` satır sonu alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymENCUnmanagedMethod Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
