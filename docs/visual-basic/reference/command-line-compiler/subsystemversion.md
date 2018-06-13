---
title: -subsystemversion (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eb8aa1cd86dba4a1a65edf31a3b18df7085a33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654456"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="bbe4f-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbe4f-102">-subsystemversion (Visual Basic)</span></span>
<span data-ttu-id="bbe4f-103">Böylece yürütülebilir dosyayı çalıştırmak Windows sürümlerinin belirleme oluşturulan yürütülebilir dosyanın çalıştırılabileceği alt en düşük sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="bbe4f-104">En yaygın olarak, bu seçeneği, yürütülebilir dosyanın daha eski Windows sürümlerinde kullanılamaz belirli güvenlik özellikleri yararlanabilirsiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbe4f-105">Alt belirtmek için kullanın [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe4f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbe4f-106">Syntax</span></span>  
  
```vb  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbe4f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbe4f-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="bbe4f-108">Alt sistemi sürümü, birincil ve ikincil sürümleri için noktalı gösterim ifade gibi gerekli olan en düşük.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="bbe4f-109">Örneğin, bir uygulama 6.01 için bu seçeneği değerini ayarlarsanız, bu konunun ilerleyen bölümlerinde tabloda açıklandığı gibi Windows 7'den daha eski bir işletim sisteminde çalışamaz belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="bbe4f-110">Değerleri belirtmelisiniz `major` ve `minor` tamsayı olarak.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="bbe4f-111">Önde gelen sıfır `minor` sürüm sürümü değişmez, ancak bunu sondaki sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="bbe4f-112">Örneğin, aynı sürüm 6.1 ve 6.01 bakın, ancak farklı bir sürüme 6.10 başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="bbe4f-113">Karışıklığı önlemek için iki basamaklı olarak alt sürüm ifade öneririz.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbe4f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbe4f-114">Remarks</span></span>  
 <span data-ttu-id="bbe4f-115">Aşağıdaki tabloda Windows ortak alt sistemi sürümleri listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="bbe4f-116">Windows sürümü</span><span class="sxs-lookup"><span data-stu-id="bbe4f-116">Windows version</span></span>|<span data-ttu-id="bbe4f-117">Alt sistemi sürümü</span><span class="sxs-lookup"><span data-stu-id="bbe4f-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="bbe4f-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="bbe4f-118">Windows 2000</span></span>|<span data-ttu-id="bbe4f-119">5.00</span><span class="sxs-lookup"><span data-stu-id="bbe4f-119">5.00</span></span>|  
|<span data-ttu-id="bbe4f-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="bbe4f-120">Windows XP</span></span>|<span data-ttu-id="bbe4f-121">5.01</span><span class="sxs-lookup"><span data-stu-id="bbe4f-121">5.01</span></span>|  
|<span data-ttu-id="bbe4f-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="bbe4f-122">Windows Server 2003</span></span>|<span data-ttu-id="bbe4f-123">5.02</span><span class="sxs-lookup"><span data-stu-id="bbe4f-123">5.02</span></span>|  
|<span data-ttu-id="bbe4f-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="bbe4f-124">Windows Vista</span></span>|<span data-ttu-id="bbe4f-125">6.00</span><span class="sxs-lookup"><span data-stu-id="bbe4f-125">6.00</span></span>|  
|<span data-ttu-id="bbe4f-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="bbe4f-126">Windows 7</span></span>|<span data-ttu-id="bbe4f-127">6.01</span><span class="sxs-lookup"><span data-stu-id="bbe4f-127">6.01</span></span>|  
|<span data-ttu-id="bbe4f-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="bbe4f-128">Windows Server 2008</span></span>|<span data-ttu-id="bbe4f-129">6.01</span><span class="sxs-lookup"><span data-stu-id="bbe4f-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="bbe4f-130">6.02</span><span class="sxs-lookup"><span data-stu-id="bbe4f-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="bbe4f-131">Varsayılan değerler</span><span class="sxs-lookup"><span data-stu-id="bbe4f-131">Default values</span></span>  
 <span data-ttu-id="bbe4f-132">Varsayılan değer olan **- subsystemversion** derleyici seçeneği, aşağıdaki listeden koşulların bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="bbe4f-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="bbe4f-133">Aşağıdaki listede herhangi bir derleyici seçeneği ayarlandıysa varsayılan değeri 6.02 şöyledir:</span><span class="sxs-lookup"><span data-stu-id="bbe4f-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="bbe4f-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="bbe4f-134">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="bbe4f-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="bbe4f-135">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [<span data-ttu-id="bbe4f-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="bbe4f-136">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   <span data-ttu-id="bbe4f-137">MSBuild kullanıyorsanız, varsayılan değer 6,00, hedefleme [!INCLUDE[net_v45](~/includes/net-v45-md.md)], ve bu listede daha önce belirtilmiş derleyici seçenekleri hiçbirini ayarlamadıysanız.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="bbe4f-138">Önceki koşulların hiçbiri true ise varsayılan değer 4.00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="bbe4f-139">Bu seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="bbe4f-139">Setting this option</span></span>  
 <span data-ttu-id="bbe4f-140">Ayarlamak için **- subsystemversion** derleyici seçeneği Visual Studio'da .vbproj dosyasını açın ve için bir değer belirtmeniz gerekir `SubsystemVersion` MSBuild XML özellik.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="bbe4f-141">Bu seçenek, Visual Studio IDE içinde ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="bbe4f-142">Daha fazla bilgi için bu konunun önceki kısımlarında "Varsayılan değerler" konusuna bakın veya [yaygın MSBuild proje özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="bbe4f-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="bbe4f-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe4f-143">See Also</span></span>  
[<span data-ttu-id="bbe4f-144">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bbe4f-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

[<span data-ttu-id="bbe4f-145">MSBuild Özellikleri</span><span class="sxs-lookup"><span data-stu-id="bbe4f-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
