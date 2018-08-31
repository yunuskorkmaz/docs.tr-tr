---
title: -bugreport (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 6e4674acd2a5edbbffd2babf130d2078019ab9b7
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331741"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="321b8-102">-bugreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="321b8-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="321b8-103">Hata ayıklama bilgileri daha sonra çözümlemek için bir dosya yerleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="321b8-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="321b8-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="321b8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="321b8-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="321b8-106">Hata raporunuzu içermesini istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="321b8-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321b8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="321b8-107">Remarks</span></span>  
 <span data-ttu-id="321b8-108">**- Bugreport** seçeneği belirtir, aşağıdaki bilgileri yerleştirilmelidir `file`:</span><span class="sxs-lookup"><span data-stu-id="321b8-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="321b8-109">Derlemedeki tüm kaynak kodu dosyalarının bir kopyasını.</span><span class="sxs-lookup"><span data-stu-id="321b8-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="321b8-110">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="321b8-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="321b8-111">Derleyici, çalıştırma ve işletim sistemi sürüm bilgisi.</span><span class="sxs-lookup"><span data-stu-id="321b8-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="321b8-112">Başvurulan derlemeler ve modüller, SDK ve .NET Framework ile birlikte gelen derlemeleri hariç onaltılık basamak olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="321b8-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="321b8-113">Derleyici çıkışı, varsa.</span><span class="sxs-lookup"><span data-stu-id="321b8-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="321b8-114">İçin istenir sorun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="321b8-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="321b8-115">Sorun ne düşündüğünüzü açıklaması, hangi için istenir düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="321b8-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="321b8-116">Bu seçeneği ile kullandıysanız **- errorreport: istemi** veya **- errorreport: gönderme**, dosyasındaki bilgiler, Microsoft Corporation'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="321b8-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="321b8-117">Tüm kaynak kodu dosyalarının bir kopyasını yerleştirileceği çünkü `file`, şüpheli kod hatası kısa olası programda yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="321b8-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="321b8-118">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="321b8-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="321b8-119">Oluşturulan dosyanın içeriğini bilgilerin yanlışlıkla açığa çıkmasına neden olabilecek kaynak kodu ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="321b8-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321b8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="321b8-120">See Also</span></span>  

- [<span data-ttu-id="321b8-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="321b8-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="321b8-122">-errorreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="321b8-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
- [<span data-ttu-id="321b8-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="321b8-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
