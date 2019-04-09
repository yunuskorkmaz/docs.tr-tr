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
ms.openlocfilehash: 2caa9b48fc92a1b2e82f574d37d99758e19382c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133204"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi
Tek bir değişken, geçerli sözlü kapsamda tanımlar. Bu yöntem, bir kapsam boyunca birden çok havaalanlarından olan aynı ada sahip bir değişken için birden çok kez çağrılabilir. Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri örtüşmemelidir.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `name`  
 [in] Yerel değişken adı.  
  
 `attributes`  
 [in] Yerel değişken öznitelikleri.  
  
 `sigToken`  
 [in] Meta veri belirteci imzası.  
  
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
 **Üst bilgi:** CorSym.idl  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
