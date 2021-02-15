---
description: :-Subsystemversion (Visual Basic) hakkında daha fazla bilgi
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 7f15d0257d65c0883d3028b20515e29caf25be9b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456412"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="2162a-103">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2162a-103">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="2162a-104">Oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt sistemin en düşük sürümünü belirtir ve bu sayede yürütülebilir dosyanın çalışacağı Windows sürümlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="2162a-104">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="2162a-105">En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2162a-105">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="2162a-106">Alt sistemin kendisini belirtmek için [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2162a-106">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="2162a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2162a-107">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="2162a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2162a-108">Parameters</span></span>

`major.minor`

<span data-ttu-id="2162a-109">Alt sistemin gerekli en düşük sürümü, birincil ve ikincil sürümler için nokta gösteriminde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="2162a-109">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="2162a-110">Örneğin, bu seçeneğin değerini 6,01 olarak ayarlarsanız, uygulamanın bu konunun ilerleyen kısımlarında açıklandığı gibi, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışabilebileceğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2162a-110">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="2162a-111">Ve değerlerini tamsayılar olarak belirtmeniz gerekir `major` `minor` .</span><span class="sxs-lookup"><span data-stu-id="2162a-111">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="2162a-112">Sürümdeki öndeki sıfırlar `minor` sürümü değiştirmez, ancak sonunda sıfır yapılır.</span><span class="sxs-lookup"><span data-stu-id="2162a-112">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="2162a-113">Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur.</span><span class="sxs-lookup"><span data-stu-id="2162a-113">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="2162a-114">Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="2162a-114">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="2162a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2162a-115">Remarks</span></span>

<span data-ttu-id="2162a-116">Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2162a-116">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="2162a-117">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="2162a-117">Windows version</span></span>|<span data-ttu-id="2162a-118">Alt sistem sürümü</span><span class="sxs-lookup"><span data-stu-id="2162a-118">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="2162a-119">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="2162a-119">Windows 2000</span></span>|<span data-ttu-id="2162a-120">5.00</span><span class="sxs-lookup"><span data-stu-id="2162a-120">5.00</span></span>|
|<span data-ttu-id="2162a-121">Windows XP</span><span class="sxs-lookup"><span data-stu-id="2162a-121">Windows XP</span></span>|<span data-ttu-id="2162a-122">5,01</span><span class="sxs-lookup"><span data-stu-id="2162a-122">5.01</span></span>|
|<span data-ttu-id="2162a-123">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2162a-123">Windows Server 2003</span></span>|<span data-ttu-id="2162a-124">5,02</span><span class="sxs-lookup"><span data-stu-id="2162a-124">5.02</span></span>|
|<span data-ttu-id="2162a-125">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="2162a-125">Windows Vista</span></span>|<span data-ttu-id="2162a-126">6,00</span><span class="sxs-lookup"><span data-stu-id="2162a-126">6.00</span></span>|
|<span data-ttu-id="2162a-127">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2162a-127">Windows 7</span></span>|<span data-ttu-id="2162a-128">6,01</span><span class="sxs-lookup"><span data-stu-id="2162a-128">6.01</span></span>|
|<span data-ttu-id="2162a-129">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="2162a-129">Windows Server 2008</span></span>|<span data-ttu-id="2162a-130">6,01</span><span class="sxs-lookup"><span data-stu-id="2162a-130">6.01</span></span>|
|<span data-ttu-id="2162a-131">Windows 8</span><span class="sxs-lookup"><span data-stu-id="2162a-131">Windows 8</span></span>|<span data-ttu-id="2162a-132">6,02</span><span class="sxs-lookup"><span data-stu-id="2162a-132">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="2162a-133">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="2162a-133">Default values</span></span>

<span data-ttu-id="2162a-134">**-Subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="2162a-134">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="2162a-135">Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:</span><span class="sxs-lookup"><span data-stu-id="2162a-135">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="2162a-136">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="2162a-136">-target:appcontainerexe</span></span>](target.md)

  - [<span data-ttu-id="2162a-137">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="2162a-137">-target:winmdobj</span></span>](target.md)

  - [<span data-ttu-id="2162a-138">-Platform: ARM</span><span class="sxs-lookup"><span data-stu-id="2162a-138">-platform:arm</span></span>](platform.md)

- <span data-ttu-id="2162a-139">MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.</span><span class="sxs-lookup"><span data-stu-id="2162a-139">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="2162a-140">Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2162a-140">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="2162a-141">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="2162a-141">Setting this option</span></span>

<span data-ttu-id="2162a-142">Visual Studio 'da **-subsystemversion** derleyici seçeneğini ayarlamak için,. vbproj dosyasını açmanız ve `SubsystemVersion` MSBuild xml içindeki özelliği için bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2162a-142">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="2162a-143">Visual Studio IDE 'de bu seçeneği ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2162a-143">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="2162a-144">Daha fazla bilgi için bu konunun önceki kısımlarında "varsayılan değerler" veya [genel MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2162a-144">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="2162a-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2162a-145">See also</span></span>

- [<span data-ttu-id="2162a-146">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2162a-146">Visual Basic Command-Line Compiler</span></span>](index.md)

- [<span data-ttu-id="2162a-147">MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="2162a-147">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
