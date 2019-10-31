---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129191"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="99763-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99763-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="99763-103">Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="99763-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="99763-104">Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99763-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="99763-105">Her bir `breakpointMethod`/`breakpointOffset` çifti, zaman uyumsuz işlemin sürdürülecek farklı bir yöntemde olabilecek olduğunu bize söyler.</span><span class="sxs-lookup"><span data-stu-id="99763-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99763-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99763-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99763-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99763-107">Parameters</span></span>  
  
|<span data-ttu-id="99763-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="99763-108">Parameter</span></span>|<span data-ttu-id="99763-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99763-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="99763-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99763-110">Return Value</span></span>  
 <span data-ttu-id="99763-111">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="99763-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99763-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99763-112">Requirements</span></span>  
 <span data-ttu-id="99763-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="99763-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99763-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99763-114">See also</span></span>

- [<span data-ttu-id="99763-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99763-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
