---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828218"
---
# <a name="-nowarn"></a><span data-ttu-id="9d047-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="9d047-102">-nowarn</span></span>
<span data-ttu-id="9d047-103">Derleyicinin, uyarı oluşturma yeteneğini engeller.</span><span class="sxs-lookup"><span data-stu-id="9d047-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d047-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d047-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d047-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d047-105">Arguments</span></span>  
  
|<span data-ttu-id="9d047-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9d047-106">Term</span></span>|<span data-ttu-id="9d047-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9d047-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="9d047-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9d047-108">Optional.</span></span> <span data-ttu-id="9d047-109">Derleyici göndermeme uyarı kimliği numaralarını virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="9d047-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="9d047-110">Uyarı kimlikleri belirtilmezse, tüm uyarıları görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="9d047-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d047-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d047-111">Remarks</span></span>  
 <span data-ttu-id="9d047-112">`-nowarn` Seçeneği derleyici uyarıları oluşturmaya değil neden olur.</span><span class="sxs-lookup"><span data-stu-id="9d047-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="9d047-113">Tek bir uyarıyı bastırmak için uyarı kimliği sağlayın. `-nowarn` izleyen iki nokta üst üste seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d047-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="9d047-114">Birden çok uyarı numaralarını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="9d047-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="9d047-115">Uyarı tanımlayıcısının yalnızca sayısal parçası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d047-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="9d047-116">Örneğin, BC42024, kullanılmayan yerel değişkenler için uyarıyı gizlemek istiyorsanız belirtin `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="9d047-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="9d047-117">Uyarı Kimliği numaralarını hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9d047-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="9d047-118">-Nowarn Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9d047-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9d047-119">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="9d047-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9d047-120">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9d047-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9d047-121">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9d047-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9d047-122">3.  Seçin **tüm uyarıları devre dışı bırak** tüm uyarıları devre dışı bırakmak için onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9d047-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="9d047-123">- veya -</span><span class="sxs-lookup"><span data-stu-id="9d047-123">- or -</span></span><br />     <span data-ttu-id="9d047-124">Belirli bir uyarı devre dışı bırakmak için **hiçbiri** uyarı bitişik aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="9d047-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d047-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d047-125">Example</span></span>  
 <span data-ttu-id="9d047-126">Aşağıdaki kod derlenir `T2.vb` ve tüm uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="9d047-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="9d047-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d047-127">Example</span></span>  
 <span data-ttu-id="9d047-128">Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler (42024) için uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="9d047-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d047-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d047-129">See also</span></span>

- [<span data-ttu-id="9d047-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9d047-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9d047-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9d047-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="9d047-132">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9d047-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
