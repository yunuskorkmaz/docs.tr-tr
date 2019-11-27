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
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="0ae1e-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="0ae1e-103">Sembol deposu içindeki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="0ae1e-104">Bu arabirim, türle ilgili öznitelikler yerine yalnızca bir yöntemin sembolüyle ilgili özniteliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ae1e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0ae1e-105">Methods</span></span>  
  
|<span data-ttu-id="0ae1e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0ae1e-106">Method</span></span>|<span data-ttu-id="0ae1e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ae1e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ae1e-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="0ae1e-109">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="0ae1e-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="0ae1e-111">Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="0ae1e-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="0ae1e-113">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="0ae1e-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="0ae1e-115">Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="0ae1e-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="0ae1e-117">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="0ae1e-118">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="0ae1e-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="0ae1e-120">Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="0ae1e-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="0ae1e-122">Bu yöntemin içindeki sıra noktalarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="0ae1e-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="0ae1e-124">Bu yöntemin içindeki tüm sıra noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="0ae1e-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="0ae1e-126">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="0ae1e-127">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae1e-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="0ae1e-128">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ae1e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ae1e-129">Requirements</span></span>  
 <span data-ttu-id="0ae1e-130">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0ae1e-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae1e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ae1e-131">See also</span></span>

- [<span data-ttu-id="0ae1e-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ae1e-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
