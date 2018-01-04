---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c86b2988d414d091bc23d29bd79f518a756d688
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a>ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu
Yerel değişkenler sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mdMethodToken`  
 [in] Yöntemleri meta veri simgesi.  
  
 `pcLocals`  
 [out] Bir işaretçi bir `ULONG32` karakter yerel değişkenler sayı içerecek şekilde gerekli arabellek boyutunu alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedENCUpdate Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
