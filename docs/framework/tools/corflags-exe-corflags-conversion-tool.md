---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129856"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="13413-102">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="13413-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="13413-103">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="13413-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="13413-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="13413-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="13413-105">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="13413-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="13413-106">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="13413-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="13413-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="13413-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13413-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13413-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="13413-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13413-109">Parameters</span></span>  
  
|<span data-ttu-id="13413-110">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="13413-110">Required parameter</span></span>|<span data-ttu-id="13413-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13413-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="13413-112">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="13413-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="13413-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="13413-113">Option</span></span>|<span data-ttu-id="13413-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13413-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="13413-115">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13413-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="13413-116">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13413-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="13413-117">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13413-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="13413-118">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="13413-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="13413-119">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="13413-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="13413-120">Bayrak DLL üzerinde ayarlandıysa, DLL 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="13413-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="13413-121">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="13413-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="13413-122">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="13413-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="13413-123">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13413-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="13413-124">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="13413-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="13413-125">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="13413-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="13413-126">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="13413-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="13413-127">**Önemli:**  Tanımlayıcı adlı bir derlemeyi güncelleştirirseniz kodu yürütmeden önce yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13413-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="13413-128">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="13413-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="13413-129">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13413-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="13413-130">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13413-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="13413-131">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="13413-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="13413-132">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="13413-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="13413-133">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="13413-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="13413-134">**Note:**  Derlemeler yerel olarak çalıştırmak için 2,5 veya daha büyük bir CLR üstbilgi sürümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13413-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13413-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13413-135">Remarks</span></span>  
 <span data-ttu-id="13413-136">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="13413-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13413-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13413-137">See also</span></span>

- [<span data-ttu-id="13413-138">Araçlar</span><span class="sxs-lookup"><span data-stu-id="13413-138">Tools</span></span>](index.md)
- [<span data-ttu-id="13413-139">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="13413-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="13413-140">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="13413-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
