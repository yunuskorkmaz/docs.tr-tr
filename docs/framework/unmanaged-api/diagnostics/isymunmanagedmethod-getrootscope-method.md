---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetRootScope Yöntemi'
title: ISymUnmanagedMethod::GetRootScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: b1e490d8e0c5e0d60143202dd0291237685c950f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710016"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="85f54-103">ISymUnmanagedMethod::GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85f54-103">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="85f54-104">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="85f54-104">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="85f54-105">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="85f54-105">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f54-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f54-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f54-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85f54-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="85f54-108">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="85f54-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85f54-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="85f54-109">Return Value</span></span>  

 <span data-ttu-id="85f54-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="85f54-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f54-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85f54-111">Requirements</span></span>  

 <span data-ttu-id="85f54-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="85f54-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f54-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f54-113">See also</span></span>

- [<span data-ttu-id="85f54-114">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f54-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
