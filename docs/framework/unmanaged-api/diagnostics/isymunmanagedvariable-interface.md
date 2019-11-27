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
ms.openlocfilehash: ee57ba14f048032e2cd9d0129089743c0f0304bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445979"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="cd386-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd386-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="cd386-103">Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd386-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd386-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd386-104">Methods</span></span>  
  
|<span data-ttu-id="cd386-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cd386-105">Method</span></span>|<span data-ttu-id="cd386-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd386-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd386-107">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="cd386-108">Bu değişken için ilk adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="cd386-109">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd386-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="cd386-110">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="cd386-111">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="cd386-112">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd386-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="cd386-113">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="cd386-114">Bu değişken için üçüncü adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="cd386-115">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cd386-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="cd386-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="cd386-117">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="cd386-118">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="cd386-119">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="cd386-120">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="cd386-121">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="cd386-122">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="cd386-123">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="cd386-124">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="cd386-125">Bu değişkenin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="cd386-126">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd386-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="cd386-127">Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="cd386-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd386-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd386-128">Requirements</span></span>  
 <span data-ttu-id="cd386-129">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cd386-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd386-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd386-130">See also</span></span>

- [<span data-ttu-id="cd386-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd386-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
