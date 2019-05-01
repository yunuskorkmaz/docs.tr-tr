---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: f1dcc03a67880727893e55c13d65a804586b3f56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788927"
---
# <a name="-optioninfer"></a><span data-ttu-id="0c86c-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="0c86c-102">-optioninfer</span></span>
<span data-ttu-id="0c86c-103">Değişken bildiriminde yerel tür çıkarımı kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0c86c-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c86c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c86c-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c86c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0c86c-105">Arguments</span></span>  
  
|<span data-ttu-id="0c86c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="0c86c-106">Term</span></span>|<span data-ttu-id="0c86c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0c86c-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0c86c-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0c86c-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0c86c-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0c86c-109">Optional.</span></span> <span data-ttu-id="0c86c-110">Belirtin `-optioninfer+` yerel tür çıkarımı etkinleştirmek için veya `-optioninfer-` bunu engellemek için.</span><span class="sxs-lookup"><span data-stu-id="0c86c-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="0c86c-111">`-optioninfer` Seçeneği, belirtilen değer ile aynı olup `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="0c86c-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="0c86c-112">Varsayılan değer `-optioninfer` anahtar mevcut değil aynı zamanda `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="0c86c-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="0c86c-113">Varsayılan değer nezahrnovat yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0c86c-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0c86c-114">Kullanabileceğiniz `-noconfig` seçeneği derleyicinin nezahrnovat içinde belirtilenlerden yerine iç Varsayılanları koruyun.</span><span class="sxs-lookup"><span data-stu-id="0c86c-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="0c86c-115">Bu seçenek derleyici varsayılan `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="0c86c-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c86c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c86c-116">Remarks</span></span>  
 <span data-ttu-id="0c86c-117">Kaynak kodu dosyası içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim geçersiz kılmalar `-optioninfer` komut satırı derleyicisini ayarı.</span><span class="sxs-lookup"><span data-stu-id="0c86c-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="0c86c-118">-Optioninfer Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0c86c-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="0c86c-119">Bir proje seçin **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0c86c-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="0c86c-120">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="0c86c-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="0c86c-121">Üzerinde **derleme** sekmesinde, bu değeri değiştirmek **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="0c86c-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c86c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c86c-122">Example</span></span>  
 <span data-ttu-id="0c86c-123">Aşağıdaki kod derlenir `test.vb` etkin yerel tür çıkarımı ile.</span><span class="sxs-lookup"><span data-stu-id="0c86c-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c86c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c86c-124">See also</span></span>

- [<span data-ttu-id="0c86c-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="0c86c-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0c86c-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="0c86c-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="0c86c-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0c86c-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="0c86c-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="0c86c-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="0c86c-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="0c86c-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="0c86c-130">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="0c86c-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="0c86c-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="0c86c-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="0c86c-132">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="0c86c-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="0c86c-133">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c86c-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="0c86c-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="0c86c-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="0c86c-135">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="0c86c-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
