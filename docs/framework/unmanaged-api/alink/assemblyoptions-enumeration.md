---
description: 'Daha fazla bilgi edinin: AssemblyOptions sabit listesi'
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
ms.openlocfilehash: aba9ecb3176f533e2d53e2e45fef3d1dc4e55077
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638424"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="82e93-103">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="82e93-103">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="82e93-104">Derleme seçeneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="82e93-104">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e93-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82e93-105">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="82e93-106">Alanlar</span><span class="sxs-lookup"><span data-stu-id="82e93-106">Fields</span></span>  
  
|<span data-ttu-id="82e93-107">Alan</span><span class="sxs-lookup"><span data-stu-id="82e93-107">Field</span></span>|<span data-ttu-id="82e93-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82e93-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="82e93-109">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="82e93-109">optAssemTitle</span></span>|<span data-ttu-id="82e93-110">String-derleme başlığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="82e93-110">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="82e93-111">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="82e93-111">optAssemDescription</span></span>|<span data-ttu-id="82e93-112">Dize-derleme açıklamasını Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-112">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="82e93-113">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="82e93-113">optAssemConfig</span></span>|<span data-ttu-id="82e93-114">Dize-derleme yapılandırmasını Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-114">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="82e93-115">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="82e93-115">optAssemOS</span></span>|<span data-ttu-id="82e93-116">Dize kodlamalı as: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="82e93-116">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="82e93-117">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="82e93-117">optAssemProcessor</span></span>|<span data-ttu-id="82e93-118">'TUR</span><span class="sxs-lookup"><span data-stu-id="82e93-118">ULONG</span></span>|  
|<span data-ttu-id="82e93-119">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="82e93-119">optAssemLocale</span></span>|<span data-ttu-id="82e93-120">Dize-derleme yerel ayarını Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-120">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="82e93-121">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="82e93-121">optAssemVersion</span></span>|<span data-ttu-id="82e93-122">Dize kodlamalı as: "ana. Ikincil. derleme. düzeltme".</span><span class="sxs-lookup"><span data-stu-id="82e93-122">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="82e93-123">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="82e93-123">optAssemCompany</span></span>|<span data-ttu-id="82e93-124">Dize-şirketi Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-124">String - Contains the company.</span></span>|  
|<span data-ttu-id="82e93-125">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="82e93-125">optAssemProduct</span></span>|<span data-ttu-id="82e93-126">Dize-ürün adını Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-126">String - Contains the product name.</span></span>|  
|<span data-ttu-id="82e93-127">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="82e93-127">optAssemProductVersion</span></span>|<span data-ttu-id="82e93-128">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="82e93-128">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="82e93-129">Optassemtelif hakkı</span><span class="sxs-lookup"><span data-stu-id="82e93-129">optAssemCopyright</span></span>|<span data-ttu-id="82e93-130">Dize-telif hakkı bilgilerini Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-130">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="82e93-131">Optassemmarka</span><span class="sxs-lookup"><span data-stu-id="82e93-131">optAssemTrademark</span></span>|<span data-ttu-id="82e93-132">Dize-ticari marka bilgilerini Içerir.</span><span class="sxs-lookup"><span data-stu-id="82e93-132">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="82e93-133">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="82e93-133">optAssemKeyFile</span></span>|<span data-ttu-id="82e93-134">Dize (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="82e93-134">String (file name).</span></span>|  
|<span data-ttu-id="82e93-135">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="82e93-135">optAssemKeyName</span></span>|<span data-ttu-id="82e93-136">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="82e93-136">String (The key name).</span></span>|  
|<span data-ttu-id="82e93-137">Optassemalgıd</span><span class="sxs-lookup"><span data-stu-id="82e93-137">optAssemAlgID</span></span>|<span data-ttu-id="82e93-138">'TUR</span><span class="sxs-lookup"><span data-stu-id="82e93-138">ULONG</span></span>|  
|<span data-ttu-id="82e93-139">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="82e93-139">optAssemFlags</span></span>|<span data-ttu-id="82e93-140">'TUR</span><span class="sxs-lookup"><span data-stu-id="82e93-140">ULONG</span></span>|  
|<span data-ttu-id="82e93-141">Optassemyarı simgesi</span><span class="sxs-lookup"><span data-stu-id="82e93-141">optAssemHalfSign</span></span>|<span data-ttu-id="82e93-142">Bool (DelaySign olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="82e93-142">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="82e93-143">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="82e93-143">optAssemFileVersion</span></span>|<span data-ttu-id="82e93-144">Dize-kodlanmış "ana. Ikincil. derleme. düzeltme"--ProductVersion ile aynı.</span><span class="sxs-lookup"><span data-stu-id="82e93-144">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="82e93-145">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="82e93-145">optAssemSatelliteVer</span></span>|<span data-ttu-id="82e93-146">"Ana. Ikincil. derleme. düzeltme" olarak dize kodlamalı.</span><span class="sxs-lookup"><span data-stu-id="82e93-146">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="82e93-147">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="82e93-147">optLastAssemOption</span></span>|<span data-ttu-id="82e93-148">Öğe sayısı sayacı.</span><span class="sxs-lookup"><span data-stu-id="82e93-148">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82e93-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82e93-149">Requirements</span></span>  

 <span data-ttu-id="82e93-150">**Üstbilgi:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="82e93-150">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="82e93-151">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="82e93-151">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e93-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e93-152">See also</span></span>

- [<span data-ttu-id="82e93-153">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="82e93-153">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
