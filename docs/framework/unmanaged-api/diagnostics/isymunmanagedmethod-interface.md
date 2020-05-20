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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615130"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="864ff-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="864ff-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="864ff-103">Sembol deposu içindeki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="864ff-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="864ff-104">Bu arabirim, türle ilgili öznitelikler yerine yalnızca bir yöntemin sembolüyle ilgili özniteliklerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="864ff-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="864ff-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="864ff-105">Methods</span></span>  
  
|<span data-ttu-id="864ff-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="864ff-106">Method</span></span>|<span data-ttu-id="864ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="864ff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="864ff-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="864ff-109">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="864ff-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="864ff-111">Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="864ff-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="864ff-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="864ff-113">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="864ff-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="864ff-115">Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="864ff-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="864ff-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="864ff-117">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="864ff-118">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="864ff-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="864ff-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="864ff-120">Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="864ff-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="864ff-122">Bu yöntemin içindeki sıra noktalarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="864ff-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="864ff-124">Bu yöntemin içindeki tüm sıra noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="864ff-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="864ff-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="864ff-126">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="864ff-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="864ff-127">GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="864ff-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="864ff-128">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="864ff-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="864ff-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="864ff-129">Requirements</span></span>  
 <span data-ttu-id="864ff-130">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="864ff-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864ff-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="864ff-131">See also</span></span>

- [<span data-ttu-id="864ff-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="864ff-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
