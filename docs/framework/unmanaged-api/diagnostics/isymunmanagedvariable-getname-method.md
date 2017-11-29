---
title: ISymUnmanagedVariable::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a86a93db6058a8fda42e837388f7fa4cf5c765c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetname-method"></a>ISymUnmanagedVariable::GetName Metodu
Bu değişken adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Arabelleğin uzunluğu, `pcchName` parametresi işaret eder.  
  
 `pcchName`  
 [out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil adını içerecek şekilde gerekli arabellek boyutunu alır.  
  
 `szName`  
 [out] Adını depolar arabelleği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isymunmanagedvariable arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
