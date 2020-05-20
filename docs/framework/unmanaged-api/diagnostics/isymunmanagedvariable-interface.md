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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610177"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="6043e-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6043e-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="6043e-103">Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6043e-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6043e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6043e-104">Methods</span></span>  
  
|<span data-ttu-id="6043e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6043e-105">Method</span></span>|<span data-ttu-id="6043e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6043e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6043e-107">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="6043e-108">Bu değişken için ilk adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="6043e-109">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6043e-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="6043e-110">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="6043e-111">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="6043e-112">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6043e-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="6043e-113">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="6043e-114">Bu değişken için üçüncü adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="6043e-115">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6043e-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="6043e-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="6043e-117">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="6043e-118">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="6043e-119">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="6043e-120">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="6043e-121">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="6043e-122">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="6043e-123">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="6043e-124">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="6043e-125">Bu değişkenin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="6043e-126">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6043e-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="6043e-127">Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="6043e-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6043e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6043e-128">Requirements</span></span>  
 <span data-ttu-id="6043e-129">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6043e-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6043e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6043e-130">See also</span></span>

- [<span data-ttu-id="6043e-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6043e-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
