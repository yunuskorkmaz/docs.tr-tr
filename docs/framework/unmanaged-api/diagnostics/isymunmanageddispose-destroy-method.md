---
description: 'Şu konuda daha fazla bilgi edinin: ı,:D estroy yöntemi'
title: ISymUnmanagedDispose::Destroy Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 3c13f90e08f2ba0dd7c70acc3321913b14195f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790210"
---
# <a name="isymunmanageddisposedestroy-method"></a>ISymUnmanagedDispose::Destroy Yöntemi

Alttaki nesnenin tüm iç başvuruları serbest bırakmaya ve sonraki yöntem çağrılarında hata döndürmesine neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDispose Arabirimi](isymunmanageddispose-interface.md)
