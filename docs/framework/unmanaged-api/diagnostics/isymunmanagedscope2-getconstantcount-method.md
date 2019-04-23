---
title: ISymUnmanagedScope2::GetConstantCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a063d25e180be466421c14ca65a5b4cea881fc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127334"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="37217-102">ISymUnmanagedScope2::GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37217-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="37217-103">Bu kapsam içinde tanımlı sabitlerden sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="37217-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37217-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37217-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37217-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37217-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="37217-106">[out] Bir işaretçi bir `ULONG32` karakter sabitleri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="37217-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37217-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37217-107">Return Value</span></span>  
 <span data-ttu-id="37217-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="37217-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37217-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37217-109">Requirements</span></span>  
 <span data-ttu-id="37217-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="37217-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37217-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37217-111">See also</span></span>

- [<span data-ttu-id="37217-112">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37217-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
