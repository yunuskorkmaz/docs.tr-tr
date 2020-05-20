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
ms.openlocfilehash: ac7559bd5431f45b266602404ddde9081aa2944d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614701"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi
Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar. Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir. Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki Yerel değişken adı.  
  
 `attributes`  
 'ndaki Yerel değişken öznitelikleri.  
  
 `sigToken`  
 'ndaki İmzanın meta veri belirteci.  
  
 `addrKind`  
 'ndaki Adres türü.  
  
 `addr1`  
 'ndaki Parametre belirtiminin ilk adresi.  
  
 `addr2`  
 'ndaki Parametre belirtiminin ikinci adresi.  
  
 `addr3`  
 'ndaki Parametre belirtiminin üçüncü adresi.  
  
 `startOffset`  
 'ndaki Değişkenin başlangıç boşluğu. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır. Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.  
  
 `endOffset`  
 'ndaki Değişkenin bitiş boşluğu. Bu parametre isteğe bağlıdır. 0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır. Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** Corsya. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter2 Arabirimi](isymunmanagedwriter2-interface.md)
- [DefineLocalVariable Yöntemi](isymunmanagedwriter-definelocalvariable-method.md)
