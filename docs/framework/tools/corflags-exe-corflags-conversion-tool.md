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
ms.openlocfilehash: 7ee801a5af214e2306e6f1667b5e4ee067683fdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093117"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="bfd29-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="bfd29-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="bfd29-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="bfd29-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="bfd29-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="bfd29-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bfd29-105">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="bfd29-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bfd29-106">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bfd29-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="bfd29-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="bfd29-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd29-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfd29-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfd29-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfd29-109">Parameters</span></span>  
  
|<span data-ttu-id="bfd29-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="bfd29-110">Required parameter</span></span>|<span data-ttu-id="bfd29-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd29-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="bfd29-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="bfd29-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="bfd29-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="bfd29-113">Option</span></span>|<span data-ttu-id="bfd29-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfd29-114">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="bfd29-115">/32BIT[REQ]+</span><span class="sxs-lookup"><span data-stu-id="bfd29-115">/32BIT[REQ]+</span></span>**|<span data-ttu-id="bfd29-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bfd29-116">Sets the 32BITREQUIRED flag.</span></span>|  
|**<span data-ttu-id="bfd29-117">/32BIT[REQ]-</span><span class="sxs-lookup"><span data-stu-id="bfd29-117">/32BIT[REQ]-</span></span>**|<span data-ttu-id="bfd29-118">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-118">Clears the 32BITREQUIRED flag.</span></span>|  
|**<span data-ttu-id="bfd29-119">/32BITPREF+</span><span class="sxs-lookup"><span data-stu-id="bfd29-119">/32BITPREF+</span></span>**|<span data-ttu-id="bfd29-120">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bfd29-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="bfd29-121">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="bfd29-122">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfd29-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="bfd29-123">Bayrak bir DLL olarak ayarlanırsa, DLL 64-bit işlemde yüklenemiyordur ve <xref:System.BadImageFormatException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bfd29-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="bfd29-124">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bfd29-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="bfd29-125">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfd29-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|**<span data-ttu-id="bfd29-126">/32BITPREF-</span><span class="sxs-lookup"><span data-stu-id="bfd29-126">/32BITPREF-</span></span>**|<span data-ttu-id="bfd29-127">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="bfd29-128">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfd29-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|**<span data-ttu-id="bfd29-129">/?</span><span class="sxs-lookup"><span data-stu-id="bfd29-129">/?</span></span>**|<span data-ttu-id="bfd29-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bfd29-130">Displays command syntax and options for the tool.</span></span>|  
|**<span data-ttu-id="bfd29-131">/ Force</span><span class="sxs-lookup"><span data-stu-id="bfd29-131">/Force</span></span>**|<span data-ttu-id="bfd29-132">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfd29-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="bfd29-133">**Önemli:**  Tanımlayıcı bir adla adlandırılmış bir derlemeyi güncelleştirirseniz, kodunu yürütülmeden önce onu tekrar imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfd29-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|**<span data-ttu-id="bfd29-134">/help</span><span class="sxs-lookup"><span data-stu-id="bfd29-134">/help</span></span>**|<span data-ttu-id="bfd29-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bfd29-135">Displays command syntax and options for the tool.</span></span>|  
|**<span data-ttu-id="bfd29-136">/ILONLY+</span><span class="sxs-lookup"><span data-stu-id="bfd29-136">/ILONLY+</span></span>**|<span data-ttu-id="bfd29-137">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bfd29-137">Sets the ILONLY flag.</span></span>|  
|**<span data-ttu-id="bfd29-138">/ILONLY-</span><span class="sxs-lookup"><span data-stu-id="bfd29-138">/ILONLY-</span></span>**|<span data-ttu-id="bfd29-139">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-139">Clears the ILONLY flag.</span></span>|  
|**<span data-ttu-id="bfd29-140">/nologo</span><span class="sxs-lookup"><span data-stu-id="bfd29-140">/nologo</span></span>**|<span data-ttu-id="bfd29-141">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-141">Suppresses the Microsoft startup banner display.</span></span>|  
|**<span data-ttu-id="bfd29-142">/ RevertCLRHeader</span><span class="sxs-lookup"><span data-stu-id="bfd29-142">/RevertCLRHeader</span></span>**|<span data-ttu-id="bfd29-143">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="bfd29-143">Reverts the CLR header version to 2.0.</span></span>|  
|**<span data-ttu-id="bfd29-144">/ UpgradeCLRHeader</span><span class="sxs-lookup"><span data-stu-id="bfd29-144">/UpgradeCLRHeader</span></span>**|<span data-ttu-id="bfd29-145">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bfd29-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="bfd29-146">**Not:**  Yerel olarak çalışması için derlemelerde CLR üstbilgi sürümü 2.5 veya daha üstü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfd29-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd29-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfd29-147">Remarks</span></span>  
 <span data-ttu-id="bfd29-148">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bfd29-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd29-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfd29-149">See also</span></span>

- [<span data-ttu-id="bfd29-150">Araçlar</span><span class="sxs-lookup"><span data-stu-id="bfd29-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="bfd29-151">64 bitlik Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bfd29-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)
- [<span data-ttu-id="bfd29-152">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="bfd29-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
