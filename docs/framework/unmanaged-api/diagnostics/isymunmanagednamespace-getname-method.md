---
title: ISymUnmanagedNamespace::GetName Metodu
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
ms.openlocfilehash: 5478a8d3433a8a57dab458c98ea745f32a9ffdf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721973"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="66a52-102">ISymUnmanagedNamespace::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="66a52-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="66a52-103">Bu ad alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="66a52-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66a52-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66a52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66a52-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="66a52-106">[in] A `ULONG32` boyutunu gösteren `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="66a52-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="66a52-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere ad alanı adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="66a52-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="66a52-108">[out] Ad alanı adını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66a52-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66a52-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66a52-109">Return Value</span></span>  
 <span data-ttu-id="66a52-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="66a52-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a52-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66a52-111">Requirements</span></span>  
 <span data-ttu-id="66a52-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66a52-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a52-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66a52-113">See also</span></span>
- [<span data-ttu-id="66a52-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66a52-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
