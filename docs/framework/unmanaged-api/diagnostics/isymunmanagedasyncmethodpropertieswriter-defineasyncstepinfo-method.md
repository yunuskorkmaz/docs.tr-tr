---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f8c77e44183fd92704aa91ca1cfd7e3fa68aa27f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719625"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="91336-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91336-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="91336-103">Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="91336-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="91336-104">Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91336-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="91336-105">Her bir `breakpointMethod` / `breakpointOffset` çiftin, zaman uyumsuz işlemin sürdürülecek, farklı bir yöntemde olabilecek bir durum olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="91336-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91336-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="91336-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91336-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91336-107">Parameters</span></span>  
  
|<span data-ttu-id="91336-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="91336-108">Parameter</span></span>|<span data-ttu-id="91336-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91336-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="91336-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91336-110">Return Value</span></span>  

 <span data-ttu-id="91336-111">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="91336-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91336-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91336-112">Requirements</span></span>  

 <span data-ttu-id="91336-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="91336-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91336-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91336-114">See also</span></span>

- [<span data-ttu-id="91336-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91336-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
