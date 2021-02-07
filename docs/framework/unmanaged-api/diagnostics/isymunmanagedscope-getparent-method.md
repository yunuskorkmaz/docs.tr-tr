---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetParent yöntemi'
title: ISymUnmanagedScope::GetParent Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: c6a056c828bfaefd171ef3f0c546d93d30fb6863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763338"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="d0aea-103">ISymUnmanagedScope::GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0aea-103">ISymUnmanagedScope::GetParent Method</span></span>

<span data-ttu-id="d0aea-104">Bu kapsamın üst kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="d0aea-104">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0aea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0aea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0aea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0aea-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d0aea-107">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0aea-107">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0aea-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0aea-108">Return Value</span></span>  

 <span data-ttu-id="d0aea-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d0aea-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0aea-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0aea-110">Requirements</span></span>  

 <span data-ttu-id="d0aea-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0aea-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0aea-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0aea-112">See also</span></span>

- [<span data-ttu-id="d0aea-113">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0aea-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="d0aea-114">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0aea-114">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
