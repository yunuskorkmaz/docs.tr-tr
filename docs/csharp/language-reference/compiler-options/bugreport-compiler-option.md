---
title: "-bugreport (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2a6c27454cc8f95b9662d6ae688471849c5cee0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="8ba3d-102">-bugreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8ba3d-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="8ba3d-103">Hata ayıklama bilgileri daha sonra çözümlemek için bir dosya yerleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ba3d-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ba3d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8ba3d-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="8ba3d-106">Hata raporu içeren istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ba3d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ba3d-107">Remarks</span></span>  
 <span data-ttu-id="8ba3d-108">**- Bugreport** seçeneği belirtir, aşağıdaki bilgileri yerleştirilmelidir `file`:</span><span class="sxs-lookup"><span data-stu-id="8ba3d-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="8ba3d-109">Derlemedeki tüm kaynak kodu dosyaları bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="8ba3d-110">Derlemede kullanılan derleyici seçeneklerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="8ba3d-111">Derleyici, çalıştırma ve işletim sistemi hakkında sürüm bilgisi.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="8ba3d-112">Başvurulan derlemeler ve modüller, .NET Framework ve SDK ile birlikte gönderilen derlemeler dışında onaltılık basamak olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="8ba3d-113">Derleyici çıkışı, varsa.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="8ba3d-114">İçin istenir sorunun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="8ba3d-115">Sorunu nasıl düşündüğünüz bir açıklama için istenir sabit.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="8ba3d-116">Bu seçenek ile kullanıldığında **- errorreport: istemi** veya **- errorreport: gönderme**, Microsoft Corporation'a dosyasındaki bilgiler gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="8ba3d-117">Tüm kaynak kodu dosyaları bir kopyasını yerleştirilecek çünkü `file`, kısa olası programı şüpheli kod hatası yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="8ba3d-118">Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="8ba3d-119">Oluşturulan dosyanın içeriğini bilgilerin yanlışlıkla açığa çıkmasına neden kaynak kodu kullanıma dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba3d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ba3d-120">See Also</span></span>  
 [<span data-ttu-id="8ba3d-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8ba3d-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="8ba3d-122">-errorreport (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8ba3d-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [<span data-ttu-id="8ba3d-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="8ba3d-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
