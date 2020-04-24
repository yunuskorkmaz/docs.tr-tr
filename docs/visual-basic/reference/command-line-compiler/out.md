---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352382"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="fc2f2-102">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc2f2-102">-out (Visual Basic)</span></span>
<span data-ttu-id="fc2f2-103">Çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc2f2-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc2f2-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="fc2f2-105">Arguments</span></span>  
  
|<span data-ttu-id="fc2f2-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="fc2f2-106">Term</span></span>|<span data-ttu-id="fc2f2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="fc2f2-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="fc2f2-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-108">Required.</span></span> <span data-ttu-id="fc2f2-109">Derleyicinin oluşturduğu çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="fc2f2-110">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc2f2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc2f2-111">Remarks</span></span>  
 <span data-ttu-id="fc2f2-112">Oluşturulacak dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="fc2f2-113">Bunu yapmazsanız,. exe dosyası, `Sub Main` yordamı içeren kaynak kodu dosyasından adını alır ve. dll dosyası adı ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="fc2f2-114">Bir. exe veya. dll uzantısı olmadan bir dosya adı belirtirseniz, derleyici, `-target` derleyici seçeneği için belirtilen değere bağlı olarak uzantıyı sizin için otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="fc2f2-115">Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fc2f2-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fc2f2-116">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fc2f2-117">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fc2f2-118">2. **uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="fc2f2-119">3. **derleme adı** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc2f2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc2f2-120">Example</span></span>  
 <span data-ttu-id="fc2f2-121">Aşağıdaki kod derleme `T2.vb` ve çıkış dosyası `T2.exe`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc2f2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2f2-122">See also</span></span>

- [<span data-ttu-id="fc2f2-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="fc2f2-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fc2f2-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc2f2-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="fc2f2-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="fc2f2-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
