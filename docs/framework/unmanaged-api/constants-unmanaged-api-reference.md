---
title: "Sabitler (Yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e086e856bb7a872b14815825f78d208ff5296899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="609e7-102">Sabitler (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="609e7-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="609e7-103">Bu konu, dil türü, dil satıcı ve CorSym.idl içinde tanımlanan belge türü sabitleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="609e7-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="609e7-104">Dil türü sabitleri</span><span class="sxs-lookup"><span data-stu-id="609e7-104">Language Type Constants</span></span>  
 <span data-ttu-id="609e7-105">Aşağıdaki tabloda dil programlama dillerini belirleyin GUID'ler temsil türü sabitleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="609e7-106">Simgesi</span><span class="sxs-lookup"><span data-stu-id="609e7-106">Symbol</span></span>|<span data-ttu-id="609e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609e7-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="609e7-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="609e7-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="609e7-109">C dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="609e7-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="609e7-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="609e7-111">C++ dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="609e7-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="609e7-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="609e7-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="609e7-113">C# dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="609e7-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="609e7-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="609e7-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="609e7-115">Temel dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="609e7-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="609e7-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="609e7-117">Java dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="609e7-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="609e7-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="609e7-119">COBOL dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="609e7-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="609e7-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="609e7-121">Pascal dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="609e7-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="609e7-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="609e7-123">Microsoft Ara dili (MSIL) bütünleştirilmiş kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="609e7-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="609e7-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="609e7-125">JScript dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="609e7-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="609e7-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="609e7-127">SMC dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="609e7-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="609e7-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="609e7-129">.NET Framework için etkin C++ dili belirtir.</span><span class="sxs-lookup"><span data-stu-id="609e7-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="609e7-130">Dil satıcı sabitleri</span><span class="sxs-lookup"><span data-stu-id="609e7-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="609e7-131">Aşağıdaki tabloda dil programlama dili satıcıları tanımlamak GUID'ler temsil eden satıcı sabitleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="609e7-132">Simgesi</span><span class="sxs-lookup"><span data-stu-id="609e7-132">Symbol</span></span>|<span data-ttu-id="609e7-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609e7-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="609e7-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="609e7-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="609e7-135">Microsoft gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="609e7-136">Belge türü sabitleri</span><span class="sxs-lookup"><span data-stu-id="609e7-136">Document Type Constants</span></span>  
 <span data-ttu-id="609e7-137">Aşağıdaki tabloda belge belge türlerini tanımlamak GUID'ler temsil türü sabitleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="609e7-138">Simgesi</span><span class="sxs-lookup"><span data-stu-id="609e7-138">Symbol</span></span>|<span data-ttu-id="609e7-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609e7-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="609e7-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="609e7-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="609e7-141">Bir metin belgesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="609e7-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="609e7-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="609e7-143">Bir metin dışı belge gösterir.</span><span class="sxs-lookup"><span data-stu-id="609e7-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="609e7-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="609e7-144">See Also</span></span>  
 [<span data-ttu-id="609e7-145">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="609e7-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
