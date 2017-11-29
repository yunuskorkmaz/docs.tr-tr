---
title: "CorFlags.exe (CorFlags Dönüştürme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca3e9dbe5578623ccc67898c6f08213c31ad8e23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="12486-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="12486-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="12486-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="12486-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="12486-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="12486-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="12486-105">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="12486-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="12486-106">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="12486-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="12486-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="12486-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12486-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12486-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12486-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12486-109">Parameters</span></span>  
  
|<span data-ttu-id="12486-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="12486-110">Required parameter</span></span>|<span data-ttu-id="12486-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12486-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="12486-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="12486-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="12486-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="12486-113">Option</span></span>|<span data-ttu-id="12486-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12486-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="12486-115">**/ 32 BIT [REQ] +**</span><span class="sxs-lookup"><span data-stu-id="12486-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="12486-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12486-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="12486-117">**/ 32 BIT [REQ]-**</span><span class="sxs-lookup"><span data-stu-id="12486-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="12486-118">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="12486-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="12486-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="12486-119">**/32BITPREF+**</span></span>|<span data-ttu-id="12486-120">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12486-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="12486-121">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="12486-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="12486-122">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="12486-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="12486-123">DLL üzerinde bayrağı ayarlarsanız, DLL 64-bit işlemde yüklenemiyordur ve <xref:System.BadImageFormatException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="12486-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="12486-124">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="12486-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="12486-125">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12486-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="12486-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="12486-126">**/32BITPREF-**</span></span>|<span data-ttu-id="12486-127">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="12486-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="12486-128">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12486-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="12486-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="12486-129">**/?**</span></span>|<span data-ttu-id="12486-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12486-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="12486-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="12486-131">**/Force**</span></span>|<span data-ttu-id="12486-132">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="12486-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="12486-133">**Önemli:** tanımlayıcı adlı bir derleme güncelleştirirseniz, kodu yeniden çalıştırmadan önce imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="12486-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="12486-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="12486-134">**/help**</span></span>|<span data-ttu-id="12486-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12486-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="12486-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="12486-136">**/ILONLY+**</span></span>|<span data-ttu-id="12486-137">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12486-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="12486-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="12486-138">**/ILONLY-**</span></span>|<span data-ttu-id="12486-139">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="12486-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="12486-140">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="12486-140">**/nologo**</span></span>|<span data-ttu-id="12486-141">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="12486-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="12486-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="12486-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="12486-143">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="12486-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="12486-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="12486-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="12486-145">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="12486-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="12486-146">**Not:** derlemeler CLR üstbilgi sürüm 2.5 veya yerel olarak çalıştırmak daha büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12486-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12486-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12486-147">Remarks</span></span>  
 <span data-ttu-id="12486-148">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12486-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12486-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12486-149">See Also</span></span>  
 [<span data-ttu-id="12486-150">Araçları</span><span class="sxs-lookup"><span data-stu-id="12486-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="12486-151">64-bit uygulamalar</span><span class="sxs-lookup"><span data-stu-id="12486-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="12486-152">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="12486-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
