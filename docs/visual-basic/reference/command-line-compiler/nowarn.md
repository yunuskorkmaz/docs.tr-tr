---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005405"
---
# <a name="-nowarn"></a><span data-ttu-id="d3061-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="d3061-102">-nowarn</span></span>
<span data-ttu-id="d3061-103">Derleyicinin uyarı oluşturma yeteneğini engeller.</span><span class="sxs-lookup"><span data-stu-id="d3061-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3061-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3061-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3061-105">Arguments</span></span>  
  
|<span data-ttu-id="d3061-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d3061-106">Term</span></span>|<span data-ttu-id="d3061-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d3061-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="d3061-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3061-108">Optional.</span></span> <span data-ttu-id="d3061-109">Derleyicinin bastırmaları gereken uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="d3061-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="d3061-110">Uyarı kimlikleri belirtilmemişse, tüm uyarılar bastırılır.</span><span class="sxs-lookup"><span data-stu-id="d3061-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3061-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3061-111">Remarks</span></span>  
 <span data-ttu-id="d3061-112">@No__t-0 seçeneği derleyicinin uyarı üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d3061-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="d3061-113">Tek bir uyarıyı bastırmak için, iki nokta üst üste takip eden `-nowarn` seçeneğine uyarı KIMLIĞINI sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d3061-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="d3061-114">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="d3061-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="d3061-115">Uyarı tanımlayıcısının yalnızca sayısal kısmını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3061-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="d3061-116">Örneğin, kullanılmayan yerel değişkenlerin uyarısı olan BC42024 ' ı bastırmak istiyorsanız `-nowarn:42024` belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3061-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="d3061-117">Uyarı KIMLIĞI numaraları hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d3061-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="d3061-118">Visual Studio tümleşik geliştirme ortamında-nowarn 'yi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d3061-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d3061-119">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3061-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d3061-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3061-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d3061-121">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3061-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d3061-122">3. tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d3061-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="d3061-123">veya</span><span class="sxs-lookup"><span data-stu-id="d3061-123">- or -</span></span><br />     <span data-ttu-id="d3061-124">Belirli bir uyarıyı devre dışı bırakmak için, uyarının yanındaki açılan listeden **hiçbiri** ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d3061-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d3061-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3061-125">Example</span></span>  
 <span data-ttu-id="d3061-126">Aşağıdaki kod `T2.vb` derler ve herhangi bir uyarı görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="d3061-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d3061-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3061-127">Example</span></span>  
 <span data-ttu-id="d3061-128">Aşağıdaki kod `T2.vb` derler ve kullanılmayan yerel değişkenler için uyarıları görüntülemez (42024).</span><span class="sxs-lookup"><span data-stu-id="d3061-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3061-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3061-129">See also</span></span>

- [<span data-ttu-id="d3061-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d3061-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d3061-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d3061-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d3061-132">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d3061-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
