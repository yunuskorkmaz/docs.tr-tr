---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethodpropertieswriter::D Efineasyncstepınfo yöntemi'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f95436b10041ae5bfd56ca080a9b8ce70748022c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790249"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="dc5c9-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc5c9-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="dc5c9-104">Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dc5c9-104">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="dc5c9-105">Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc5c9-105">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="dc5c9-106">Her bir `breakpointMethod` / `breakpointOffset` çiftin, zaman uyumsuz işlemin sürdürülecek, farklı bir yöntemde olabilecek bir durum olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="dc5c9-106">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5c9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc5c9-107">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc5c9-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc5c9-108">Parameters</span></span>  
  
|<span data-ttu-id="dc5c9-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="dc5c9-109">Parameter</span></span>|<span data-ttu-id="dc5c9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc5c9-110">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="dc5c9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dc5c9-111">Return Value</span></span>  

 <span data-ttu-id="dc5c9-112">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc5c9-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc5c9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc5c9-113">Requirements</span></span>  

 <span data-ttu-id="dc5c9-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dc5c9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5c9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5c9-115">See also</span></span>

- [<span data-ttu-id="dc5c9-116">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5c9-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
