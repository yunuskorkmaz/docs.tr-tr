---
title: ISymUnmanagedWriter::DefineGlobalVariable Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 674089f8a1076342a2479c64e253b7dda53ade87
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615208"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable Yöntemi
Tek bir genel değişkeni tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 'ndaki `WCHAR`Genel değişken adını tanımlayan bir işaretçisi.  
  
 `attributes`  
 'ndaki Genel değişken öznitelikleri.  
  
 `cSig`  
 'ndaki `ULONG32`Bu, arabelleğin karakter cinsinden boyutunu belirten bir `signature` .  
  
 `signature`  
 'ndaki Genel değişken imzası.  
  
 `addrKind`  
 'ndaki Adres türü.  
  
 `addr1`  
 'ndaki Parametre belirtiminin ilk adresi.  
  
 `addr2`  
 'ndaki Parametre belirtiminin ikinci adresi.  
  
 `addr3`  
 'ndaki Parametre belirtiminin üçüncü adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
- [DefineLocalVariable Yöntemi](isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2 Yöntemi](isymunmanagedwriter2-defineglobalvariable2-method.md)
