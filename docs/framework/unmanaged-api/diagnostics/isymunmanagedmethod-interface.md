---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod arabirimi'
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
ms.openlocfilehash: 18f87784a959ddc62415592e51d1971ea10f90bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709964"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="299e6-103">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="299e6-103">ISymUnmanagedMethod Interface</span></span>

<span data-ttu-id="299e6-104">Sembol deposu içindeki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="299e6-104">Represents a method within the symbol store.</span></span> <span data-ttu-id="299e6-105">Bu arabirim, türle ilgili öznitelikler yerine yalnızca bir yöntemin sembolüyle ilgili özniteliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="299e6-105">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="299e6-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="299e6-106">Methods</span></span>  
  
|<span data-ttu-id="299e6-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="299e6-107">Method</span></span>|<span data-ttu-id="299e6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="299e6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="299e6-109">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-109">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="299e6-110">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-110">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="299e6-111">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-111">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="299e6-112">Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="299e6-112">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="299e6-113">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-113">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="299e6-114">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-114">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="299e6-115">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-115">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="299e6-116">Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="299e6-116">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="299e6-117">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-117">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="299e6-118">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-118">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="299e6-119">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="299e6-119">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="299e6-120">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-120">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="299e6-121">Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-121">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="299e6-122">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-122">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="299e6-123">Bu yöntemin içindeki sıra noktalarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-123">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="299e6-124">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-124">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="299e6-125">Bu yöntemin içindeki tüm sıra noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-125">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="299e6-126">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="299e6-126">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="299e6-127">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="299e6-127">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="299e6-128">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="299e6-128">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="299e6-129">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="299e6-129">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="299e6-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="299e6-130">Requirements</span></span>  

 <span data-ttu-id="299e6-131">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="299e6-131">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="299e6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="299e6-132">See also</span></span>

- [<span data-ttu-id="299e6-133">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="299e6-133">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
