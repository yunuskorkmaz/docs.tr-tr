---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
description: CorFlags dönüştürme aracı CorFlags.exe anlayın. Bu araç taşınabilir bir yürütülebilir görüntünün üst bilgisinin CorFlags bölümünü yapılandırmanızı sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 4481e6718372fe7b58dbc05ab7cfe35e6d3047ce
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258058"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="cad01-104">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="cad01-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="cad01-105">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="cad01-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="cad01-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cad01-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="cad01-107">Aracı çalıştırmak için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="cad01-107">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="cad01-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="cad01-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad01-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cad01-109">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="cad01-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cad01-110">Parameters</span></span>  
  
|<span data-ttu-id="cad01-111">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="cad01-111">Required parameter</span></span>|<span data-ttu-id="cad01-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cad01-112">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="cad01-113">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="cad01-113">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="cad01-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="cad01-114">Option</span></span>|<span data-ttu-id="cad01-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cad01-115">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="cad01-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cad01-116">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="cad01-117">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cad01-117">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="cad01-118">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cad01-118">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="cad01-119">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="cad01-119">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="cad01-120">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cad01-120">Set this flag only on EXE files.</span></span> <span data-ttu-id="cad01-121">Bayrak DLL üzerinde ayarlandıysa, DLL 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="cad01-121">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="cad01-122">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cad01-122">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="cad01-123">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="cad01-123">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="cad01-124">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cad01-124">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="cad01-125">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="cad01-125">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="cad01-126">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cad01-126">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="cad01-127">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cad01-127">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="cad01-128">**Önemli:**  Tanımlayıcı adlı bir derlemeyi güncelleştirirseniz kodu yürütmeden önce yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cad01-128">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="cad01-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cad01-129">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="cad01-130">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cad01-130">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="cad01-131">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cad01-131">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="cad01-132">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="cad01-132">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="cad01-133">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="cad01-133">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="cad01-134">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="cad01-134">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="cad01-135">**Note:**  Derlemeler yerel olarak çalıştırmak için 2,5 veya daha büyük bir CLR üstbilgi sürümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cad01-135">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cad01-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cad01-136">Remarks</span></span>  

 <span data-ttu-id="cad01-137">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cad01-137">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad01-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cad01-138">See also</span></span>

- [<span data-ttu-id="cad01-139">Araçlar</span><span class="sxs-lookup"><span data-stu-id="cad01-139">Tools</span></span>](index.md)
- [<span data-ttu-id="cad01-140">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="cad01-140">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="cad01-141">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="cad01-141">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
