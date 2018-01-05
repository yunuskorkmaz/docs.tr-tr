---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1ad39acdec92667fbb0848a1c64c567b504dcb67
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="baseaddress"></a><span data-ttu-id="7ee4c-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="7ee4c-102">/baseaddress</span></span>
<span data-ttu-id="7ee4c-103">DLL oluştururken, varsayılan taban adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ee4c-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ee4c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7ee4c-105">Arguments</span></span>  
  
|<span data-ttu-id="7ee4c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7ee4c-106">Term</span></span>|<span data-ttu-id="7ee4c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7ee4c-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="7ee4c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-108">Required.</span></span> <span data-ttu-id="7ee4c-109">DLL için temel adres.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-109">The base address for the DLL.</span></span> <span data-ttu-id="7ee4c-110">Bu adresi bir onaltılık sayı olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ee4c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ee4c-111">Remarks</span></span>  
 <span data-ttu-id="7ee4c-112">Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ee4c-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="7ee4c-113">Bu adres alt sıra Word'de yuvarlanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="7ee4c-114">Örneğin, 0x11110001 belirtirseniz, 0x11110000 için yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="7ee4c-115">Bir DLL için imzalama işlemini tamamlamak için kullanmak `–R` seçeneği güçlü adlandırma aracının (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="7ee4c-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="7ee4c-116">Hedef DLL değilse, bu seçeneği göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="7ee4c-117">/ BaseAddress Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7ee4c-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7ee4c-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7ee4c-119">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7ee4c-120">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7ee4c-121">3.  **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="7ee4c-122">4.  Değer değiştirme **DLL temel adresi:** kutusu.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="7ee4c-123">**Not:** **DLL temel adresi:** kutusudur salt okunur hedef DLL değilse.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ee4c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ee4c-124">See Also</span></span>  
 [<span data-ttu-id="7ee4c-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7ee4c-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7ee4c-126">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ee4c-126">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="7ee4c-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7ee4c-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="7ee4c-128">[Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="7ee4c-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
