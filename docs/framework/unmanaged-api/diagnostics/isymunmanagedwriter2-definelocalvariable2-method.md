---
title: ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53f02499bbc64f1502951ff9fbf16a848e77f0ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [DefineLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
