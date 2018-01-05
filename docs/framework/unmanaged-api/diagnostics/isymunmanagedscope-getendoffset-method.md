---
title: ISymUnmanagedScope::GetEndOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64990dc2785a3804e683e281c823f459ec48e8a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="a0870-102">ISymUnmanagedScope::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="a0870-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="a0870-103">Bitiş uzaklığı için bu kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="a0870-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0870-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0870-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0870-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0870-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a0870-106">[out] Bir işaretçi bir `ULONG32` bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="a0870-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0870-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a0870-107">Return Value</span></span>  
 <span data-ttu-id="a0870-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a0870-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0870-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0870-109">Requirements</span></span>  
 <span data-ttu-id="a0870-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0870-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0870-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0870-111">See Also</span></span>  
 [<span data-ttu-id="a0870-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0870-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="a0870-113">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0870-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
