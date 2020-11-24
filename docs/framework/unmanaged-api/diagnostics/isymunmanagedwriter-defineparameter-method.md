---
title: ISymUnmanagedWriter::DefineParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: c5e36443295395997303cb94202f534a83d086f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677875"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter Yöntemi

Geçerli yöntemde tek bir parametre tanımlar. Parametre türü, yöntemin imzasında parametre konumundan (sıra) alınır.  
  
 Belirli bir yöntemin meta verilerinde Parametreler tanımlanmışsa, bu yöntemi kullanarak bunları tekrar tanımlamanız gerekmez. Sembol okuyucuları, sembol deposunu denetlemeden önce parametrelerin normal meta verilerini denetmelidir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametreler  

 `name`  
 'ndaki Parametre adı.  
  
 `attributes`  
 'ndaki Parametre öznitelikleri.  
  
 `sequence`  
 'ndaki Parametre imzası.  
  
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
