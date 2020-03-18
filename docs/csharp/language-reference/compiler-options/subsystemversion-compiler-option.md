---
title: -alt sistem versiyonu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802037"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="24555-102">-alt sistem versiyonu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="24555-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="24555-103">Oluşturulan yürütülebilir dosyanın çalıştırılabildiği alt sistemin minimum sürümünü belirtir ve bu nedenle yürütülebilir dosyanın çalıştırılabildiği Windows sürümlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="24555-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="24555-104">En yaygın olarak, bu seçenek, yürütülebilir dosyanın Windows'un eski sürümlerinde kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="24555-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="24555-105">Alt sistemin kendisini belirtmek için [-hedef](./target-compiler-option.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="24555-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="24555-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24555-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="24555-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24555-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="24555-108">Alt sistemin, büyük ve küçük sürümler için nokta gösteriminde ifade edilen minimum gerekli sürümü.</span><span class="sxs-lookup"><span data-stu-id="24555-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="24555-109">Örneğin, bu seçeneğin değerini 6.01 olarak ayarlarsanız, bu konunun daha sonra açıkladığı gibi, bir uygulamanın Windows 7'den eski bir işletim sisteminde çalıştırılamamasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24555-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="24555-110">Ve tümseler `major` `minor` olarak değerleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24555-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="24555-111">`minor` Sürümdeki satır aralığı sıfırlar sürümü değiştirmez, ancak sondaki sıfırlar değiştirir.</span><span class="sxs-lookup"><span data-stu-id="24555-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="24555-112">Örneğin, 6.1 ve 6.01 aynı sürüme atıfta bulunur, ancak 6.10 farklı bir sürüme başvurur.</span><span class="sxs-lookup"><span data-stu-id="24555-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="24555-113">Karışıklığı önlemek için küçük sürümü iki basamak olarak ifade etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="24555-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="24555-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24555-114">Remarks</span></span>

<span data-ttu-id="24555-115">Aşağıdaki tabloda Windows'un ortak alt sistem sürümleri listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="24555-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="24555-116">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="24555-116">Windows version</span></span>|<span data-ttu-id="24555-117">Alt sistem sürümü</span><span class="sxs-lookup"><span data-stu-id="24555-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="24555-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="24555-118">Windows 2000</span></span>|<span data-ttu-id="24555-119">5,00</span><span class="sxs-lookup"><span data-stu-id="24555-119">5.00</span></span>|
|<span data-ttu-id="24555-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="24555-120">Windows XP</span></span>|<span data-ttu-id="24555-121">5.01</span><span class="sxs-lookup"><span data-stu-id="24555-121">5.01</span></span>|
|<span data-ttu-id="24555-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="24555-122">Windows Server 2003</span></span>|<span data-ttu-id="24555-123">5.02</span><span class="sxs-lookup"><span data-stu-id="24555-123">5.02</span></span>|
|<span data-ttu-id="24555-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="24555-124">Windows Vista</span></span>|<span data-ttu-id="24555-125">6.00</span><span class="sxs-lookup"><span data-stu-id="24555-125">6.00</span></span>|
|<span data-ttu-id="24555-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="24555-126">Windows 7</span></span>|<span data-ttu-id="24555-127">6.01</span><span class="sxs-lookup"><span data-stu-id="24555-127">6.01</span></span>|
|<span data-ttu-id="24555-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="24555-128">Windows Server 2008</span></span>|<span data-ttu-id="24555-129">6.01</span><span class="sxs-lookup"><span data-stu-id="24555-129">6.01</span></span>|
|<span data-ttu-id="24555-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="24555-130">Windows 8</span></span>|<span data-ttu-id="24555-131">6.02</span><span class="sxs-lookup"><span data-stu-id="24555-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="24555-132">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="24555-132">Default values</span></span>

<span data-ttu-id="24555-133">**-subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listedeki koşullara bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="24555-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="24555-134">Aşağıdaki listedeki herhangi bir derleyici seçeneği ayarlanmışsa varsayılan değer 6,02'dir:</span><span class="sxs-lookup"><span data-stu-id="24555-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="24555-135">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="24555-135">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="24555-136">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="24555-136">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="24555-137">-platform:kol</span><span class="sxs-lookup"><span data-stu-id="24555-137">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="24555-138">MSBuild kullanıyorsanız, .NET Framework 4.5'i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini ayarlamamışsanız varsayılan değer 6,00'dır.</span><span class="sxs-lookup"><span data-stu-id="24555-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="24555-139">Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00'dir.</span><span class="sxs-lookup"><span data-stu-id="24555-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="24555-140">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="24555-140">Setting this option</span></span>

<span data-ttu-id="24555-141">Visual Studio'da **-subsystemversion** derleyici seçeneğini ayarlamak için .csproj dosyasını açmanız ve MSBuild XML'deki `SubsystemVersion` özellik için bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24555-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="24555-142">Bu seçeneği Visual Studio IDE'de ayarlayamam.</span><span class="sxs-lookup"><span data-stu-id="24555-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="24555-143">Daha fazla bilgi için, bu konu veya [Ortak MSBuild Project Özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)daha önce "Varsayılan değerler" bakın.</span><span class="sxs-lookup"><span data-stu-id="24555-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="24555-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24555-144">See also</span></span>

- [<span data-ttu-id="24555-145">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="24555-145">C# Compiler Options</span></span>](./index.md)
