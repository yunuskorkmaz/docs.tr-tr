---
description: Daha fazla bilgi edinin:-BaseAddress
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
ms.openlocfilehash: eaa2992c126ebb83b20cfdbef3ab995a30ee25fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468324"
---
# <a name="-baseaddress"></a><span data-ttu-id="b0935-103">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="b0935-103">-baseaddress</span></span>

<span data-ttu-id="b0935-104">DLL oluşturulurken varsayılan bir temel adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0935-104">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0935-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b0935-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0935-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b0935-106">Arguments</span></span>  
  
|<span data-ttu-id="b0935-107">Terim</span><span class="sxs-lookup"><span data-stu-id="b0935-107">Term</span></span>|<span data-ttu-id="b0935-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="b0935-108">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="b0935-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b0935-109">Required.</span></span> <span data-ttu-id="b0935-110">DLL 'nin temel adresi.</span><span class="sxs-lookup"><span data-stu-id="b0935-110">The base address for the DLL.</span></span> <span data-ttu-id="b0935-111">Bu adres, onaltılık bir sayı olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b0935-111">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0935-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0935-112">Remarks</span></span>  

 <span data-ttu-id="b0935-113">Bir DLL için varsayılan temel adres .NET Framework tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b0935-113">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="b0935-114">Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b0935-114">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="b0935-115">Örneğin, 0x11110001 belirtirseniz, 0x11110000 ' a yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="b0935-115">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="b0935-116">DLL imzalama işlemini gerçekleştirmek için, `–R` tanımlayıcı adlandırma aracının (Sn.exe) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0935-116">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="b0935-117">Hedef bir DLL değilse, bu seçenek yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b0935-117">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="b0935-118">Visual Studio IDE 'de-BaseAddress ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b0935-118">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="b0935-119">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0935-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b0935-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b0935-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="b0935-121">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b0935-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b0935-122">3. **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b0935-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="b0935-123">4. **dll taban adresi:** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b0935-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="b0935-124">**Note:**      **Dll taban adresi:** kutusu, hedef dll olmadığı takdirde salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="b0935-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0935-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0935-125">See also</span></span>

- [<span data-ttu-id="b0935-126">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b0935-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b0935-127">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0935-127">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="b0935-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b0935-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="b0935-129">[Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="b0935-129">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
