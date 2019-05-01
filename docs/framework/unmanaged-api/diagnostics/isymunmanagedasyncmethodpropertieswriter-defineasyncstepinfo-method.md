---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8305d0a562fd90e3fae32e372b663ca3942d2a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940146"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="3c802-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c802-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="3c802-103">Zaman uyumsuz grubu tanımlamanız geçerli yöntemi işlemleri bekler.</span><span class="sxs-lookup"><span data-stu-id="3c802-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="3c802-104">Her yield uzaklığı olası yield tanımlayan bir await'ın dönüş yönergesi, eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3c802-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="3c802-105">Her `breakpointMethod` / `breakpointOffset` çifti söyler bize zaman uyumsuz işlem, farklı bir yöntem olabilir. burada devam edecek.</span><span class="sxs-lookup"><span data-stu-id="3c802-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c802-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c802-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c802-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c802-107">Parameters</span></span>  
  
|<span data-ttu-id="3c802-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="3c802-108">Parameter</span></span>|<span data-ttu-id="3c802-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c802-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="3c802-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c802-110">Return Value</span></span>  
 <span data-ttu-id="3c802-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="3c802-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c802-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c802-112">Requirements</span></span>  
 <span data-ttu-id="3c802-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3c802-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c802-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c802-114">See also</span></span>

- [<span data-ttu-id="3c802-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c802-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
