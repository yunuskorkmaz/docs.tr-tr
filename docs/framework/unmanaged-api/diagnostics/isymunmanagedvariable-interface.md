---
description: 'Şu konuda daha fazla bilgi edinin: ıstreamunmanagedvariable arabirimi'
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
ms.openlocfilehash: 15b6c7018f92ad4c82abb9e5b4e52bf428b3f54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762701"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="c4ed4-103">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-103">ISymUnmanagedVariable Interface</span></span>

<span data-ttu-id="c4ed4-104">Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-104">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4ed4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c4ed4-105">Methods</span></span>  
  
|<span data-ttu-id="c4ed4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c4ed4-106">Method</span></span>|<span data-ttu-id="c4ed4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4ed4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4ed4-108">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-108">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="c4ed4-109">Bu değişken için ilk adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-109">Gets the first address field for this variable.</span></span> <span data-ttu-id="c4ed4-110">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-110">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c4ed4-111">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-111">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="c4ed4-112">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-112">Gets the second address field for this variable.</span></span> <span data-ttu-id="c4ed4-113">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-113">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c4ed4-114">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-114">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="c4ed4-115">Bu değişken için üçüncü adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-115">Gets the third address field for this variable.</span></span> <span data-ttu-id="c4ed4-116">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-116">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c4ed4-117">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="c4ed4-118">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-118">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="c4ed4-119">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-119">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="c4ed4-120">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-120">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="c4ed4-121">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-121">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="c4ed4-122">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-122">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="c4ed4-123">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-123">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="c4ed4-124">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-124">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="c4ed4-125">GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="c4ed4-125">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="c4ed4-126">Bu değişkenin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-126">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="c4ed4-127">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ed4-127">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="c4ed4-128">Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-128">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4ed4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4ed4-129">Requirements</span></span>  

 <span data-ttu-id="c4ed4-130">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c4ed4-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ed4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4ed4-131">See also</span></span>

- [<span data-ttu-id="c4ed4-132">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c4ed4-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
