---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b165501b3e090cf309f3b4053649644b87b47f22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555576"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="e31c6-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e31c6-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="e31c6-103">Zaman uyumsuz grubu tanımlamanız geçerli yöntemi işlemleri bekler.</span><span class="sxs-lookup"><span data-stu-id="e31c6-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="e31c6-104">Her yield uzaklığı olası yield tanımlayan bir await'ın dönüş yönergesi, eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e31c6-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="e31c6-105">Her `breakpointMethod` / `breakpointOffset` çifti söyler bize nerede zaman uyumsuz işlemi, (Bu, farklı bir yöntem olabilir. devam edecek</span><span class="sxs-lookup"><span data-stu-id="e31c6-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31c6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e31c6-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e31c6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e31c6-107">Parameters</span></span>  
  
|<span data-ttu-id="e31c6-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="e31c6-108">Parameter</span></span>|<span data-ttu-id="e31c6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31c6-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e31c6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e31c6-110">Return Value</span></span>  
 <span data-ttu-id="e31c6-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e31c6-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31c6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e31c6-112">Requirements</span></span>  
 <span data-ttu-id="e31c6-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e31c6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31c6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e31c6-114">See also</span></span>
- [<span data-ttu-id="e31c6-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e31c6-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
