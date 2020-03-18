---
title: -hata raporu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603074"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="007b4-102">-hata raporu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="007b4-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="007b4-103">Hata ayıklama bilgilerinin daha sonraki çözümleme için bir dosyaya konulması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="007b4-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="007b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="007b4-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="007b4-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="007b4-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="007b4-106">Hata raporunuzu içermek istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="007b4-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="007b4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="007b4-107">Remarks</span></span>  
 <span data-ttu-id="007b4-108">**-hata raporu** seçeneği, aşağıdaki bilgilerin yerleştirilmesini `file`belirtir:</span><span class="sxs-lookup"><span data-stu-id="007b4-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="007b4-109">Derlemedeki tüm kaynak kod dosyalarının bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="007b4-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="007b4-110">Derlemede kullanılan derleyici seçeneklerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="007b4-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="007b4-111">Derleyiciniz, çalışma süreniz ve işletim sisteminiz hakkındaki sürüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="007b4-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="007b4-112">.NET Framework ve SDK ile birlikte sevk edilen derlemeler hariç, hexadecimal basamak olarak kaydedilen başvurulan derlemeler ve modüller.</span><span class="sxs-lookup"><span data-stu-id="007b4-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="007b4-113">Varsa derleyici çıktısı.</span><span class="sxs-lookup"><span data-stu-id="007b4-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="007b4-114">Sizden istenecek sorunun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="007b4-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="007b4-115">Sorunun nasıl çözülmesi gerektiğini düşündüğünüze ve sizden isteneceğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="007b4-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="007b4-116">Bu seçenek **-errorreport:prompt** veya **-errorreport:send**ile kullanılırsa, dosyadaki bilgiler Microsoft Corporation'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="007b4-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="007b4-117">Tüm kaynak kodu dosyalarının bir kopyası `file`yerleştirilecektir çünkü, şüpheli kod kusurunu mümkün olan en kısa programda çoğaltmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007b4-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="007b4-118">Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="007b4-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="007b4-119">Oluşturulan dosyanın içeriğinin, yanlışlıkla bilgi ifşası ile sonuçlabilen kaynak kodu ortaya çıkardığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="007b4-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007b4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="007b4-120">See also</span></span>

- [<span data-ttu-id="007b4-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="007b4-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="007b4-122">-hata raporu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="007b4-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="007b4-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="007b4-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
