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
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448790"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="28609-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28609-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="28609-103">Represents a method within the symbol store.</span><span class="sxs-lookup"><span data-stu-id="28609-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="28609-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span><span class="sxs-lookup"><span data-stu-id="28609-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28609-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28609-105">Methods</span></span>  
  
|<span data-ttu-id="28609-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="28609-106">Method</span></span>|<span data-ttu-id="28609-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28609-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28609-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="28609-109">Gets the namespace within which this method is defined.</span><span class="sxs-lookup"><span data-stu-id="28609-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="28609-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="28609-111">Returns the offset within this method that corresponds to a given position within a document.</span><span class="sxs-lookup"><span data-stu-id="28609-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="28609-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="28609-113">Gets the parameters for this method.</span><span class="sxs-lookup"><span data-stu-id="28609-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="28609-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="28609-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span><span class="sxs-lookup"><span data-stu-id="28609-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="28609-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="28609-117">Gets the root lexical scope within this method.</span><span class="sxs-lookup"><span data-stu-id="28609-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="28609-118">This scope encloses the entire method.</span><span class="sxs-lookup"><span data-stu-id="28609-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="28609-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="28609-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span><span class="sxs-lookup"><span data-stu-id="28609-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="28609-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="28609-122">Gets the count of sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="28609-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="28609-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="28609-124">Gets all the sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="28609-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="28609-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="28609-126">Gets the start and end document positions for the source of this method.</span><span class="sxs-lookup"><span data-stu-id="28609-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="28609-127">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28609-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="28609-128">Returns the metadata token for this method.</span><span class="sxs-lookup"><span data-stu-id="28609-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28609-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28609-129">Requirements</span></span>  
 <span data-ttu-id="28609-130">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28609-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28609-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28609-131">See also</span></span>

- [<span data-ttu-id="28609-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28609-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
