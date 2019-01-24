---
title: ISymUnmanagedMethod Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b19e5ce88ea34188b2757d2a0c313341fbf1e7e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604268"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="3ce6c-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="3ce6c-103">Sembol deposundaki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="3ce6c-104">Bu arabirim türü ile ilgili öznitelikler yerine bir yöntemin yalnızca sembolü ile ilgili özniteliklere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ce6c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3ce6c-105">Methods</span></span>  
  
|<span data-ttu-id="3ce6c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3ce6c-106">Method</span></span>|<span data-ttu-id="3ce6c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ce6c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ce6c-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="3ce6c-109">Bu yöntem içinde tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="3ce6c-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="3ce6c-111">Bir belge içindeki belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="3ce6c-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="3ce6c-113">Bu yöntem için parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="3ce6c-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="3ce6c-115">Belgede bir konuma konumu bu yöntem içinde kapsayan Microsoft Ara dilini (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş uzaklığında Çiftler dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="3ce6c-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="3ce6c-117">Bu yöntem kök sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="3ce6c-118">Bu kapsam tüm yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="3ce6c-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="3ce6c-120">Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="3ce6c-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="3ce6c-122">Bu yöntem içinde dizi noktaları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="3ce6c-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="3ce6c-124">Bu yöntem içinde tüm dizi noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="3ce6c-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="3ce6c-126">Bu yöntemin kaynağı için başlangıç ve bitiş belge konumları alır.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="3ce6c-127">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce6c-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="3ce6c-128">Bu yöntem için meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ce6c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ce6c-129">Requirements</span></span>  
 <span data-ttu-id="3ce6c-130">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3ce6c-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce6c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce6c-131">See also</span></span>
- [<span data-ttu-id="3ce6c-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3ce6c-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
