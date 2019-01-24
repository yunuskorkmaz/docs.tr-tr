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
ms.openlocfilehash: 939e815f4d3adc5f6e1c8b8fc85c9f4b89372501
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571489"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="9f151-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9f151-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="9f151-103">Derleme seçeneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="9f151-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f151-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f151-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="9f151-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="9f151-105">Fields</span></span>  
  
|<span data-ttu-id="9f151-106">Alan</span><span class="sxs-lookup"><span data-stu-id="9f151-106">Field</span></span>|<span data-ttu-id="9f151-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f151-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f151-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="9f151-108">optAssemTitle</span></span>|<span data-ttu-id="9f151-109">Dize - derleme başlığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f151-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="9f151-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="9f151-110">optAssemDescription</span></span>|<span data-ttu-id="9f151-111">Dize - derleme tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="9f151-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="9f151-112">optAssemConfig</span></span>|<span data-ttu-id="9f151-113">Dize - derleme yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="9f151-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="9f151-114">optAssemOS</span></span>|<span data-ttu-id="9f151-115">Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="9f151-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="9f151-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="9f151-116">optAssemProcessor</span></span>|<span data-ttu-id="9f151-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="9f151-117">ULONG</span></span>|  
|<span data-ttu-id="9f151-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="9f151-118">optAssemLocale</span></span>|<span data-ttu-id="9f151-119">Dize - derleme yerel ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="9f151-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="9f151-120">optAssemVersion</span></span>|<span data-ttu-id="9f151-121">Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="9f151-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="9f151-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="9f151-122">optAssemCompany</span></span>|<span data-ttu-id="9f151-123">Dize - şirket içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="9f151-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="9f151-124">optAssemProduct</span></span>|<span data-ttu-id="9f151-125">Dize - ürün adını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="9f151-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="9f151-126">optAssemProductVersion</span></span>|<span data-ttu-id="9f151-127">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="9f151-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="9f151-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="9f151-128">optAssemCopyright</span></span>|<span data-ttu-id="9f151-129">Dize - telif hakkı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="9f151-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="9f151-130">optAssemTrademark</span></span>|<span data-ttu-id="9f151-131">Dize - ticari marka bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f151-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="9f151-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="9f151-132">optAssemKeyFile</span></span>|<span data-ttu-id="9f151-133">String (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="9f151-133">String (file name).</span></span>|  
|<span data-ttu-id="9f151-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="9f151-134">optAssemKeyName</span></span>|<span data-ttu-id="9f151-135">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="9f151-135">String (The key name).</span></span>|  
|<span data-ttu-id="9f151-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="9f151-136">optAssemAlgID</span></span>|<span data-ttu-id="9f151-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="9f151-137">ULONG</span></span>|  
|<span data-ttu-id="9f151-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="9f151-138">optAssemFlags</span></span>|<span data-ttu-id="9f151-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="9f151-139">ULONG</span></span>|  
|<span data-ttu-id="9f151-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="9f151-140">optAssemHalfSign</span></span>|<span data-ttu-id="9f151-141">Bool (DelaySign da bilinir).</span><span class="sxs-lookup"><span data-stu-id="9f151-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="9f151-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="9f151-142">optAssemFileVersion</span></span>|<span data-ttu-id="9f151-143">Dize - "Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="9f151-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="9f151-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="9f151-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="9f151-145">Dize - "Major.Minor.Build.Revision" olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="9f151-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="9f151-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="9f151-146">optLastAssemOption</span></span>|<span data-ttu-id="9f151-147">Bir sayacı öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="9f151-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f151-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f151-148">Requirements</span></span>  
 <span data-ttu-id="9f151-149">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="9f151-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="9f151-150">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="9f151-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f151-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f151-151">See also</span></span>
- [<span data-ttu-id="9f151-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="9f151-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
