---
title: -subsystemversion (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: ff4cd196edc1ec04f8abcecfa1a7a4e99e32dd56
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749296"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="a87bc-102">-subsystemversion (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a87bc-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="a87bc-103">Böylece Windows yürütülebilir dosyayı çalışabileceği sürümleri belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="a87bc-104">En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümleri ile kullanılamayan belirli güvenlik özellikleri yararlanabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="a87bc-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a87bc-105">Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a87bc-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87bc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a87bc-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a87bc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a87bc-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="a87bc-108">Alt sistem sürümünü, birincil ve ikincil sürüme bir nokta gösterimi ifade olarak gerekli olan en düşük.</span><span class="sxs-lookup"><span data-stu-id="a87bc-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="a87bc-109">Örneğin, bir uygulama için 6.01, bu seçenek değerini ayarlarsanız bu konunun ilerleyen bölümlerindeki bir tabloda açıklandığı gibi Windows 7'den eski bir işletim sisteminde çalıştıramazsınız belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="a87bc-110">Değerleri belirtmelisiniz `major` ve `minor` tamsayılar olarak.</span><span class="sxs-lookup"><span data-stu-id="a87bc-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="a87bc-111">Baştaki sıfırları `minor` sürümü, sürüm değişmez ancak Sondaki sıfırları yapın.</span><span class="sxs-lookup"><span data-stu-id="a87bc-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="a87bc-112">Örneğin, aynı sürüme 6.1 ve 6.01 bakın, ancak farklı bir sürüme 6.10 başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="a87bc-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="a87bc-113">Alt sürüm iki basamak Karışıklığı önlemek için ifade öneririz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87bc-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a87bc-114">Remarks</span></span>  
 <span data-ttu-id="a87bc-115">Aşağıdaki tabloda Windows ortak alt sistemi sürümlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="a87bc-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="a87bc-116">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="a87bc-116">Windows version</span></span>|<span data-ttu-id="a87bc-117">Alt sistem sürümü</span><span class="sxs-lookup"><span data-stu-id="a87bc-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="a87bc-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="a87bc-118">Windows 2000</span></span>|<span data-ttu-id="a87bc-119">5.00</span><span class="sxs-lookup"><span data-stu-id="a87bc-119">5.00</span></span>|  
|<span data-ttu-id="a87bc-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="a87bc-120">Windows XP</span></span>|<span data-ttu-id="a87bc-121">5.01</span><span class="sxs-lookup"><span data-stu-id="a87bc-121">5.01</span></span>|  
|<span data-ttu-id="a87bc-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="a87bc-122">Windows Server 2003</span></span>|<span data-ttu-id="a87bc-123">5.02</span><span class="sxs-lookup"><span data-stu-id="a87bc-123">5.02</span></span>|  
|<span data-ttu-id="a87bc-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="a87bc-124">Windows Vista</span></span>|<span data-ttu-id="a87bc-125">6.00</span><span class="sxs-lookup"><span data-stu-id="a87bc-125">6.00</span></span>|  
|<span data-ttu-id="a87bc-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a87bc-126">Windows 7</span></span>|<span data-ttu-id="a87bc-127">6.01</span><span class="sxs-lookup"><span data-stu-id="a87bc-127">6.01</span></span>|  
|<span data-ttu-id="a87bc-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a87bc-128">Windows Server 2008</span></span>|<span data-ttu-id="a87bc-129">6.01</span><span class="sxs-lookup"><span data-stu-id="a87bc-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="a87bc-130">6.02</span><span class="sxs-lookup"><span data-stu-id="a87bc-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="a87bc-131">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="a87bc-131">Default values</span></span>  
 <span data-ttu-id="a87bc-132">Varsayılan değer olan **- subsystemversion** derleyici seçeneği, aşağıdaki listede koşul bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="a87bc-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="a87bc-133">Aşağıdaki listedeki herhangi bir derleyici seçeneği ayarlanırsa varsayılan değeri 6.02 şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a87bc-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="a87bc-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="a87bc-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="a87bc-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="a87bc-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="a87bc-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="a87bc-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="a87bc-137">MSBuild kullanıyorsanız, varsayılan değer 6.00:, hedeflediğiniz [!INCLUDE[net_v45](~/includes/net-v45-md.md)], ve bu listede daha önce belirtilmiş derleyici seçeneklerinden herhangi birini ayarlamasını yapmadığınızı.</span><span class="sxs-lookup"><span data-stu-id="a87bc-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="a87bc-138">Yukarıdaki koşulların hiçbiri doğru olması durumunda varsayılan 4.00 değerdir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="a87bc-139">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="a87bc-139">Setting this option</span></span>  
 <span data-ttu-id="a87bc-140">Ayarlanacak **- subsystemversion** derleyici seçeneğini Visual Studio'da .csproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özelliği.</span><span class="sxs-lookup"><span data-stu-id="a87bc-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="a87bc-141">Visual Studio IDE'de bu seçeneği ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="a87bc-142">Daha fazla bilgi için bu konuda daha önce "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="a87bc-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87bc-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-143">See Also</span></span>  

- [<span data-ttu-id="a87bc-144">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a87bc-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
