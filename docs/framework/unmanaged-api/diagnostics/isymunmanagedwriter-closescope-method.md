---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: CloseScope yöntemi'
title: ISymUnmanagedWriter::CloseScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: bb41e69955632d1e4d86250a63a9f25a7d1ae807
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762558"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope Yöntemi

Geçerli sözcük temelli kapsamı kapatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>Parametreler  

 `endOffset`  
 'ndaki Sözlü kapsamdaki son yönergenin sonundaki noktanın başından itibaren bayt cinsinden olan Aralık.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir kapsam kapatıldıktan sonra, içinde daha fazla değişken tanımlanamaz.  
  
 [Ityperunmanagedwriter:: OpenScope](isymunmanagedwriter-openscope-method.md) , daha sonra bir kapsamın başlangıç ve bitiş sapmasını tanımlamak için [ıvmunmanagedwriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor. Bu durumda, ve öğesine geçirilen uzaklıklar `ISymUnmanagedWriter::OpenScope` `ISymUnmanagedWriter::CloseScope` yok sayılır. Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
