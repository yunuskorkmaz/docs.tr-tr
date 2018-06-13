---
title: -subsystemversion (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 25391dd504fb8a2b9458fd9495477258fc23d81a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215520"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="99cff-102">-subsystemversion (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="99cff-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="99cff-103">Böylece yürütülebilir dosyayı çalıştırmak Windows sürümlerinin belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="99cff-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="99cff-104">En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümlerinde kullanılamaz belirli güvenlik özellikleri yararlanabilirsiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="99cff-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99cff-105">Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="99cff-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99cff-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99cff-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99cff-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="99cff-108">Alt sistemi sürümü, birincil ve ikincil sürümleri için noktalı gösterim ifade gibi gerekli olan en düşük.</span><span class="sxs-lookup"><span data-stu-id="99cff-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="99cff-109">Örneğin, bir uygulama 6.01 için bu seçeneği değerini ayarlarsanız, bu konunun ilerleyen bölümlerinde tabloda açıklandığı gibi Windows 7'den daha eski bir işletim sisteminde çalışamaz belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99cff-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="99cff-110">Değerleri belirtmelisiniz `major` ve `minor` tamsayı olarak.</span><span class="sxs-lookup"><span data-stu-id="99cff-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="99cff-111">Önde gelen sıfır `minor` sürüm sürümü değişmez, ancak bunu sondaki sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="99cff-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="99cff-112">Örneğin, aynı sürüm 6.1 ve 6.01 bakın, ancak farklı bir sürüme 6.10 başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="99cff-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="99cff-113">Karışıklığı önlemek için iki basamaklı olarak alt sürüm ifade öneririz.</span><span class="sxs-lookup"><span data-stu-id="99cff-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cff-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99cff-114">Remarks</span></span>  
 <span data-ttu-id="99cff-115">Aşağıdaki tabloda Windows ortak alt sistemi sürümleri listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="99cff-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="99cff-116">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="99cff-116">Windows version</span></span>|<span data-ttu-id="99cff-117">Alt sistemi sürümü</span><span class="sxs-lookup"><span data-stu-id="99cff-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="99cff-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="99cff-118">Windows 2000</span></span>|<span data-ttu-id="99cff-119">5.00</span><span class="sxs-lookup"><span data-stu-id="99cff-119">5.00</span></span>|  
|<span data-ttu-id="99cff-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="99cff-120">Windows XP</span></span>|<span data-ttu-id="99cff-121">5.01</span><span class="sxs-lookup"><span data-stu-id="99cff-121">5.01</span></span>|  
|<span data-ttu-id="99cff-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="99cff-122">Windows Server 2003</span></span>|<span data-ttu-id="99cff-123">5.02</span><span class="sxs-lookup"><span data-stu-id="99cff-123">5.02</span></span>|  
|<span data-ttu-id="99cff-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="99cff-124">Windows Vista</span></span>|<span data-ttu-id="99cff-125">6.00</span><span class="sxs-lookup"><span data-stu-id="99cff-125">6.00</span></span>|  
|<span data-ttu-id="99cff-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="99cff-126">Windows 7</span></span>|<span data-ttu-id="99cff-127">6.01</span><span class="sxs-lookup"><span data-stu-id="99cff-127">6.01</span></span>|  
|<span data-ttu-id="99cff-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="99cff-128">Windows Server 2008</span></span>|<span data-ttu-id="99cff-129">6.01</span><span class="sxs-lookup"><span data-stu-id="99cff-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="99cff-130">6.02</span><span class="sxs-lookup"><span data-stu-id="99cff-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="99cff-131">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="99cff-131">Default values</span></span>  
 <span data-ttu-id="99cff-132">Varsayılan değer olan **- subsystemversion** derleyici seçeneği, aşağıdaki listeden koşulların bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="99cff-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="99cff-133">Aşağıdaki listede herhangi bir derleyici seçeneği ayarlandıysa varsayılan değeri 6.02 şöyledir:</span><span class="sxs-lookup"><span data-stu-id="99cff-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="99cff-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="99cff-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="99cff-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="99cff-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="99cff-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="99cff-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="99cff-137">MSBuild kullanıyorsanız, varsayılan değer 6,00, hedefleme [!INCLUDE[net_v45](~/includes/net-v45-md.md)], ve bu listede daha önce belirtilmiş derleyici seçenekleri hiçbirini ayarlamadıysanız.</span><span class="sxs-lookup"><span data-stu-id="99cff-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="99cff-138">Önceki koşulların hiçbiri true ise varsayılan değer 4.00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="99cff-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="99cff-139">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="99cff-139">Setting this option</span></span>  
 <span data-ttu-id="99cff-140">Ayarlamak için **- subsystemversion** derleyici seçeneği Visual Studio'da .csproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özellik.</span><span class="sxs-lookup"><span data-stu-id="99cff-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="99cff-141">Bu seçenek, Visual Studio IDE içinde ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="99cff-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="99cff-142">Daha fazla bilgi için bu konunun önceki kısımlarında "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="99cff-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cff-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99cff-143">See Also</span></span>  
 [<span data-ttu-id="99cff-144">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="99cff-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
