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
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002393"
---
# <a name="-baseaddress"></a><span data-ttu-id="2ba78-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="2ba78-102">-baseaddress</span></span>
<span data-ttu-id="2ba78-103">DLL oluşturulurken varsayılan bir temel adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ba78-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ba78-104">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ba78-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2ba78-105">Arguments</span></span>  
  
|<span data-ttu-id="2ba78-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="2ba78-106">Term</span></span>|<span data-ttu-id="2ba78-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2ba78-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="2ba78-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2ba78-108">Required.</span></span> <span data-ttu-id="2ba78-109">DLL 'nin temel adresi.</span><span class="sxs-lookup"><span data-stu-id="2ba78-109">The base address for the DLL.</span></span> <span data-ttu-id="2ba78-110">Bu adres, onaltılık bir sayı olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ba78-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ba78-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ba78-111">Remarks</span></span>  
 <span data-ttu-id="2ba78-112">Bir DLL için varsayılan temel adres .NET Framework tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2ba78-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="2ba78-113">Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ba78-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="2ba78-114">Örneğin, 0x11110001 belirtirseniz, 0x11110000 ' a yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="2ba78-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="2ba78-115">DLL imzalama işlemini gerçekleştirmek için, tanımlayıcı adlandırma aracı (sn `–R` . exe) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ba78-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="2ba78-116">Hedef bir DLL değilse, bu seçenek yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="2ba78-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="2ba78-117">Visual Studio IDE 'de-BaseAddress ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2ba78-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="2ba78-118">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ba78-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2ba78-119">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2ba78-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="2ba78-120">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2ba78-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2ba78-121">3. **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2ba78-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="2ba78-122">4. **dll taban adresi:** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2ba78-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="2ba78-123">**Note:**      **Dll taban adresi:** kutusu, hedef dll olmadığı takdirde salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="2ba78-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ba78-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ba78-124">See also</span></span>

- [<span data-ttu-id="2ba78-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2ba78-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2ba78-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ba78-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="2ba78-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2ba78-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="2ba78-128">[Sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="2ba78-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
