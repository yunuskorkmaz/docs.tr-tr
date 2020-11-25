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
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717038"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="729dd-102">AssemblyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="729dd-102">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="729dd-103">Derleme seçeneklerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="729dd-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729dd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="729dd-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="729dd-105">Alanlar</span><span class="sxs-lookup"><span data-stu-id="729dd-105">Fields</span></span>  
  
|<span data-ttu-id="729dd-106">Alan</span><span class="sxs-lookup"><span data-stu-id="729dd-106">Field</span></span>|<span data-ttu-id="729dd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="729dd-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="729dd-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="729dd-108">optAssemTitle</span></span>|<span data-ttu-id="729dd-109">String-derleme başlığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="729dd-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="729dd-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="729dd-110">optAssemDescription</span></span>|<span data-ttu-id="729dd-111">Dize-derleme açıklamasını Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="729dd-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="729dd-112">optAssemConfig</span></span>|<span data-ttu-id="729dd-113">Dize-derleme yapılandırmasını Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="729dd-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="729dd-114">optAssemOS</span></span>|<span data-ttu-id="729dd-115">Dize kodlamalı as: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="729dd-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="729dd-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="729dd-116">optAssemProcessor</span></span>|<span data-ttu-id="729dd-117">'TUR</span><span class="sxs-lookup"><span data-stu-id="729dd-117">ULONG</span></span>|  
|<span data-ttu-id="729dd-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="729dd-118">optAssemLocale</span></span>|<span data-ttu-id="729dd-119">Dize-derleme yerel ayarını Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="729dd-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="729dd-120">optAssemVersion</span></span>|<span data-ttu-id="729dd-121">Dize kodlamalı as: "ana. Ikincil. derleme. düzeltme".</span><span class="sxs-lookup"><span data-stu-id="729dd-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="729dd-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="729dd-122">optAssemCompany</span></span>|<span data-ttu-id="729dd-123">Dize-şirketi Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="729dd-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="729dd-124">optAssemProduct</span></span>|<span data-ttu-id="729dd-125">Dize-ürün adını Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="729dd-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="729dd-126">optAssemProductVersion</span></span>|<span data-ttu-id="729dd-127">Dize (InformationalVersion olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="729dd-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="729dd-128">Optassemtelif hakkı</span><span class="sxs-lookup"><span data-stu-id="729dd-128">optAssemCopyright</span></span>|<span data-ttu-id="729dd-129">Dize-telif hakkı bilgilerini Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="729dd-130">Optassemmarka</span><span class="sxs-lookup"><span data-stu-id="729dd-130">optAssemTrademark</span></span>|<span data-ttu-id="729dd-131">Dize-ticari marka bilgilerini Içerir.</span><span class="sxs-lookup"><span data-stu-id="729dd-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="729dd-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="729dd-132">optAssemKeyFile</span></span>|<span data-ttu-id="729dd-133">Dize (dosya adı).</span><span class="sxs-lookup"><span data-stu-id="729dd-133">String (file name).</span></span>|  
|<span data-ttu-id="729dd-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="729dd-134">optAssemKeyName</span></span>|<span data-ttu-id="729dd-135">Dize (anahtar adı).</span><span class="sxs-lookup"><span data-stu-id="729dd-135">String (The key name).</span></span>|  
|<span data-ttu-id="729dd-136">Optassemalgıd</span><span class="sxs-lookup"><span data-stu-id="729dd-136">optAssemAlgID</span></span>|<span data-ttu-id="729dd-137">'TUR</span><span class="sxs-lookup"><span data-stu-id="729dd-137">ULONG</span></span>|  
|<span data-ttu-id="729dd-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="729dd-138">optAssemFlags</span></span>|<span data-ttu-id="729dd-139">'TUR</span><span class="sxs-lookup"><span data-stu-id="729dd-139">ULONG</span></span>|  
|<span data-ttu-id="729dd-140">Optassemyarı simgesi</span><span class="sxs-lookup"><span data-stu-id="729dd-140">optAssemHalfSign</span></span>|<span data-ttu-id="729dd-141">Bool (DelaySign olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="729dd-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="729dd-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="729dd-142">optAssemFileVersion</span></span>|<span data-ttu-id="729dd-143">Dize-kodlanmış "ana. Ikincil. derleme. düzeltme"--ProductVersion ile aynı.</span><span class="sxs-lookup"><span data-stu-id="729dd-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="729dd-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="729dd-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="729dd-145">"Ana. Ikincil. derleme. düzeltme" olarak dize kodlamalı.</span><span class="sxs-lookup"><span data-stu-id="729dd-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="729dd-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="729dd-146">optLastAssemOption</span></span>|<span data-ttu-id="729dd-147">Öğe sayısı sayacı.</span><span class="sxs-lookup"><span data-stu-id="729dd-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="729dd-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="729dd-148">Requirements</span></span>  

 <span data-ttu-id="729dd-149">**Üstbilgi:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="729dd-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="729dd-150">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="729dd-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729dd-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="729dd-151">See also</span></span>

- [<span data-ttu-id="729dd-152">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="729dd-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
