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
ms.openlocfilehash: 63d64acc0d0a1ed90a722db75b467bd3ce5f260e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663017"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="1f1f6-102">-bugreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f1f6-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="1f1f6-103">Hata ayıklama bilgileri daha sonra çözümlemek için bir dosya yerleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f1f6-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f1f6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f1f6-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="1f1f6-106">Hata raporunuzu içermesini istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f1f6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f1f6-107">Remarks</span></span>  
 <span data-ttu-id="1f1f6-108">**- Bugreport** seçeneği belirtir, aşağıdaki bilgileri yerleştirilmelidir `file`:</span><span class="sxs-lookup"><span data-stu-id="1f1f6-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="1f1f6-109">Derlemedeki tüm kaynak kodu dosyalarının bir kopyasını.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="1f1f6-110">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="1f1f6-111">Derleyici, çalıştırma ve işletim sistemi sürüm bilgisi.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="1f1f6-112">Başvurulan derlemeler ve modüller, SDK ve .NET Framework ile birlikte gelen derlemeleri hariç onaltılık basamak olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="1f1f6-113">Derleyici çıkışı, varsa.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="1f1f6-114">İçin istenir sorun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="1f1f6-115">Sorun ne düşündüğünüzü açıklaması, hangi için istenir düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="1f1f6-116">Bu seçeneği ile kullandıysanız **- errorreport: istemi** veya **- errorreport: gönderme**, dosyasındaki bilgiler, Microsoft Corporation'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="1f1f6-117">Tüm kaynak kodu dosyalarının bir kopyasını yerleştirileceği çünkü `file`, şüpheli kod hatası kısa olası programda yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="1f1f6-118">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="1f1f6-119">Oluşturulan dosyanın içeriğini bilgilerin yanlışlıkla açığa çıkmasına neden olabilecek kaynak kodu ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1f6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f1f6-120">See also</span></span>

- [<span data-ttu-id="1f1f6-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1f1f6-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="1f1f6-122">-errorreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f1f6-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)
- [<span data-ttu-id="1f1f6-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1f1f6-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
