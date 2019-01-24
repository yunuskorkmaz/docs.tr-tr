---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: eff367fd6cc14c655f0c623731e334054233b0a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744316"
---
# <a name="-nowarn"></a><span data-ttu-id="e9917-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="e9917-102">-nowarn</span></span>
<span data-ttu-id="e9917-103">Derleyicinin, uyarı oluşturma yeteneğini engeller.</span><span class="sxs-lookup"><span data-stu-id="e9917-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9917-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9917-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9917-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9917-105">Arguments</span></span>  
  
|<span data-ttu-id="e9917-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e9917-106">Term</span></span>|<span data-ttu-id="e9917-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e9917-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="e9917-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e9917-108">Optional.</span></span> <span data-ttu-id="e9917-109">Derleyici göndermeme uyarı kimliği numaralarını virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="e9917-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="e9917-110">Uyarı kimlikleri belirtilmezse, tüm uyarıları görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="e9917-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9917-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9917-111">Remarks</span></span>  
 <span data-ttu-id="e9917-112">`-nowarn` Seçeneği derleyici uyarıları oluşturmaya değil neden olur.</span><span class="sxs-lookup"><span data-stu-id="e9917-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="e9917-113">Tek bir uyarıyı bastırmak için uyarı kimliği sağlayın. `-nowarn` izleyen iki nokta üst üste seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e9917-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="e9917-114">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="e9917-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="e9917-115">Uyarı tanımlayıcısının yalnızca sayısal parçası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9917-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="e9917-116">Örneğin, BC42024, kullanılmayan yerel değişkenler için uyarıyı gizlemek istiyorsanız belirtin `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="e9917-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="e9917-117">Uyarı Kimliği numaralarını hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e9917-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="e9917-118">-Nowarn Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e9917-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e9917-119">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="e9917-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e9917-120">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e9917-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e9917-121">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e9917-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e9917-122">3.  Seçin **tüm uyarıları devre dışı bırak** tüm uyarıları devre dışı bırakmak için onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e9917-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="e9917-123">- veya -</span><span class="sxs-lookup"><span data-stu-id="e9917-123">- or -</span></span><br />     <span data-ttu-id="e9917-124">Belirli bir uyarı devre dışı bırakmak için **hiçbiri** uyarı bitişik aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="e9917-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9917-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9917-125">Example</span></span>  
 <span data-ttu-id="e9917-126">Aşağıdaki kod derlenir `T2.vb` ve tüm uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="e9917-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="e9917-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9917-127">Example</span></span>  
 <span data-ttu-id="e9917-128">Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler (42024) için uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="e9917-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9917-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9917-129">See also</span></span>
- [<span data-ttu-id="e9917-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e9917-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e9917-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="e9917-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e9917-132">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9917-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
