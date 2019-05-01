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
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797492"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="1e477-102">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e477-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="1e477-103">Bir parametre, yerel bir değişken veya bir alan gibi bir değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e477-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e477-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1e477-104">Methods</span></span>  
  
|<span data-ttu-id="1e477-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1e477-105">Method</span></span>|<span data-ttu-id="1e477-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e477-107">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="1e477-108">Bu değişken için ilk adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="1e477-109">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e477-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1e477-110">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="1e477-111">Bu değişken için ikinci bir adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="1e477-112">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e477-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1e477-113">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="1e477-114">Üçüncü adres alanı, bu değişken için alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="1e477-115">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e477-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="1e477-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="1e477-117">Bu değişkenin adresi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="1e477-118">GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="1e477-119">Bu değişken için öznitelik bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="1e477-120">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="1e477-121">Bu değişkenin içinde üst bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="1e477-122">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="1e477-123">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="1e477-124">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="1e477-125">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="1e477-126">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e477-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="1e477-127">Bu değişkenin içinde üst başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="1e477-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e477-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e477-128">Requirements</span></span>  
 <span data-ttu-id="1e477-129">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1e477-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e477-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e477-130">See also</span></span>

- [<span data-ttu-id="1e477-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1e477-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
