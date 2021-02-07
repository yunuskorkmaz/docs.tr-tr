---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetMethod yöntemi'
title: ISymUnmanagedScope::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 7dfc5f41d849d47bfaf600e40a7ccc9dd45da676
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763403"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="a6fc2-103">ISymUnmanagedScope::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6fc2-103">ISymUnmanagedScope::GetMethod Method</span></span>

<span data-ttu-id="a6fc2-104">Bu kapsamı içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="a6fc2-104">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6fc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6fc2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6fc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6fc2-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="a6fc2-107">dışı Döndürülen [ıdimunmanagedmethod](isymunmanagedmethod-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6fc2-107">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6fc2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6fc2-108">Return Value</span></span>  

 <span data-ttu-id="a6fc2-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a6fc2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6fc2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6fc2-110">Requirements</span></span>  

 <span data-ttu-id="a6fc2-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a6fc2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fc2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6fc2-112">See also</span></span>

- [<span data-ttu-id="a6fc2-113">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6fc2-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
