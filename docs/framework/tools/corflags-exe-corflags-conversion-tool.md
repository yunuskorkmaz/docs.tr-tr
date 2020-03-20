---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129856"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="c0cf3-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="c0cf3-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="c0cf3-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="c0cf3-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c0cf3-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c0cf3-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c0cf3-106">Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c0cf3-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="c0cf3-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cf3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0cf3-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0cf3-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0cf3-109">Parameters</span></span>  
  
|<span data-ttu-id="c0cf3-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="c0cf3-110">Required parameter</span></span>|<span data-ttu-id="c0cf3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0cf3-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="c0cf3-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="c0cf3-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="c0cf3-113">Option</span></span>|<span data-ttu-id="c0cf3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0cf3-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="c0cf3-115">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="c0cf3-116">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="c0cf3-117">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="c0cf3-118">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="c0cf3-119">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="c0cf3-120">Bayrak bir DLL üzerinde ayarlanmışsa, DLL 64 bit işlemlerinde <xref:System.BadImageFormatException> yüklenmez ve bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="c0cf3-121">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="c0cf3-122">.NET Framework 4.5'te yeni.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="c0cf3-123">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="c0cf3-124">.NET Framework 4.5'te yeni.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="c0cf3-125">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="c0cf3-126">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="c0cf3-127">**Önemli:**  Güçlü adlandırılmış bir derlemeyi güncellerseniz, kodunu yürütmeden önce yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="c0cf3-128">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="c0cf3-129">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="c0cf3-130">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="c0cf3-131">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="c0cf3-132">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="c0cf3-133">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="c0cf3-134">**Not:**  Derlemelerin yerel olarak çalıştırılabilmek için 2,5 veya daha büyük bir CLR üstbilgi sürümü ne olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0cf3-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0cf3-135">Remarks</span></span>  
 <span data-ttu-id="c0cf3-136">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cf3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0cf3-137">See also</span></span>

- [<span data-ttu-id="c0cf3-138">Araçlar</span><span class="sxs-lookup"><span data-stu-id="c0cf3-138">Tools</span></span>](index.md)
- [<span data-ttu-id="c0cf3-139">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="c0cf3-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="c0cf3-140">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="c0cf3-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
