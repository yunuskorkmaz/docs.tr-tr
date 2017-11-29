---
title: "-warn (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab5748f43777ec545e76100543473785894461cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="warn-c-compiler-options"></a><span data-ttu-id="771dc-102">/warn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="771dc-102">/warn (C# Compiler Options)</span></span>
<span data-ttu-id="771dc-103">**/ Warn** seçeneği derleyici görüntülenecek uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="771dc-103">The **/warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="771dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="771dc-104">Syntax</span></span>  
  
```console  
/warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="771dc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="771dc-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="771dc-106">Derleme için görüntülenmesini istediğiniz uyarı düzeyini: küçük numaralar yalnızca yüksek öneme sahip uyarılar; büyük sayılar daha fazla uyarıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="771dc-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="771dc-107">Geçerli değerler 0-4 şunlardır:</span><span class="sxs-lookup"><span data-stu-id="771dc-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="771dc-108">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="771dc-108">Warning level</span></span>|<span data-ttu-id="771dc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="771dc-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="771dc-110">0</span><span class="sxs-lookup"><span data-stu-id="771dc-110">0</span></span>|<span data-ttu-id="771dc-111">Tüm uyarı iletilerini yayımlanmasını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="771dc-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="771dc-112">1.</span><span class="sxs-lookup"><span data-stu-id="771dc-112">1</span></span>|<span data-ttu-id="771dc-113">Önemli uyarı iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="771dc-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="771dc-114">2</span><span class="sxs-lookup"><span data-stu-id="771dc-114">2</span></span>|<span data-ttu-id="771dc-115">Düzey 1 uyarıları artı bazı, görüntüler, sınıf üyelerini gizleme uyarıları gibi daha düşük öneme sahip uyarılar.</span><span class="sxs-lookup"><span data-stu-id="771dc-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="771dc-116">3</span><span class="sxs-lookup"><span data-stu-id="771dc-116">3</span></span>|<span data-ttu-id="771dc-117">Düzey 2 uyarıları görüntüler için her zaman değerlendirin ifadeler hakkında uyarılar gibi belirli, daha az önemli uyarıları artı `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="771dc-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="771dc-118">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="771dc-118">4 (the default)</span></span>|<span data-ttu-id="771dc-119">Tüm görüntüler 3 uyarıları ve bilgilendirici uyarılar düzeyi.</span><span class="sxs-lookup"><span data-stu-id="771dc-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="771dc-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="771dc-120">Remarks</span></span>  
 <span data-ttu-id="771dc-121">Bir hata veya uyarı hakkında bilgi almak için Yardım dizini hata kodunu arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="771dc-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="771dc-122">Bir hata veya uyarı hakkında bilgi almak diğer yolları için bkz: [C# derleyici hataları](../../../csharp/language-reference/compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="771dc-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="771dc-123">Kullanım [/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) tüm uyarıları hata olarak değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="771dc-123">Use [/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="771dc-124">Kullanım [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="771dc-124">Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="771dc-125">**/w** kısa biçimi olan **/ warn**.</span><span class="sxs-lookup"><span data-stu-id="771dc-125">**/w** is the short form of **/warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="771dc-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="771dc-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="771dc-127">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="771dc-127">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="771dc-128">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="771dc-128">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="771dc-129">Değiştirme **uyarı düzeyi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="771dc-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="771dc-130">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="771dc-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="771dc-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="771dc-131">Example</span></span>  
 <span data-ttu-id="771dc-132">Derleme `in.cs` ve derleyicinin yalnızca düzey 1 Uyarıları görüntüle:</span><span class="sxs-lookup"><span data-stu-id="771dc-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc /warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="771dc-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="771dc-133">See Also</span></span>  
 [<span data-ttu-id="771dc-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="771dc-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="771dc-135">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="771dc-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
