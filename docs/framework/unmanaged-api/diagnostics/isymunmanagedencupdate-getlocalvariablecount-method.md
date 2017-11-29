---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f0a47012a2e6e1f6fec1a363c3b514e45bee396
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="c3ec7-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Metodu</span><span class="sxs-lookup"><span data-stu-id="c3ec7-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="c3ec7-103">Yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c3ec7-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ec7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3ec7-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3ec7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3ec7-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="c3ec7-106">[in] Yöntemleri meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="c3ec7-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="c3ec7-107">[out] Bir işaretçi bir `ULONG32` karakter yerel değişkenler sayı içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c3ec7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3ec7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3ec7-108">Return Value</span></span>  
 <span data-ttu-id="c3ec7-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c3ec7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ec7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ec7-110">Requirements</span></span>  
 <span data-ttu-id="c3ec7-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c3ec7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ec7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ec7-112">See Also</span></span>  
 [<span data-ttu-id="c3ec7-113">Isymunmanagedencupdate arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ec7-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
