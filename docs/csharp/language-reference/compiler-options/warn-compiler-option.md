---
title: -warn (C# Derleyici Seçenekleri)
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
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 14656fa25ea1d01339bd63efb999e938e1243db8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865614"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="ee42d-102">-warn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ee42d-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="ee42d-103">**-Warn** seçeneği, derleyicinin görüntülenecek uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee42d-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee42d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee42d-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee42d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ee42d-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="ee42d-106">Derleme için görüntülenmesini istediğiniz uyarı düzeyini: yalnızca yüksek önem düzeyindeki uyarılar; düşük numaralarını göster daha yüksek numaralar daha fazla uyarıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee42d-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="ee42d-107">Geçerli değerler 0-4:</span><span class="sxs-lookup"><span data-stu-id="ee42d-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="ee42d-108">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="ee42d-108">Warning level</span></span>|<span data-ttu-id="ee42d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee42d-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="ee42d-110">0</span><span class="sxs-lookup"><span data-stu-id="ee42d-110">0</span></span>|<span data-ttu-id="ee42d-111">Tüm uyarı iletilerini arabellek devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ee42d-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="ee42d-112">1.</span><span class="sxs-lookup"><span data-stu-id="ee42d-112">1</span></span>|<span data-ttu-id="ee42d-113">Önemli uyarı iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee42d-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="ee42d-114">2</span><span class="sxs-lookup"><span data-stu-id="ee42d-114">2</span></span>|<span data-ttu-id="ee42d-115">1. düzey uyarıları ve bazı, görüntüler, sınıf üyeleri gizleme hakkında uyarılar gibi daha az öneme sahip uyarılar.</span><span class="sxs-lookup"><span data-stu-id="ee42d-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="ee42d-116">3</span><span class="sxs-lookup"><span data-stu-id="ee42d-116">3</span></span>|<span data-ttu-id="ee42d-117">Düzey 2 uyarıları görüntüler belirli, uyarılar için her zaman değerlendirin ifadeler hakkında gibi daha az öneme sahip uyarılar ayrıca `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="ee42d-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="ee42d-118">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="ee42d-118">4 (the default)</span></span>|<span data-ttu-id="ee42d-119">Tüm görüntüler, 3 uyarıları ve bilgilendirici uyarılar düzey.</span><span class="sxs-lookup"><span data-stu-id="ee42d-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee42d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee42d-120">Remarks</span></span>  
 <span data-ttu-id="ee42d-121">Bir hata veya uyarı hakkında bilgi almak için Yardım dizini hata kodunu bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee42d-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="ee42d-122">Bir hata veya uyarı hakkında bilgi almak diğer yolları için bkz. [C# derleyici hataları](../../../csharp/language-reference/compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee42d-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="ee42d-123">Kullanım [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) tüm uyarıları hata olarak değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="ee42d-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="ee42d-124">Kullanım [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı.</span><span class="sxs-lookup"><span data-stu-id="ee42d-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="ee42d-125">**-w** öğesinin kısa biçimidir **-warn**.</span><span class="sxs-lookup"><span data-stu-id="ee42d-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ee42d-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ee42d-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ee42d-127">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="ee42d-127">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ee42d-128">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="ee42d-128">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ee42d-129">Değiştirme **uyarı düzeyi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ee42d-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="ee42d-130">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee42d-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee42d-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee42d-131">Example</span></span>  
 <span data-ttu-id="ee42d-132">Derleme `in.cs` ve derleyicinin yalnızca 1. düzey uyarıları göster:</span><span class="sxs-lookup"><span data-stu-id="ee42d-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee42d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee42d-133">See Also</span></span>  

- [<span data-ttu-id="ee42d-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ee42d-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="ee42d-135">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ee42d-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
