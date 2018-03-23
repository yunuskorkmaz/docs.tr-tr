---
title: -baseaddress
ms.date: 08/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3abe566e7a32a0b350a4f483df5c77fa4d003367
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-baseaddress"></a><span data-ttu-id="2715b-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="2715b-102">-baseaddress</span></span>
<span data-ttu-id="2715b-103">DLL oluştururken, varsayılan taban adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2715b-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2715b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2715b-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="2715b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2715b-105">Arguments</span></span>  
  
|<span data-ttu-id="2715b-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2715b-106">Term</span></span>|<span data-ttu-id="2715b-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2715b-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="2715b-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2715b-108">Required.</span></span> <span data-ttu-id="2715b-109">DLL için temel adres.</span><span class="sxs-lookup"><span data-stu-id="2715b-109">The base address for the DLL.</span></span> <span data-ttu-id="2715b-110">Bu adresi bir onaltılık sayı olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2715b-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2715b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2715b-111">Remarks</span></span>  
 <span data-ttu-id="2715b-112">Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2715b-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="2715b-113">Bu adres alt sıra Word'de yuvarlanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2715b-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="2715b-114">Örneğin, 0x11110001 belirtirseniz, 0x11110000 için yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="2715b-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="2715b-115">Bir DLL için imzalama işlemini tamamlamak için kullanmak `–R` seçeneği güçlü adlandırma aracının (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="2715b-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="2715b-116">Hedef DLL değilse, bu seçeneği göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="2715b-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="2715b-117">-Baseaddress Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2715b-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="2715b-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="2715b-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2715b-119">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2715b-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="2715b-120">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="2715b-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2715b-121">3.  **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2715b-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="2715b-122">4.  Değer değiştirme **DLL temel adresi:** kutusu.</span><span class="sxs-lookup"><span data-stu-id="2715b-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="2715b-123">**Not:** **DLL temel adresi:** kutusudur salt okunur hedef DLL değilse.</span><span class="sxs-lookup"><span data-stu-id="2715b-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2715b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2715b-124">See Also</span></span>  
 [<span data-ttu-id="2715b-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2715b-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2715b-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2715b-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="2715b-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2715b-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="2715b-128">[Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="2715b-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
