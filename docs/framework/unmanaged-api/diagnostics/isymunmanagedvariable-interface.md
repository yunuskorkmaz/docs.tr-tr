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
ms.openlocfilehash: c32d5b66c575a21b4d390cff560b71f93aa31927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="5b4d2-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="5b4d2-103">Bir parametre, yerel bir değişken ya da bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b4d2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5b4d2-104">Methods</span></span>  
  
|<span data-ttu-id="5b4d2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5b4d2-105">Method</span></span>|<span data-ttu-id="5b4d2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b4d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b4d2-107">GetAddressField1 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="5b4d2-108">İlk adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="5b4d2-109">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="5b4d2-110">GetAddressField2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="5b4d2-111">İkinci adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="5b4d2-112">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="5b4d2-113">GetAddressField3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="5b4d2-114">Üçüncü adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="5b4d2-115">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="5b4d2-116">GetAddressKind yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="5b4d2-117">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="5b4d2-118">GetAttributes yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="5b4d2-119">Öznitelik bayrakları için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="5b4d2-120">GetEndOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="5b4d2-121">Bu değişken, üst içinde son uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="5b4d2-122">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="5b4d2-123">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="5b4d2-124">GetSignature yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="5b4d2-125">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="5b4d2-126">GetStartOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b4d2-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="5b4d2-127">Bu değişken, üst içinde başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b4d2-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b4d2-128">Requirements</span></span>  
 <span data-ttu-id="5b4d2-129">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b4d2-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4d2-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b4d2-130">See Also</span></span>  
 [<span data-ttu-id="5b4d2-131">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b4d2-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
