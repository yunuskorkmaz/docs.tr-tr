---
title: "ISymUnmanagedWriter::DefineLocalVariable Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e454aa2c2dd8ceb8f8dbbc03bdd1e70e8a800de2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable Yöntemi
Tek bir değişken geçerli sözcük kapsamda tanımlar. Bu yöntem, birden çok ev bir kapsama sahip aynı ada sahip bir değişken için birden çok kez çağrılabilir. Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri çakışmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 [in] Bir işaretçi bir `WCHAR` yerel değişken adını tanımlar.  
  
 `attributes`  
 [in] Yerel değişken öznitelikleri.  
  
 `cSig`  
 [in] A `ULONG32` bayt cinsinden boyutu belirten `signature` arabellek.  
  
 `signature`  
 [in] Yerel değişken imzası.  
  
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
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Isymunmanagedwriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [DefineGlobalVariable yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [DefineLocalVariable2 yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
