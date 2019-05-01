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
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790110"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="dd13d-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dd13d-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="dd13d-103">Derleme seçeneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="dd13d-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd13d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd13d-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="dd13d-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="dd13d-105">Fields</span></span>  
  
|<span data-ttu-id="dd13d-106">Alan</span><span class="sxs-lookup"><span data-stu-id="dd13d-106">Field</span></span>|<span data-ttu-id="dd13d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd13d-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd13d-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="dd13d-108">optAssemTitle</span></span>|<span data-ttu-id="dd13d-109">Dize - derleme başlığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dd13d-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="dd13d-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="dd13d-110">optAssemDescription</span></span>|<span data-ttu-id="dd13d-111">Dize - derleme tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="dd13d-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="dd13d-112">optAssemConfig</span></span>|<span data-ttu-id="dd13d-113">Dize - derleme yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="dd13d-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="dd13d-114">optAssemOS</span></span>|<span data-ttu-id="dd13d-115">Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="dd13d-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="dd13d-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="dd13d-116">optAssemProcessor</span></span>|<span data-ttu-id="dd13d-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="dd13d-117">ULONG</span></span>|  
|<span data-ttu-id="dd13d-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="dd13d-118">optAssemLocale</span></span>|<span data-ttu-id="dd13d-119">Dize - derleme yerel ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="dd13d-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="dd13d-120">optAssemVersion</span></span>|<span data-ttu-id="dd13d-121">Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="dd13d-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="dd13d-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="dd13d-122">optAssemCompany</span></span>|<span data-ttu-id="dd13d-123">Dize - şirket içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="dd13d-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="dd13d-124">optAssemProduct</span></span>|<span data-ttu-id="dd13d-125">Dize - ürün adını içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="dd13d-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="dd13d-126">optAssemProductVersion</span></span>|<span data-ttu-id="dd13d-127">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="dd13d-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="dd13d-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="dd13d-128">optAssemCopyright</span></span>|<span data-ttu-id="dd13d-129">Dize - telif hakkı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="dd13d-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="dd13d-130">optAssemTrademark</span></span>|<span data-ttu-id="dd13d-131">Dize - ticari marka bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="dd13d-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="dd13d-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="dd13d-132">optAssemKeyFile</span></span>|<span data-ttu-id="dd13d-133">String (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="dd13d-133">String (file name).</span></span>|  
|<span data-ttu-id="dd13d-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="dd13d-134">optAssemKeyName</span></span>|<span data-ttu-id="dd13d-135">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="dd13d-135">String (The key name).</span></span>|  
|<span data-ttu-id="dd13d-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="dd13d-136">optAssemAlgID</span></span>|<span data-ttu-id="dd13d-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="dd13d-137">ULONG</span></span>|  
|<span data-ttu-id="dd13d-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="dd13d-138">optAssemFlags</span></span>|<span data-ttu-id="dd13d-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="dd13d-139">ULONG</span></span>|  
|<span data-ttu-id="dd13d-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="dd13d-140">optAssemHalfSign</span></span>|<span data-ttu-id="dd13d-141">Bool (DelaySign da bilinir).</span><span class="sxs-lookup"><span data-stu-id="dd13d-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="dd13d-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="dd13d-142">optAssemFileVersion</span></span>|<span data-ttu-id="dd13d-143">Dize - "Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="dd13d-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="dd13d-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="dd13d-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="dd13d-145">Dize - "Major.Minor.Build.Revision" olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="dd13d-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="dd13d-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="dd13d-146">optLastAssemOption</span></span>|<span data-ttu-id="dd13d-147">Bir sayacı öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="dd13d-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd13d-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd13d-148">Requirements</span></span>  
 <span data-ttu-id="dd13d-149">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="dd13d-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="dd13d-150">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="dd13d-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd13d-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd13d-151">See also</span></span>

- [<span data-ttu-id="dd13d-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="dd13d-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
