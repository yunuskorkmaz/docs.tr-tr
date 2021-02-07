---
description: 'Hakkında daha fazla bilgi edinin: ISymUnmanagedWriter2::D efineLocalVariable2 yöntemi'
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
ms.openlocfilehash: 169a086b8420b5dbe20af8e16b21d5b41a958ead
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761817"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi

Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar. Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir. Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
