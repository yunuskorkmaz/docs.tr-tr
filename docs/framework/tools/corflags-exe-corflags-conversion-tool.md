---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
description: CorFlags dönüştürme aracı CorFlags.exe anlayın. Bu araç taşınabilir bir yürütülebilir görüntünün üst bilgisinin CorFlags bölümünü yapılandırmanızı sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: da5efadd63cc03f6f6e4eecf3115865ca3643b39
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167225"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="9b554-104">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="9b554-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="9b554-105">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="9b554-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="9b554-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9b554-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9b554-107">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9b554-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="9b554-108">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9b554-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="9b554-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="9b554-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b554-110">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9b554-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b554-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b554-111">Parameters</span></span>  
  
|<span data-ttu-id="9b554-112">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="9b554-112">Required parameter</span></span>|<span data-ttu-id="9b554-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b554-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="9b554-114">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="9b554-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="9b554-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="9b554-115">Option</span></span>|<span data-ttu-id="9b554-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b554-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="9b554-117">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9b554-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="9b554-118">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9b554-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="9b554-119">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9b554-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="9b554-120">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9b554-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="9b554-121">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9b554-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="9b554-122">Bayrak DLL üzerinde ayarlandıysa, DLL 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="9b554-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="9b554-123">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9b554-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="9b554-124">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="9b554-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="9b554-125">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9b554-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="9b554-126">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="9b554-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="9b554-127">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9b554-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="9b554-128">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b554-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="9b554-129">**Önemli:**  Tanımlayıcı adlı bir derlemeyi güncelleştirirseniz kodu yürütmeden önce yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b554-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="9b554-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9b554-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="9b554-131">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9b554-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="9b554-132">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9b554-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="9b554-133">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="9b554-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="9b554-134">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b554-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="9b554-135">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="9b554-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="9b554-136">**Note:**  Derlemeler yerel olarak çalıştırmak için 2,5 veya daha büyük bir CLR üstbilgi sürümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b554-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b554-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b554-137">Remarks</span></span>  
 <span data-ttu-id="9b554-138">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9b554-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b554-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b554-139">See also</span></span>

- [<span data-ttu-id="9b554-140">Araçlar</span><span class="sxs-lookup"><span data-stu-id="9b554-140">Tools</span></span>](index.md)
- [<span data-ttu-id="9b554-141">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="9b554-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="9b554-142">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="9b554-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
