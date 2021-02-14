---
description: :-Nowarn hakkında daha fazla bilgi edinin
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 4fb7d39aef48ff1443c342367f9e20bb37f9c5e0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434868"
---
# <a name="-nowarn"></a><span data-ttu-id="4fc24-103">-nowarn</span><span class="sxs-lookup"><span data-stu-id="4fc24-103">-nowarn</span></span>

<span data-ttu-id="4fc24-104">Derleyicinin uyarı oluşturma yeteneğini engeller.</span><span class="sxs-lookup"><span data-stu-id="4fc24-104">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc24-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4fc24-105">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4fc24-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4fc24-106">Arguments</span></span>  
  
|<span data-ttu-id="4fc24-107">Terim</span><span class="sxs-lookup"><span data-stu-id="4fc24-107">Term</span></span>|<span data-ttu-id="4fc24-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="4fc24-108">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="4fc24-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4fc24-109">Optional.</span></span> <span data-ttu-id="4fc24-110">Derleyicinin bastırmaları gereken uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="4fc24-110">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="4fc24-111">Uyarı kimlikleri belirtilmemişse, tüm uyarılar bastırılır.</span><span class="sxs-lookup"><span data-stu-id="4fc24-111">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fc24-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fc24-112">Remarks</span></span>  

 <span data-ttu-id="4fc24-113">`-nowarn`Seçeneği derleyicinin uyarı üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="4fc24-113">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="4fc24-114">Tek bir uyarıyı gizlemek için, `-nowarn` iki nokta üst üste izleyen seçeneğe uyarı kimliğini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="4fc24-114">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="4fc24-115">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="4fc24-115">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="4fc24-116">Uyarı tanımlayıcısının yalnızca sayısal kısmını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fc24-116">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="4fc24-117">Örneğin, kullanılmayan yerel değişkenlerin uyarısı olan BC42024 'i gizlemek istiyorsanız, öğesini belirtin `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="4fc24-117">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="4fc24-118">Uyarı KIMLIĞI numaraları hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4fc24-118">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="4fc24-119">Visual Studio tümleşik geliştirme ortamında-nowarn 'yi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4fc24-119">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4fc24-120">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4fc24-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4fc24-121">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4fc24-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="4fc24-122">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4fc24-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4fc24-123">3. tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="4fc24-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="4fc24-124">- veya -</span><span class="sxs-lookup"><span data-stu-id="4fc24-124">- or -</span></span><br />     <span data-ttu-id="4fc24-125">Belirli bir uyarıyı devre dışı bırakmak için, uyarının yanındaki açılan listeden **hiçbiri** ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4fc24-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4fc24-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fc24-126">Example</span></span>  

 <span data-ttu-id="4fc24-127">Aşağıdaki kod derlenir `T2.vb` ve herhangi bir uyarı görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="4fc24-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="4fc24-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fc24-128">Example</span></span>  

 <span data-ttu-id="4fc24-129">Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler için uyarıları görüntülemez (42024).</span><span class="sxs-lookup"><span data-stu-id="4fc24-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fc24-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fc24-130">See also</span></span>

- [<span data-ttu-id="4fc24-131">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4fc24-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4fc24-132">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4fc24-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4fc24-133">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4fc24-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
