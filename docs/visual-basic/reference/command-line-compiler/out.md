---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098910"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="d368b-102">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d368b-102">-out (Visual Basic)</span></span>

<span data-ttu-id="d368b-103">Çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d368b-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d368b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d368b-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d368b-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d368b-105">Arguments</span></span>  
  
|<span data-ttu-id="d368b-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d368b-106">Term</span></span>|<span data-ttu-id="d368b-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d368b-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="d368b-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d368b-108">Required.</span></span> <span data-ttu-id="d368b-109">Derleyicinin oluşturduğu çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="d368b-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="d368b-110">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="d368b-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d368b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d368b-111">Remarks</span></span>  

 <span data-ttu-id="d368b-112">Oluşturulacak dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d368b-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="d368b-113">Bunu yapmazsanız,. exe dosyası, yordamı içeren kaynak kodu dosyasından adını alır `Sub Main` ve. dll dosyası adı ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="d368b-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="d368b-114">Bir. exe veya. dll uzantısı olmadan bir dosya adı belirtirseniz, derleyici, derleyici seçeneği için belirtilen değere bağlı olarak uzantıyı sizin için otomatik olarak ekler `-target` .</span><span class="sxs-lookup"><span data-stu-id="d368b-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="d368b-115">Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d368b-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d368b-116">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d368b-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d368b-117">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d368b-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d368b-118">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d368b-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d368b-119">3. **derleme adı** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d368b-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d368b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d368b-120">Example</span></span>  

 <span data-ttu-id="d368b-121">Aşağıdaki kod derleme `T2.vb` ve çıkış dosyası oluşturur `T2.exe` .</span><span class="sxs-lookup"><span data-stu-id="d368b-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="d368b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d368b-122">See also</span></span>

- [<span data-ttu-id="d368b-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d368b-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d368b-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d368b-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="d368b-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d368b-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
