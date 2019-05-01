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
ms.openlocfilehash: c29656a4787c674886505a3be2508470460dfc10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939535"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="132bd-102">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="132bd-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="132bd-103">Sembol deposundaki bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="132bd-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="132bd-104">Bu arabirim türü ile ilgili öznitelikler yerine bir yöntemin yalnızca sembolü ile ilgili özniteliklere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="132bd-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="132bd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="132bd-105">Methods</span></span>  
  
|<span data-ttu-id="132bd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="132bd-106">Method</span></span>|<span data-ttu-id="132bd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="132bd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="132bd-108">GetNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="132bd-109">Bu yöntem içinde tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="132bd-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="132bd-111">Bir belge içindeki belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="132bd-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="132bd-112">GetParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="132bd-113">Bu yöntem için parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="132bd-114">GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="132bd-115">Belgede bir konuma konumu bu yöntem içinde kapsayan Microsoft Ara dilini (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş uzaklığında Çiftler dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="132bd-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="132bd-116">GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="132bd-117">Bu yöntem kök sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="132bd-118">Bu kapsam tüm yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="132bd-119">GetScopeFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="132bd-120">Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="132bd-121">GetSequencePointCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="132bd-122">Bu yöntem içinde dizi noktaları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="132bd-123">GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="132bd-124">Bu yöntem içinde tüm dizi noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="132bd-125">GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="132bd-126">Bu yöntemin kaynağı için başlangıç ve bitiş belge konumları alır.</span><span class="sxs-lookup"><span data-stu-id="132bd-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="132bd-127">GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="132bd-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="132bd-128">Bu yöntem için meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="132bd-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="132bd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="132bd-129">Requirements</span></span>  
 <span data-ttu-id="132bd-130">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="132bd-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132bd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="132bd-131">See also</span></span>

- [<span data-ttu-id="132bd-132">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="132bd-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
