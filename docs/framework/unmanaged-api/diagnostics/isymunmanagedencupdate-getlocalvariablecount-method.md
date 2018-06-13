---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu
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
ms.openlocfilehash: d7d557e2111a26c0865c20d8eb952c4d42b5604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436065"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="c9e32-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu</span><span class="sxs-lookup"><span data-stu-id="c9e32-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="c9e32-103">Yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c9e32-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9e32-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9e32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9e32-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="c9e32-106">[in] Yöntemleri meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c9e32-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="c9e32-107">[out] Bir işaretçi bir `ULONG32` karakter yerel değişkenler sayı içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c9e32-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9e32-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9e32-108">Return Value</span></span>  
 <span data-ttu-id="c9e32-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c9e32-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e32-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9e32-110">Requirements</span></span>  
 <span data-ttu-id="c9e32-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9e32-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e32-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e32-112">See Also</span></span>  
 [<span data-ttu-id="c9e32-113">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9e32-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
