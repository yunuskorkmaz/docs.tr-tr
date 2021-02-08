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
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="856cd-103">ISymUnmanagedDispose::Destroy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="856cd-103">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="856cd-104">Alttaki nesnenin tüm iç başvuruları serbest bırakmaya ve sonraki yöntem çağrılarında hata döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="856cd-104">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856cd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="856cd-105">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="856cd-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="856cd-106">Return Value</span></span>  

 <span data-ttu-id="856cd-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="856cd-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="856cd-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="856cd-108">Requirements</span></span>  

 <span data-ttu-id="856cd-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="856cd-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856cd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="856cd-110">See also</span></span>

- [<span data-ttu-id="856cd-111">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="856cd-111">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
