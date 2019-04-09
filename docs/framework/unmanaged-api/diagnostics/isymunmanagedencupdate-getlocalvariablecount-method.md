---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a75ca89a3537ce8ee72e8ba24401800eacff20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153783"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="3f6f5-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f6f5-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="3f6f5-103">Yerel değişken sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f6f5-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f6f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f6f5-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="3f6f5-106">[in] Meta veri belirteci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="3f6f5-107">[out] Bir işaretçi bir `ULONG32` karakter yerel değişken sayısını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f6f5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f6f5-108">Return Value</span></span>  
 <span data-ttu-id="3f6f5-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f6f5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f6f5-110">Requirements</span></span>  
 <span data-ttu-id="3f6f5-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3f6f5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6f5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-112">See also</span></span>

- [<span data-ttu-id="3f6f5-113">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f6f5-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
