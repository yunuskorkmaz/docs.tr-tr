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
ms.openlocfilehash: 4323423d3958fa1ca652c55f8f75749bb6e1ee79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759390"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="5929c-102">ISymUnmanagedNamespace::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5929c-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="5929c-103">Bu ad alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="5929c-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5929c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5929c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5929c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5929c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5929c-106">[in] A `ULONG32` boyutunu gösteren `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="5929c-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5929c-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere ad alanı adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5929c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="5929c-108">[out] Ad alanı adını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5929c-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5929c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5929c-109">Return Value</span></span>  
 <span data-ttu-id="5929c-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5929c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5929c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5929c-111">Requirements</span></span>  
 <span data-ttu-id="5929c-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5929c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5929c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5929c-113">See also</span></span>

- [<span data-ttu-id="5929c-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5929c-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
