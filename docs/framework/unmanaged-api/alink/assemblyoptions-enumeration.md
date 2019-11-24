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
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446593"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="782ea-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="782ea-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="782ea-103">Enumerates the assembly options.</span><span class="sxs-lookup"><span data-stu-id="782ea-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="782ea-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="fields"></a><span data-ttu-id="782ea-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="782ea-105">Fields</span></span>  
  
|<span data-ttu-id="782ea-106">Alan</span><span class="sxs-lookup"><span data-stu-id="782ea-106">Field</span></span>|<span data-ttu-id="782ea-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="782ea-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="782ea-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="782ea-108">optAssemTitle</span></span>|<span data-ttu-id="782ea-109">String - Represents the assembly title.</span><span class="sxs-lookup"><span data-stu-id="782ea-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="782ea-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="782ea-110">optAssemDescription</span></span>|<span data-ttu-id="782ea-111">String - Contains the assembly description.</span><span class="sxs-lookup"><span data-stu-id="782ea-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="782ea-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="782ea-112">optAssemConfig</span></span>|<span data-ttu-id="782ea-113">String - Contains the assembly configuration.</span><span class="sxs-lookup"><span data-stu-id="782ea-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="782ea-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="782ea-114">optAssemOS</span></span>|<span data-ttu-id="782ea-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="782ea-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="782ea-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="782ea-116">optAssemProcessor</span></span>|<span data-ttu-id="782ea-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="782ea-117">ULONG</span></span>|  
|<span data-ttu-id="782ea-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="782ea-118">optAssemLocale</span></span>|<span data-ttu-id="782ea-119">String - Contains the assembly locale.</span><span class="sxs-lookup"><span data-stu-id="782ea-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="782ea-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="782ea-120">optAssemVersion</span></span>|<span data-ttu-id="782ea-121">String - Encoded as: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="782ea-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="782ea-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="782ea-122">optAssemCompany</span></span>|<span data-ttu-id="782ea-123">String - Contains the company.</span><span class="sxs-lookup"><span data-stu-id="782ea-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="782ea-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="782ea-124">optAssemProduct</span></span>|<span data-ttu-id="782ea-125">String - Contains the product name.</span><span class="sxs-lookup"><span data-stu-id="782ea-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="782ea-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="782ea-126">optAssemProductVersion</span></span>|<span data-ttu-id="782ea-127">String (also known as InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="782ea-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="782ea-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="782ea-128">optAssemCopyright</span></span>|<span data-ttu-id="782ea-129">String - Contains the copyright information.</span><span class="sxs-lookup"><span data-stu-id="782ea-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="782ea-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="782ea-130">optAssemTrademark</span></span>|<span data-ttu-id="782ea-131">String - Contains the trademark information.</span><span class="sxs-lookup"><span data-stu-id="782ea-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="782ea-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="782ea-132">optAssemKeyFile</span></span>|<span data-ttu-id="782ea-133">String (file name).</span><span class="sxs-lookup"><span data-stu-id="782ea-133">String (file name).</span></span>|  
|<span data-ttu-id="782ea-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="782ea-134">optAssemKeyName</span></span>|<span data-ttu-id="782ea-135">String (The key name).</span><span class="sxs-lookup"><span data-stu-id="782ea-135">String (The key name).</span></span>|  
|<span data-ttu-id="782ea-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="782ea-136">optAssemAlgID</span></span>|<span data-ttu-id="782ea-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="782ea-137">ULONG</span></span>|  
|<span data-ttu-id="782ea-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="782ea-138">optAssemFlags</span></span>|<span data-ttu-id="782ea-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="782ea-139">ULONG</span></span>|  
|<span data-ttu-id="782ea-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="782ea-140">optAssemHalfSign</span></span>|<span data-ttu-id="782ea-141">Bool (Also known as DelaySign).</span><span class="sxs-lookup"><span data-stu-id="782ea-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="782ea-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="782ea-142">optAssemFileVersion</span></span>|<span data-ttu-id="782ea-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="782ea-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="782ea-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="782ea-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="782ea-145">String - Encoded as "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="782ea-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="782ea-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="782ea-146">optLastAssemOption</span></span>|<span data-ttu-id="782ea-147">A counter of the number of elements.</span><span class="sxs-lookup"><span data-stu-id="782ea-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="782ea-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="782ea-148">Requirements</span></span>  
 <span data-ttu-id="782ea-149">**Header:** alink.h</span><span class="sxs-lookup"><span data-stu-id="782ea-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="782ea-150">**Library**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="782ea-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782ea-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="782ea-151">See also</span></span>

- [<span data-ttu-id="782ea-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="782ea-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
