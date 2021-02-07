---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: SetScopeRange Yöntemi'
title: ISymUnmanagedWriter::SetScopeRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: 43cfbeaa0d366b9f2d25068cfa7b91a0fea8ac59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762064"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange Yöntemi

Belirtilen sözcük temelli kapsamın fark aralığını tanımlar. Kapsam, yeni geçerli kapsam haline gelir ve bir kapsam yığınına gönderilir. Kapsamlar bir hiyerarşi oluşturmalıdır. Eşdüzey öğelerinin örtüşmesine izin verilmez.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>Parametreler  

 `scopeId`  
 'ndaki Kapsamın kapsam tanımlayıcısı.  
  
 `startOffset`  
 'ndaki Metodun başındaki sözcük temelli kapsamdaki ilk yönergenin bayt cinsinden değeri.  
  
 `endOffset`  
 'ndaki Metodun başındaki sözcük temelli kapsamdaki son yönergenin bayt cinsinden değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  

 [Ivmunmanagedwriter:: OpenScope](isymunmanagedwriter-openscope-method.md) , bir `ISymUnmanagedWriter::SetScopeRange` kapsamın başlangıç ve bitiş sapmasını daha sonra tanımlamak için ile birlikte kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor. Bu durumda, `ISymUnmanagedWriter::OpenScope` ve [ıvmunmanagedwriter:: CloseScope](isymunmanagedwriter-closescope-method.md) öğesine geçirilen uzaklıklar yok sayılır. Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
