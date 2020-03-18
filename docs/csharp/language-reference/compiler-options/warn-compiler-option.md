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
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602398"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="12547-102">-warn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="12547-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="12547-103">**-uyarseçeneği** derleyicinin görüntülenmesi için uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12547-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12547-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12547-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="12547-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="12547-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="12547-106">Derleme için görüntülenmesini istediğiniz uyarı düzeyi: Daha düşük sayılar yalnızca yüksek önem uyarılarını gösterir; daha yüksek sayılar daha fazla uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="12547-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="12547-107">Geçerli değerler 0-4:</span><span class="sxs-lookup"><span data-stu-id="12547-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="12547-108">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="12547-108">Warning level</span></span>|<span data-ttu-id="12547-109">Anlamı</span><span class="sxs-lookup"><span data-stu-id="12547-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="12547-110">0</span><span class="sxs-lookup"><span data-stu-id="12547-110">0</span></span>|<span data-ttu-id="12547-111">Tüm uyarı iletilerinin emisyonunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="12547-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="12547-112">1</span><span class="sxs-lookup"><span data-stu-id="12547-112">1</span></span>|<span data-ttu-id="12547-113">Ciddi uyarı iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12547-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="12547-114">2</span><span class="sxs-lookup"><span data-stu-id="12547-114">2</span></span>|<span data-ttu-id="12547-115">Düzey 1 uyarılarının yanı sıra sınıf üyelerini gizleme yle ilgili uyarılar gibi belirli, daha az ciddi uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12547-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="12547-116">3</span><span class="sxs-lookup"><span data-stu-id="12547-116">3</span></span>|<span data-ttu-id="12547-117">Düzey 2 uyarılarının yanı sıra, her zaman değer biçilen `true` ifadeler `false`hakkındaki uyarılar gibi belirli, daha az ciddi uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12547-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="12547-118">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="12547-118">4 (the default)</span></span>|<span data-ttu-id="12547-119">Tüm düzey 3 uyarıları ve bilgilendirme uyarılarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12547-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12547-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12547-120">Remarks</span></span>  
 <span data-ttu-id="12547-121">Bir hata veya uyarı hakkında bilgi almak için Yardım Dizini'ndeki hata kodunu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12547-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="12547-122">Bir hata veya uyarı hakkında bilgi almanın diğer yolları için [C# Derleyici Hataları'na](../compiler-messages/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="12547-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="12547-123">Tüm uyarıları hata olarak ele almak için [-warnaserror'ı](./warnaserror-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="12547-123">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="12547-124">Bazı [-nowarn](./nowarn-compiler-option.md) uyarıları devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12547-124">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="12547-125">**-w** kısa şeklidir **-warn**.</span><span class="sxs-lookup"><span data-stu-id="12547-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="12547-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="12547-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="12547-127">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="12547-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="12547-128">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="12547-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="12547-129">Uyarı **Düzeyi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12547-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="12547-130">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A></span><span class="sxs-lookup"><span data-stu-id="12547-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12547-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="12547-131">Example</span></span>  
 <span data-ttu-id="12547-132">Derleyiciyi yalnızca seviye 1 uyarıları tazyin `in.cs` ve derleyiciye sahip</span><span class="sxs-lookup"><span data-stu-id="12547-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="12547-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12547-133">See also</span></span>

- [<span data-ttu-id="12547-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="12547-134">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="12547-135">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="12547-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
