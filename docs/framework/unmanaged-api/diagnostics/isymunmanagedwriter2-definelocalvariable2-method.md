---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi
Tek bir değişken geçerli sözcük kapsamda tanımlar. Bu yöntem, birden çok ev bir kapsama sahip aynı ada sahip bir değişken için birden çok kez çağrılabilir. Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri çakışmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 [in] Yerel değişken adı.  
  
 `attributes`  
 [in] Yerel değişken öznitelikleri.  
  
 `sigToken`  
 [in] İmza meta veri simgesi.  
  
 `addrKind`  
 [in] Adres türü.  
  
 `addr1`  
 [in] Parametre belirtimini ilk adresi.  
  
 `addr2`  
 [in] Parametre belirtimini ikinci adresi.  
  
 `addr3`  
 [in] Parametre belirtimini üçüncü adresi.  
  
 `startOffset`  
 [in] Değişken için başlangıç uzaklığı. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır. Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.  
  
 `endOffset`  
 [in] Değişken için bitiş uzaklığı. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır. Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isymunmanagedwriter2 arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [DefineLocalVariable yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
