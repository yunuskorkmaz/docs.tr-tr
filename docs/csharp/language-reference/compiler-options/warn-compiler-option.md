---
title: -warn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d495ef76dc390d8dd2a361d5530f9e39d7128b3e
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867613"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="bd7de-102">-warn (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bd7de-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="bd7de-103">**-Warn** seçeneği derleyicinin görüntüleyeceği uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd7de-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7de-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bd7de-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd7de-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="bd7de-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="bd7de-106">Derleme için görüntülenmesini istediğiniz uyarı düzeyi: daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir; daha yüksek numaralar daha fazla uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd7de-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="bd7de-107">Değer sıfır veya pozitif bir tamsayı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="bd7de-107">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="bd7de-108">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="bd7de-108">Warning level</span></span>|<span data-ttu-id="bd7de-109">Anlamı</span><span class="sxs-lookup"><span data-stu-id="bd7de-109">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="bd7de-110">0</span><span class="sxs-lookup"><span data-stu-id="bd7de-110">0</span></span>|<span data-ttu-id="bd7de-111">Tüm uyarı iletilerinin emisyonunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="bd7de-111">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="bd7de-112">1</span><span class="sxs-lookup"><span data-stu-id="bd7de-112">1</span></span>|<span data-ttu-id="bd7de-113">Ciddi uyarı iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd7de-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="bd7de-114">2</span><span class="sxs-lookup"><span data-stu-id="bd7de-114">2</span></span>|<span data-ttu-id="bd7de-115">Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd7de-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="bd7de-116">3</span><span class="sxs-lookup"><span data-stu-id="bd7de-116">3</span></span>|<span data-ttu-id="bd7de-117">Düzey 2 uyarılarını ve her zaman veya olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="bd7de-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="bd7de-118">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="bd7de-118">4 (the default)</span></span>|<span data-ttu-id="bd7de-119">Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd7de-119">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="bd7de-120">5</span><span class="sxs-lookup"><span data-stu-id="bd7de-120">5</span></span>|<span data-ttu-id="bd7de-121">4. düzey uyarıları ve C# 9,0 ile gönderilen derleyicinin [ek uyarılarını](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bd7de-121">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="bd7de-122">5 ' ten büyük</span><span class="sxs-lookup"><span data-stu-id="bd7de-122">Greater than 5</span></span>|<span data-ttu-id="bd7de-123">5 ' ten büyük bir değer 5 olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bd7de-123">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="bd7de-124">Genellikle rastgele büyük bir değer (örneğin,), `9999` derleyici yeni uyarı düzeyleriyle güncelleştirilirse her zaman tüm uyarılara sahip olduğunuzdan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd7de-124">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="bd7de-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd7de-125">Remarks</span></span>  
 <span data-ttu-id="bd7de-126">Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd7de-126">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="bd7de-127">Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz. [C# derleyici hataları](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd7de-127">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="bd7de-128">Tüm uyarıları hata olarak değerlendirmek için [-warnaserror](./warnaserror-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd7de-128">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="bd7de-129">Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd7de-129">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="bd7de-130">**-w** , **-Warn**kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="bd7de-130">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bd7de-131">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bd7de-131">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bd7de-132">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="bd7de-132">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bd7de-133">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bd7de-133">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bd7de-134">**Uyarı düzeyi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bd7de-134">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="bd7de-135">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> ..</span><span class="sxs-lookup"><span data-stu-id="bd7de-135">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd7de-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd7de-136">Example</span></span>  
 <span data-ttu-id="bd7de-137">Derleyin `in.cs` ve derleyicinin yalnızca düzey 1 uyarılarını görüntülemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bd7de-137">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd7de-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd7de-138">See also</span></span>

- [<span data-ttu-id="bd7de-139">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bd7de-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bd7de-140">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bd7de-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
