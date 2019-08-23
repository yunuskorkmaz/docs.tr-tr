---
title: -subsystemversion (C# derleyici seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: f70389f87bf49ffccded4aef775c27ed0d034e1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922460"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="ac17f-102">-subsystemversion (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ac17f-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="ac17f-103">Oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt sistemin en düşük sürümünü belirtir ve bu sayede yürütülebilir dosyanın çalışacağı Windows sürümlerini belirler.</span><span class="sxs-lookup"><span data-stu-id="ac17f-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="ac17f-104">En yaygın olarak, bu seçenek yürütülebilir dosyanın eski Windows sürümleriyle kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac17f-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="ac17f-105">Alt sistemin kendisini belirtmek için [-target](./target-compiler-option.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac17f-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac17f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac17f-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="ac17f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac17f-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="ac17f-108">Alt sistemin gerekli en düşük sürümü, birincil ve ikincil sürümler için nokta gösteriminde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="ac17f-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="ac17f-109">Örneğin, bu seçeneğin değerini 6,01 olarak ayarlarsanız, uygulamanın bu konunun ilerleyen kısımlarında açıklandığı gibi, bir uygulamanın Windows 7 ' den eski bir işletim sisteminde çalışabilebileceğinizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac17f-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="ac17f-110">`major` Ve`minor` değerlerini tamsayılar olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac17f-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="ac17f-111">`minor` Sürümdeki öndeki sıfırlar sürümü değiştirmez, ancak sonunda sıfır yapılır.</span><span class="sxs-lookup"><span data-stu-id="ac17f-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="ac17f-112">Örneğin, 6,1 ve 6,01 aynı sürüme başvurun, ancak 6,10 farklı bir sürüme başvurur.</span><span class="sxs-lookup"><span data-stu-id="ac17f-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="ac17f-113">Karışıklığın önüne geçmek için küçük sürümü iki basamakla ifade etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ac17f-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac17f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac17f-114">Remarks</span></span>

<span data-ttu-id="ac17f-115">Aşağıdaki tabloda, Windows 'un ortak alt sistem sürümleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac17f-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="ac17f-116">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="ac17f-116">Windows version</span></span>|<span data-ttu-id="ac17f-117">Alt sistem sürümü</span><span class="sxs-lookup"><span data-stu-id="ac17f-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="ac17f-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="ac17f-118">Windows 2000</span></span>|<span data-ttu-id="ac17f-119">5.00</span><span class="sxs-lookup"><span data-stu-id="ac17f-119">5.00</span></span>|
|<span data-ttu-id="ac17f-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="ac17f-120">Windows XP</span></span>|<span data-ttu-id="ac17f-121">5.01</span><span class="sxs-lookup"><span data-stu-id="ac17f-121">5.01</span></span>|
|<span data-ttu-id="ac17f-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="ac17f-122">Windows Server 2003</span></span>|<span data-ttu-id="ac17f-123">5.02</span><span class="sxs-lookup"><span data-stu-id="ac17f-123">5.02</span></span>|
|<span data-ttu-id="ac17f-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="ac17f-124">Windows Vista</span></span>|<span data-ttu-id="ac17f-125">6.00</span><span class="sxs-lookup"><span data-stu-id="ac17f-125">6.00</span></span>|
|<span data-ttu-id="ac17f-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="ac17f-126">Windows 7</span></span>|<span data-ttu-id="ac17f-127">6.01</span><span class="sxs-lookup"><span data-stu-id="ac17f-127">6.01</span></span>|
|<span data-ttu-id="ac17f-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="ac17f-128">Windows Server 2008</span></span>|<span data-ttu-id="ac17f-129">6.01</span><span class="sxs-lookup"><span data-stu-id="ac17f-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="ac17f-130">6.02</span><span class="sxs-lookup"><span data-stu-id="ac17f-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="ac17f-131">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="ac17f-131">Default values</span></span>

<span data-ttu-id="ac17f-132">**-Subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listede yer alan koşullara bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="ac17f-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="ac17f-133">Aşağıdaki listede herhangi bir derleyici seçeneğinin ayarlanmış olması halinde varsayılan değer 6,02 ' dir:</span><span class="sxs-lookup"><span data-stu-id="ac17f-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="ac17f-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="ac17f-134">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="ac17f-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="ac17f-135">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="ac17f-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="ac17f-136">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="ac17f-137">MSBuild kullanıyorsanız varsayılan değer 6,00 ' dir. .NET Framework 4,5 ' i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini belirlemediniz.</span><span class="sxs-lookup"><span data-stu-id="ac17f-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="ac17f-138">Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ac17f-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="ac17f-139">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="ac17f-139">Setting this option</span></span>

<span data-ttu-id="ac17f-140">Visual Studio 'da **-subsystemversion** derleyici seçeneğini ayarlamak için,. csproj dosyasını açmanız ve MSBuild xml içindeki `SubsystemVersion` özelliği için bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac17f-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="ac17f-141">Visual Studio IDE 'de bu seçeneği ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac17f-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="ac17f-142">Daha fazla bilgi için bu konunun önceki kısımlarında "varsayılan değerler" veya [genel MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ac17f-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac17f-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac17f-143">See also</span></span>

- [<span data-ttu-id="ac17f-144">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ac17f-144">C# Compiler Options</span></span>](./index.md)
