---
description: Daha fazla bilgi edinin:-Out (Visual Basic)
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 82fb43ecf2239c38245f3afe7cacef8bad573175
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475896"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="36514-103">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36514-103">-out (Visual Basic)</span></span>

<span data-ttu-id="36514-104">Çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36514-104">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36514-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="36514-105">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="36514-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="36514-106">Arguments</span></span>  
  
|<span data-ttu-id="36514-107">Terim</span><span class="sxs-lookup"><span data-stu-id="36514-107">Term</span></span>|<span data-ttu-id="36514-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="36514-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="36514-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="36514-109">Required.</span></span> <span data-ttu-id="36514-110">Derleyicinin oluşturduğu çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="36514-110">The name of the output file the compiler creates.</span></span> <span data-ttu-id="36514-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="36514-111">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36514-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36514-112">Remarks</span></span>  

 <span data-ttu-id="36514-113">Oluşturulacak dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="36514-113">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="36514-114">Bunu yapmazsanız,. exe dosyası, yordamı içeren kaynak kodu dosyasından adını alır `Sub Main` ve. dll dosyası adı ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="36514-114">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="36514-115">Bir. exe veya. dll uzantısı olmadan bir dosya adı belirtirseniz, derleyici, derleyici seçeneği için belirtilen değere bağlı olarak uzantıyı sizin için otomatik olarak ekler `-target` .</span><span class="sxs-lookup"><span data-stu-id="36514-115">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="36514-116">Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="36514-116">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="36514-117">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36514-117">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="36514-118">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36514-118">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="36514-119">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36514-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="36514-120">3. **derleme adı** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="36514-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36514-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="36514-121">Example</span></span>  

 <span data-ttu-id="36514-122">Aşağıdaki kod derleme `T2.vb` ve çıkış dosyası oluşturur `T2.exe` .</span><span class="sxs-lookup"><span data-stu-id="36514-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="36514-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36514-123">See also</span></span>

- [<span data-ttu-id="36514-124">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="36514-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="36514-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36514-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="36514-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="36514-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
