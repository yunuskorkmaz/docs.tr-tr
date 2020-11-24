---
title: Sabitler (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
ms.openlocfilehash: 19defe9c6c19bc04eb3c9ddaee386ef1ee409de5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673936"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="a6400-102">Sabitler (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6400-102">Constants (Unmanaged API Reference)</span></span>

<span data-ttu-id="a6400-103">Bu konuda, CorSym. IDL içinde tanımlanan dil türü, dil satıcısı ve belge türü sabitleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6400-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="a6400-104">Dil türü sabitleri</span><span class="sxs-lookup"><span data-stu-id="a6400-104">Language Type Constants</span></span>  

 <span data-ttu-id="a6400-105">Aşağıdaki tabloda, programlama dillerini tanımlayan GUID 'Leri temsil eden dil türü sabitleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6400-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="a6400-106">Sembol</span><span class="sxs-lookup"><span data-stu-id="a6400-106">Symbol</span></span>|<span data-ttu-id="a6400-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6400-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6400-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="a6400-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="a6400-109">C dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="a6400-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="a6400-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="a6400-111">C++ dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="a6400-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="a6400-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="a6400-113">C# dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="a6400-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="a6400-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="a6400-115">Temel dili gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="a6400-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="a6400-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="a6400-117">Java dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="a6400-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="a6400-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="a6400-119">COBOL dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="a6400-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="a6400-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="a6400-121">Pascal dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="a6400-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="a6400-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="a6400-123">Microsoft ara dili (MSIL) derleme kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="a6400-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="a6400-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="a6400-125">JScript dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="a6400-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="a6400-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="a6400-127">SMC dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="a6400-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="a6400-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="a6400-129">.NET Framework için etkinleştirilmiş C++ dilini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="a6400-130">Dil satıcısı sabitleri</span><span class="sxs-lookup"><span data-stu-id="a6400-130">Language Vendor Constants</span></span>  

 <span data-ttu-id="a6400-131">Aşağıdaki tabloda, programlama dili satıcılarını tanımlayan GUID 'Leri temsil eden dil satıcısı sabitleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6400-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="a6400-132">Sembol</span><span class="sxs-lookup"><span data-stu-id="a6400-132">Symbol</span></span>|<span data-ttu-id="a6400-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6400-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6400-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="a6400-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="a6400-135">Microsoft 'ı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="a6400-136">Belge türü sabitleri</span><span class="sxs-lookup"><span data-stu-id="a6400-136">Document Type Constants</span></span>  

 <span data-ttu-id="a6400-137">Aşağıdaki tabloda, belge türlerini tanımlayan GUID 'Leri temsil eden belge türü sabitleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6400-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="a6400-138">Sembol</span><span class="sxs-lookup"><span data-stu-id="a6400-138">Symbol</span></span>|<span data-ttu-id="a6400-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6400-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6400-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="a6400-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="a6400-141">Bir metin belgesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="a6400-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="a6400-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="a6400-143">Metin olmayan bir belgeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6400-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6400-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6400-144">See also</span></span>

- [<span data-ttu-id="a6400-145">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6400-145">Unmanaged API Reference</span></span>](index.md)
