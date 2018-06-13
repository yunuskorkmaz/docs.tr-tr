---
title: AssemblyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3926a0d49b2db02cf52a3cc943b05edc4cc36a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406293"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="14dbd-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="14dbd-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="14dbd-103">Derleme seçenekleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="14dbd-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14dbd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14dbd-104">Syntax</span></span>  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="14dbd-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="14dbd-105">Fields</span></span>  
  
|<span data-ttu-id="14dbd-106">Alan</span><span class="sxs-lookup"><span data-stu-id="14dbd-106">Field</span></span>|<span data-ttu-id="14dbd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14dbd-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14dbd-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="14dbd-108">optAssemTitle</span></span>|<span data-ttu-id="14dbd-109">Dize - derleme başlığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14dbd-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="14dbd-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="14dbd-110">optAssemDescription</span></span>|<span data-ttu-id="14dbd-111">Dize - derleme açıklaması içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="14dbd-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="14dbd-112">optAssemConfig</span></span>|<span data-ttu-id="14dbd-113">Dize - derleme yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="14dbd-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="14dbd-114">optAssemOS</span></span>|<span data-ttu-id="14dbd-115">Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="14dbd-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="14dbd-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="14dbd-116">optAssemProcessor</span></span>|<span data-ttu-id="14dbd-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="14dbd-117">ULONG</span></span>|  
|<span data-ttu-id="14dbd-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="14dbd-118">optAssemLocale</span></span>|<span data-ttu-id="14dbd-119">Dize - derleme yerel içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="14dbd-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="14dbd-120">optAssemVersion</span></span>|<span data-ttu-id="14dbd-121">Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="14dbd-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="14dbd-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="14dbd-122">optAssemCompany</span></span>|<span data-ttu-id="14dbd-123">Dize - şirket içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="14dbd-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="14dbd-124">optAssemProduct</span></span>|<span data-ttu-id="14dbd-125">Dize - ürün adı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="14dbd-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="14dbd-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="14dbd-126">optAssemProductVersion</span></span>|<span data-ttu-id="14dbd-127">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="14dbd-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="14dbd-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="14dbd-128">optAssemCopyright</span></span>|<span data-ttu-id="14dbd-129">Dize - telif hakkı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="14dbd-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="14dbd-130">optAssemTrademark</span></span>|<span data-ttu-id="14dbd-131">Dize - ticari marka bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="14dbd-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="14dbd-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="14dbd-132">optAssemKeyFile</span></span>|<span data-ttu-id="14dbd-133">String (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="14dbd-133">String (file name).</span></span>|  
|<span data-ttu-id="14dbd-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="14dbd-134">optAssemKeyName</span></span>|<span data-ttu-id="14dbd-135">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="14dbd-135">String (The key name).</span></span>|  
|<span data-ttu-id="14dbd-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="14dbd-136">optAssemAlgID</span></span>|<span data-ttu-id="14dbd-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="14dbd-137">ULONG</span></span>|  
|<span data-ttu-id="14dbd-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="14dbd-138">optAssemFlags</span></span>|<span data-ttu-id="14dbd-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="14dbd-139">ULONG</span></span>|  
|<span data-ttu-id="14dbd-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="14dbd-140">optAssemHalfSign</span></span>|<span data-ttu-id="14dbd-141">Bool (DelaySign da bilinir).</span><span class="sxs-lookup"><span data-stu-id="14dbd-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="14dbd-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="14dbd-142">optAssemFileVersion</span></span>|<span data-ttu-id="14dbd-143">"Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış bir dize -.</span><span class="sxs-lookup"><span data-stu-id="14dbd-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="14dbd-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="14dbd-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="14dbd-145">"Major.Minor.Build.Revision" kodlanmış bir dize -.</span><span class="sxs-lookup"><span data-stu-id="14dbd-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="14dbd-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="14dbd-146">optLastAssemOption</span></span>|<span data-ttu-id="14dbd-147">Bir sayaç öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="14dbd-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14dbd-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14dbd-148">Requirements</span></span>  
 <span data-ttu-id="14dbd-149">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="14dbd-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="14dbd-150">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="14dbd-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14dbd-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14dbd-151">See Also</span></span>  
 [<span data-ttu-id="14dbd-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="14dbd-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
