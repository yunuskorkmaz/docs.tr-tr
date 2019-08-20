---
title: -bugreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603074"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="ca38a-102">-bugreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ca38a-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="ca38a-103">Hata ayıklama bilgilerinin daha sonra analiz edilmek üzere bir dosyaya yerleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca38a-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca38a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca38a-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca38a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca38a-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="ca38a-106">Hata raporunuzu içermesini istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="ca38a-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca38a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca38a-107">Remarks</span></span>  
 <span data-ttu-id="ca38a-108">**-Bugreport** seçeneği aşağıdaki bilgilerin yerleştirilmesi `file`gerektiğini belirtir:</span><span class="sxs-lookup"><span data-stu-id="ca38a-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="ca38a-109">Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="ca38a-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="ca38a-110">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="ca38a-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="ca38a-111">Derleyici, çalışma zamanı ve işletim sistemi ile ilgili sürüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="ca38a-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="ca38a-112">Başvurulan derlemeler ve modüller, .NET Framework ve SDK ile birlikte gelen derlemeler hariç, onaltılık basamaklar olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ca38a-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="ca38a-113">Varsa derleyici çıkışı.</span><span class="sxs-lookup"><span data-stu-id="ca38a-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="ca38a-114">Probleme için sizden sorulacak bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="ca38a-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="ca38a-115">Sorunun düzeltilmesi hakkında bir açıklama ve sizden istenir.</span><span class="sxs-lookup"><span data-stu-id="ca38a-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="ca38a-116">Bu seçenek **-errorreport: Prompt** veya **-errorreport: Send**ile kullanılırsa, dosyadaki bilgiler Microsoft Corporation 'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ca38a-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="ca38a-117">Tüm kaynak kodu dosyalarının bir kopyası içine `file`yerleştirilecek, olası en kısa programda şüpheli kod hatasını yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca38a-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="ca38a-118">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="ca38a-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="ca38a-119">Oluşturulan dosyanın içeriğinin, yanlışlıkla bilginin açığa çıkmasına neden olabilecek kaynak kodu kullanıma sunduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ca38a-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca38a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca38a-120">See also</span></span>

- [<span data-ttu-id="ca38a-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ca38a-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ca38a-122">-errorreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ca38a-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="ca38a-123">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ca38a-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
