---
title: ISymUnmanagedNamespace::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9017eeaf8e80c3dc0b546c1f3c2fb54634b3e949
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939522"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="e51a6-102">ISymUnmanagedNamespace::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e51a6-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="e51a6-103">Bu ad alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="e51a6-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e51a6-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e51a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e51a6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e51a6-106">[in] A `ULONG32` boyutunu gösteren `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="e51a6-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e51a6-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere ad alanı adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e51a6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="e51a6-108">[out] Ad alanı adını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e51a6-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e51a6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e51a6-109">Return Value</span></span>  
 <span data-ttu-id="e51a6-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e51a6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e51a6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e51a6-111">Requirements</span></span>  
 <span data-ttu-id="e51a6-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e51a6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51a6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e51a6-113">See also</span></span>

- [<span data-ttu-id="e51a6-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e51a6-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
