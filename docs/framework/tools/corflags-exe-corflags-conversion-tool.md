---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a97ba44cfadc27582b2ae9119c01b392f14a19f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496501"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="bb1ea-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="bb1ea-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="bb1ea-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="bb1ea-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bb1ea-105">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bb1ea-106">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bb1ea-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="bb1ea-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="bb1ea-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1ea-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb1ea-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb1ea-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb1ea-109">Parameters</span></span>  
  
|<span data-ttu-id="bb1ea-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="bb1ea-110">Required parameter</span></span>|<span data-ttu-id="bb1ea-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1ea-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="bb1ea-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="bb1ea-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="bb1ea-113">Option</span></span>|<span data-ttu-id="bb1ea-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb1ea-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bb1ea-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="bb1ea-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="bb1ea-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="bb1ea-118">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="bb1ea-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-119">**/32BITPREF+**</span></span>|<span data-ttu-id="bb1ea-120">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="bb1ea-121">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="bb1ea-122">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="bb1ea-123">Bayrak bir DLL olarak ayarlanırsa, DLL 64-bit işlemde yüklenemiyordur ve <xref:System.BadImageFormatException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="bb1ea-124">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="bb1ea-125">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb1ea-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="bb1ea-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-126">**/32BITPREF-**</span></span>|<span data-ttu-id="bb1ea-127">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="bb1ea-128">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb1ea-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="bb1ea-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-129">**/?**</span></span>|<span data-ttu-id="bb1ea-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="bb1ea-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-131">**/Force**</span></span>|<span data-ttu-id="bb1ea-132">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="bb1ea-133">**Önemli:**  Tanımlayıcı bir adla adlandırılmış bir derlemeyi güncelleştirirseniz, kodunu yürütülmeden önce onu tekrar imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="bb1ea-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-134">**/help**</span></span>|<span data-ttu-id="bb1ea-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="bb1ea-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-136">**/ILONLY+**</span></span>|<span data-ttu-id="bb1ea-137">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="bb1ea-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-138">**/ILONLY-**</span></span>|<span data-ttu-id="bb1ea-139">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="bb1ea-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-140">**/nologo**</span></span>|<span data-ttu-id="bb1ea-141">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="bb1ea-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="bb1ea-143">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="bb1ea-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="bb1ea-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="bb1ea-145">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="bb1ea-146">**Not:**  Yerel olarak çalışması için derlemelerde CLR üstbilgi sürümü 2.5 veya daha üstü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb1ea-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb1ea-147">Remarks</span></span>  
 <span data-ttu-id="bb1ea-148">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1ea-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-149">See also</span></span>
- [<span data-ttu-id="bb1ea-150">Araçlar</span><span class="sxs-lookup"><span data-stu-id="bb1ea-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="bb1ea-151">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bb1ea-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)
- [<span data-ttu-id="bb1ea-152">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="bb1ea-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
