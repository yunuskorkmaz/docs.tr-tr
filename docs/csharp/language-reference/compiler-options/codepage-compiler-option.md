---
title: -codepage (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 04a0d3a62ebd2b3a938445995725994d72d5bd4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216931"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="fb376-102">-codepage (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fb376-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="fb376-103">Bu seçenek gerekli sayfa sistem için geçerli varsayılan kod sayfası değilse derleme sırasında kullanılacak hangi kod sayfasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb376-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb376-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb376-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb376-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fb376-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="fb376-106">Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfası kimliği.</span><span class="sxs-lookup"><span data-stu-id="fb376-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb376-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb376-107">Remarks</span></span>  
 <span data-ttu-id="fb376-108">Bilgisayarınızda varsayılan kod sayfası kullanmak için oluşturulmamış bir veya daha fazla kaynak kodu dosyaları derleme yaparsanız kullanabileceğiniz **- codepage** hangi kod sayfası kullanılması gerektiğini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="fb376-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="fb376-109">**-codepage** derlemeniz tüm kaynak kodu dosyaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fb376-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="fb376-110">Kaynak kodu dosyaları bilgisayarınızda geçerli olan kod sayfası ile oluşturulan veya kaynak kodu dosyaları UNICODE veya UTF-8 ile oluşturulmuşsa kullanılmıyor ihtiyacınız varsa **- codepage**.</span><span class="sxs-lookup"><span data-stu-id="fb376-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="fb376-111">Bkz: [desteklendiğinin](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) hangi kodu bulma hakkında bilgi için sisteminizde sayfaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fb376-111">See [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="fb376-112">Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fb376-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb376-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb376-113">See Also</span></span>  
 [<span data-ttu-id="fb376-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fb376-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="fb376-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="fb376-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
