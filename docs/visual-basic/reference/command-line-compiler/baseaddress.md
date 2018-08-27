---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930448"
---
# <a name="-baseaddress"></a><span data-ttu-id="2290d-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="2290d-102">-baseaddress</span></span>
<span data-ttu-id="2290d-103">DLL oluştururken varsayılan temel adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2290d-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2290d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2290d-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="2290d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2290d-105">Arguments</span></span>  
  
|<span data-ttu-id="2290d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2290d-106">Term</span></span>|<span data-ttu-id="2290d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2290d-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="2290d-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2290d-108">Required.</span></span> <span data-ttu-id="2290d-109">DLL için temel adres.</span><span class="sxs-lookup"><span data-stu-id="2290d-109">The base address for the DLL.</span></span> <span data-ttu-id="2290d-110">Bu adres, onaltılık bir sayı olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2290d-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2290d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2290d-111">Remarks</span></span>  
 <span data-ttu-id="2290d-112">Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2290d-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="2290d-113">Bu adres alt sıra Word'de yuvarlanır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2290d-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="2290d-114">Örneğin, 0x11110001 belirtirseniz 0x11110000 için yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="2290d-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="2290d-115">Bir DLL için imzalama işlemini tamamlamak için kullanın `–R` seçeneği tanımlayıcı adlandırma aracı (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="2290d-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="2290d-116">Hedef DLL değilse, bu seçenek göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="2290d-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="2290d-117">-Baseaddress Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2290d-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="2290d-118">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="2290d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2290d-119">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2290d-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="2290d-120">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="2290d-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2290d-121">3.  **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2290d-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="2290d-122">4.  Değer değiştirme **DLL temel adresi:** kutusu.</span><span class="sxs-lookup"><span data-stu-id="2290d-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="2290d-123">**Not:** **DLL temel adresi:** kutusu, salt okunur bir DLL hedef olmadığı sürece.</span><span class="sxs-lookup"><span data-stu-id="2290d-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2290d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2290d-124">See Also</span></span>  
 [<span data-ttu-id="2290d-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2290d-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2290d-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2290d-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="2290d-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2290d-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="2290d-128">[Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="2290d-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
