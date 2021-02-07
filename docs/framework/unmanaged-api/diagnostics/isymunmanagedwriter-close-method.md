---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Close yöntemi'
title: ISymUnmanagedWriter::Close Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 02f4d8d4a232240160ad5065947282f40af42f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762636"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close Yöntemi

Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir. Sembol yazıcısını sembolleri kaydetmeden kapatmak için, bunun yerine [ıvmunmanagedwriter:: Abort](isymunmanagedwriter-abort-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)
