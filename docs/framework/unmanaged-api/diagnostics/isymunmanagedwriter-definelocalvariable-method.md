---
title: ISymUnmanagedWriter::DefineLocalVariable Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c62ad58cd7ad1bd752d5958a5630dc7a019131e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645450"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable Yöntemi
Tek bir değişken, geçerli sözlü kapsamda tanımlar. Bu yöntem, bir kapsam boyunca birden çok havaalanlarından olan aynı ada sahip bir değişken için birden çok kez çağrılabilir. Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri örtüşmemelidir.  
  
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
 [in] Bir işaretçi bir `WCHAR` , yerel değişken adını tanımlar.  
  
 `attributes`  
 [in] Yerel değişken öznitelikleri.  
  
 `cSig`  
 [in] A `ULONG32` bayt cinsinden boyutunu belirten `signature` arabellek.  
  
 `signature`  
 [in] Yerel değişken imzası.  
  
 `addrKind`  
 [in] Adres türü.  
  
 `addr1`  
 [in] Parametre belirtimine ilk adresi.  
  
 `addr2`  
 [in] Parametre belirtimine ikinci adresi.  
  
 `addr3`  
 [in] Parametre belirtimine üçüncü adresi.  
  
 `startOffset`  
 [in] Değişken için başlangıç uzaklığı. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır. Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.  
  
 `endOffset`  
 [in] Değişken için bitiş uzaklığı. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır. Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
