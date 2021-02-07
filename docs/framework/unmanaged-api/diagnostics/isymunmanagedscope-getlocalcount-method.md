---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetLocalCount yöntemi'
title: ISymUnmanagedScope::GetLocalCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 987d161d273b12810988ef30acb703973098d29c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763454"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="4e8f7-103">ISymUnmanagedScope::GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e8f7-103">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="4e8f7-104">Bu kapsam içinde tanımlanan yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4e8f7-104">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8f7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e8f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e8f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e8f7-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="4e8f7-107">dışı `ULONG32` Yerel değişkenlerin sayısını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4e8f7-107">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e8f7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e8f7-108">Return Value</span></span>  

 <span data-ttu-id="4e8f7-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4e8f7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e8f7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e8f7-110">Requirements</span></span>  

 <span data-ttu-id="4e8f7-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4e8f7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8f7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e8f7-112">See also</span></span>

- [<span data-ttu-id="4e8f7-113">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e8f7-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
