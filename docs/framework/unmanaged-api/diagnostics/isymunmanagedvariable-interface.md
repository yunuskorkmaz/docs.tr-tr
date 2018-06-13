---
title: ISymUnmanagedVariable Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3db4fc691637c049e0374416cb92a2056555ad11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428706"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="16184-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16184-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="16184-103">Bir parametre, yerel bir değişken ya da bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="16184-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16184-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16184-104">Methods</span></span>  
  
|<span data-ttu-id="16184-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="16184-105">Method</span></span>|<span data-ttu-id="16184-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16184-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16184-107">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="16184-108">İlk adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="16184-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="16184-109">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16184-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16184-110">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="16184-111">İkinci adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="16184-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="16184-112">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16184-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16184-113">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="16184-114">Üçüncü adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="16184-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="16184-115">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16184-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16184-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="16184-117">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="16184-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="16184-118">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="16184-119">Öznitelik bayrakları için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="16184-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="16184-120">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="16184-121">Bu değişken, üst içinde son uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="16184-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="16184-122">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="16184-123">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="16184-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="16184-124">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="16184-125">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="16184-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="16184-126">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16184-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="16184-127">Bu değişken, üst içinde başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="16184-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16184-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16184-128">Requirements</span></span>  
 <span data-ttu-id="16184-129">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16184-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16184-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16184-130">See Also</span></span>  
 [<span data-ttu-id="16184-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16184-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
