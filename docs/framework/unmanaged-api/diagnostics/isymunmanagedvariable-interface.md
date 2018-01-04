---
title: ISymUnmanagedVariable Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable
helpviewer_keywords: ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5ae8d1d05274363dc523c1a2cebf4ed09c1f461
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="b2ce3-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="b2ce3-103">Bir parametre, yerel bir değişken ya da bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2ce3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2ce3-104">Methods</span></span>  
  
|<span data-ttu-id="b2ce3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b2ce3-105">Method</span></span>|<span data-ttu-id="b2ce3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2ce3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2ce3-107">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="b2ce3-108">İlk adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="b2ce3-109">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2ce3-110">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="b2ce3-111">İkinci adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="b2ce3-112">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2ce3-113">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="b2ce3-114">Üçüncü adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="b2ce3-115">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="b2ce3-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="b2ce3-117">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="b2ce3-118">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="b2ce3-119">Öznitelik bayrakları için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="b2ce3-120">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="b2ce3-121">Bu değişken, üst içinde son uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="b2ce3-122">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="b2ce3-123">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="b2ce3-124">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="b2ce3-125">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="b2ce3-126">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ce3-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="b2ce3-127">Bu değişken, üst içinde başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2ce3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2ce3-128">Requirements</span></span>  
 <span data-ttu-id="b2ce3-129">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b2ce3-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ce3-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ce3-130">See Also</span></span>  
 [<span data-ttu-id="b2ce3-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2ce3-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
