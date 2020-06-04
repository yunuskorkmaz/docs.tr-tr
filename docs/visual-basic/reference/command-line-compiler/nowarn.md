---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 37851f99eb88543e939ce48995ded41958e57cc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397494"
---
# <a name="-nowarn"></a><span data-ttu-id="ffa0f-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="ffa0f-102">-nowarn</span></span>
<span data-ttu-id="ffa0f-103">Derleyicinin uyarı oluşturma yeteneğini engeller.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa0f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ffa0f-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ffa0f-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ffa0f-105">Arguments</span></span>  
  
|<span data-ttu-id="ffa0f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ffa0f-106">Term</span></span>|<span data-ttu-id="ffa0f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ffa0f-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="ffa0f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-108">Optional.</span></span> <span data-ttu-id="ffa0f-109">Derleyicinin bastırmaları gereken uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="ffa0f-110">Uyarı kimlikleri belirtilmemişse, tüm uyarılar bastırılır.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa0f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffa0f-111">Remarks</span></span>  
 <span data-ttu-id="ffa0f-112">`-nowarn`Seçeneği derleyicinin uyarı üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="ffa0f-113">Tek bir uyarıyı gizlemek için, `-nowarn` iki nokta üst üste izleyen seçeneğe uyarı kimliğini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="ffa0f-114">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="ffa0f-115">Uyarı tanımlayıcısının yalnızca sayısal kısmını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="ffa0f-116">Örneğin, kullanılmayan yerel değişkenlerin uyarısı olan BC42024 'i gizlemek istiyorsanız, öğesini belirtin `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="ffa0f-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="ffa0f-117">Uyarı KIMLIĞI numaraları hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ffa0f-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="ffa0f-118">Visual Studio tümleşik geliştirme ortamında-nowarn 'yi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ffa0f-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ffa0f-119">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ffa0f-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ffa0f-121">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ffa0f-122">3. tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="ffa0f-123">- veya -</span><span class="sxs-lookup"><span data-stu-id="ffa0f-123">- or -</span></span><br />     <span data-ttu-id="ffa0f-124">Belirli bir uyarıyı devre dışı bırakmak için, uyarının yanındaki açılan listeden **hiçbiri** ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ffa0f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffa0f-125">Example</span></span>  
 <span data-ttu-id="ffa0f-126">Aşağıdaki kod derlenir `T2.vb` ve herhangi bir uyarı görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="ffa0f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffa0f-127">Example</span></span>  
 <span data-ttu-id="ffa0f-128">Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler için uyarıları görüntülemez (42024).</span><span class="sxs-lookup"><span data-stu-id="ffa0f-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffa0f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffa0f-129">See also</span></span>

- [<span data-ttu-id="ffa0f-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ffa0f-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ffa0f-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ffa0f-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="ffa0f-132">Visual Basic'teki Uyarıları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffa0f-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
