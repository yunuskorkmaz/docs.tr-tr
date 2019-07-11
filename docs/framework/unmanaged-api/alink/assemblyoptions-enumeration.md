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
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742271"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="875c6-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="875c6-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="875c6-103">Derleme seçeneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="875c6-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="875c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="875c6-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="875c6-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="875c6-105">Fields</span></span>  
  
|<span data-ttu-id="875c6-106">Alan</span><span class="sxs-lookup"><span data-stu-id="875c6-106">Field</span></span>|<span data-ttu-id="875c6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="875c6-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="875c6-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="875c6-108">optAssemTitle</span></span>|<span data-ttu-id="875c6-109">Dize - derleme başlığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="875c6-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="875c6-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="875c6-110">optAssemDescription</span></span>|<span data-ttu-id="875c6-111">Dize - derleme tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="875c6-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="875c6-112">optAssemConfig</span></span>|<span data-ttu-id="875c6-113">Dize - derleme yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="875c6-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="875c6-114">optAssemOS</span></span>|<span data-ttu-id="875c6-115">Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="875c6-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="875c6-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="875c6-116">optAssemProcessor</span></span>|<span data-ttu-id="875c6-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="875c6-117">ULONG</span></span>|  
|<span data-ttu-id="875c6-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="875c6-118">optAssemLocale</span></span>|<span data-ttu-id="875c6-119">Dize - derleme yerel ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="875c6-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="875c6-120">optAssemVersion</span></span>|<span data-ttu-id="875c6-121">Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="875c6-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="875c6-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="875c6-122">optAssemCompany</span></span>|<span data-ttu-id="875c6-123">Dize - şirket içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="875c6-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="875c6-124">optAssemProduct</span></span>|<span data-ttu-id="875c6-125">Dize - ürün adını içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="875c6-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="875c6-126">optAssemProductVersion</span></span>|<span data-ttu-id="875c6-127">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="875c6-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="875c6-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="875c6-128">optAssemCopyright</span></span>|<span data-ttu-id="875c6-129">Dize - telif hakkı bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="875c6-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="875c6-130">optAssemTrademark</span></span>|<span data-ttu-id="875c6-131">Dize - ticari marka bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="875c6-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="875c6-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="875c6-132">optAssemKeyFile</span></span>|<span data-ttu-id="875c6-133">String (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="875c6-133">String (file name).</span></span>|  
|<span data-ttu-id="875c6-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="875c6-134">optAssemKeyName</span></span>|<span data-ttu-id="875c6-135">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="875c6-135">String (The key name).</span></span>|  
|<span data-ttu-id="875c6-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="875c6-136">optAssemAlgID</span></span>|<span data-ttu-id="875c6-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="875c6-137">ULONG</span></span>|  
|<span data-ttu-id="875c6-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="875c6-138">optAssemFlags</span></span>|<span data-ttu-id="875c6-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="875c6-139">ULONG</span></span>|  
|<span data-ttu-id="875c6-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="875c6-140">optAssemHalfSign</span></span>|<span data-ttu-id="875c6-141">Bool (DelaySign da bilinir).</span><span class="sxs-lookup"><span data-stu-id="875c6-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="875c6-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="875c6-142">optAssemFileVersion</span></span>|<span data-ttu-id="875c6-143">Dize - "Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="875c6-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="875c6-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="875c6-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="875c6-145">Dize - "Major.Minor.Build.Revision" olarak kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="875c6-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="875c6-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="875c6-146">optLastAssemOption</span></span>|<span data-ttu-id="875c6-147">Bir sayacı öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="875c6-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="875c6-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="875c6-148">Requirements</span></span>  
 <span data-ttu-id="875c6-149">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="875c6-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="875c6-150">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="875c6-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875c6-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="875c6-151">See also</span></span>

- [<span data-ttu-id="875c6-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="875c6-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
