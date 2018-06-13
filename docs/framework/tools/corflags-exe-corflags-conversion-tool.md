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
ms.openlocfilehash: d4a5b6d490387f2da441ad95bdf369f700cf2e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400035"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="8e542-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="8e542-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="8e542-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="8e542-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="8e542-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8e542-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8e542-105">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e542-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8e542-106">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8e542-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8e542-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="8e542-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e542-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e542-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e542-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e542-109">Parameters</span></span>  
  
|<span data-ttu-id="8e542-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="8e542-110">Required parameter</span></span>|<span data-ttu-id="8e542-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e542-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="8e542-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="8e542-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="8e542-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="8e542-113">Option</span></span>|<span data-ttu-id="8e542-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e542-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8e542-115">**/ 32 BIT [REQ] +**</span><span class="sxs-lookup"><span data-stu-id="8e542-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="8e542-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8e542-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="8e542-117">**/ 32 BIT [REQ]-**</span><span class="sxs-lookup"><span data-stu-id="8e542-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="8e542-118">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e542-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="8e542-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="8e542-119">**/32BITPREF+**</span></span>|<span data-ttu-id="8e542-120">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8e542-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="8e542-121">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="8e542-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="8e542-122">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8e542-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="8e542-123">DLL üzerinde bayrağı ayarlarsanız, DLL 64-bit işlemde yüklenemiyordur ve <xref:System.BadImageFormatException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="8e542-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="8e542-124">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8e542-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="8e542-125">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e542-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="8e542-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="8e542-126">**/32BITPREF-**</span></span>|<span data-ttu-id="8e542-127">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e542-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="8e542-128">Yeni [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e542-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="8e542-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="8e542-129">**/?**</span></span>|<span data-ttu-id="8e542-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e542-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="8e542-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="8e542-131">**/Force**</span></span>|<span data-ttu-id="8e542-132">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e542-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="8e542-133">**Önemli:** tanımlayıcı adlı bir derleme güncelleştirirseniz, kodu yeniden çalıştırmadan önce imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e542-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="8e542-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="8e542-134">**/help**</span></span>|<span data-ttu-id="8e542-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e542-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="8e542-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="8e542-136">**/ILONLY+**</span></span>|<span data-ttu-id="8e542-137">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8e542-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="8e542-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="8e542-138">**/ILONLY-**</span></span>|<span data-ttu-id="8e542-139">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e542-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="8e542-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="8e542-140">**/nologo**</span></span>|<span data-ttu-id="8e542-141">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="8e542-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="8e542-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="8e542-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="8e542-143">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e542-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="8e542-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="8e542-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="8e542-145">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="8e542-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="8e542-146">**Not:** derlemeler CLR üstbilgi sürüm 2.5 veya yerel olarak çalıştırmak daha büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e542-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e542-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e542-147">Remarks</span></span>  
 <span data-ttu-id="8e542-148">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8e542-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e542-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e542-149">See Also</span></span>  
 [<span data-ttu-id="8e542-150">Araçlar</span><span class="sxs-lookup"><span data-stu-id="8e542-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="8e542-151">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="8e542-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="8e542-152">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="8e542-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
