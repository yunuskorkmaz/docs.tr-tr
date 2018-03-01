---
title: ISymUnmanagedMethod Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6305625c3d02dbd126a284287e19b319e21eeba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="ab0e3-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="ab0e3-103">Sembol deposu içinde yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="ab0e3-104">Bu arabirim türü ile ilgili öznitelikleri yerine bir yöntemin yalnızca simgesi ilgili öznitelikleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab0e3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ab0e3-105">Methods</span></span>  
  
|<span data-ttu-id="ab0e3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab0e3-106">Method</span></span>|<span data-ttu-id="ab0e3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab0e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab0e3-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="ab0e3-109">Bu yöntem tanımlandığı ad alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="ab0e3-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="ab0e3-111">Bir belge içinde belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="ab0e3-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="ab0e3-113">Bu yöntem için parametre alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="ab0e3-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="ab0e3-115">Bir konumda bir belge, bu yöntem içinde konumu kapsayan Microsoft Ara dili (MSIL) aralıklarına karşılık gelir başlangıç ve bitiş uzaklığında çiftleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="ab0e3-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="ab0e3-117">Bu yöntem için kök sözcük kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="ab0e3-118">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="ab0e3-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="ab0e3-120">Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözcük kapsamında alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="ab0e3-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="ab0e3-122">Bu yöntem içinde sıralama noktaları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="ab0e3-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="ab0e3-124">Bu yöntem içindeki tüm sıralama noktaları alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="ab0e3-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="ab0e3-126">Bu yöntem kaynak için başlangıç ve bitiş belge konumlarına alır.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="ab0e3-127">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab0e3-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="ab0e3-128">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab0e3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab0e3-129">Requirements</span></span>  
 <span data-ttu-id="ab0e3-130">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab0e3-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0e3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab0e3-131">See Also</span></span>  
 [<span data-ttu-id="ab0e3-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab0e3-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
