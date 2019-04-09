---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b3c9c637bdaa0d0e18dbfd9655790ff5ebd46f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141849"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="eaf1b-102">ISymUnmanagedScope::GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaf1b-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="eaf1b-103">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="eaf1b-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaf1b-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eaf1b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="eaf1b-106">[out] Bir işaretçi bir `ULONG32` , yerel değişkenleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="eaf1b-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaf1b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eaf1b-107">Return Value</span></span>  
 <span data-ttu-id="eaf1b-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="eaf1b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf1b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaf1b-109">Requirements</span></span>  
 <span data-ttu-id="eaf1b-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eaf1b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf1b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf1b-111">See also</span></span>

- [<span data-ttu-id="eaf1b-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaf1b-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
