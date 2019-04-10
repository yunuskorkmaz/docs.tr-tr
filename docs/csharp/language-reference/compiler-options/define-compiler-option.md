---
title: -tanımlama (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 46ceca3a84e8ffbe6d07886c1b93d062f3ccd2d1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305266"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="6f4e8-102">-tanımlama (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6f4e8-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="6f4e8-103">**-Tanımlama** seçeneği tanımlar `name` programınızı tüm kaynak kodu sembol dosyaları olarak.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f4e8-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f4e8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6f4e8-105">Arguments</span></span>  
 `name`<span data-ttu-id="6f4e8-106">,</span><span class="sxs-lookup"><span data-stu-id="6f4e8-106">,</span></span> `name2`  
 <span data-ttu-id="6f4e8-107">Tanımlamak istediğiniz bir veya daha fazla sembol adı.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f4e8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f4e8-108">Remarks</span></span>  
 <span data-ttu-id="6f4e8-109">**-Tanımlama** seçeneğini kullanmakla aynı etkiye sahip bir [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi dışında derleyici seçeneği etkin projedeki tüm dosyalar içindir.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-109">The **-define** option has the same effect as using a [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="6f4e8-110">Bir sembol kadar kaynak dosyada kalacağı bir [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) yönergesi kaynak dosyadaki tanımı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-110">A symbol remains defined in a source file until an [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="6f4e8-111">Kullandığınızda, define seçeneği, bir `#undef` yönergesi tek bir dosyada proje diğer kaynak kodu dosyaları üzerinde hiçbir etkisi.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="6f4e8-112">Bu seçenekle tarafından oluşturulan simgeleri kullanabilirsiniz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), ve [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) kaynak dosyaları koşullu olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-112">You can use symbols created by this option with [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), and [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="6f4e8-113">**-d** öğesinin kısa biçimidir **-tanımlama**.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="6f4e8-114">Birden çok sembolleriyle tanımlayabilirsiniz **-tanımlama** sembol adını ayırmak için noktalı virgül veya virgülle kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="6f4e8-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6f4e8-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="6f4e8-116">C# derleyicisi kendisine hiçbir sembol veya kaynak kodunuzda kullanabileceğiniz makroları tanımlar; Tüm sembol tanımlarını, kullanıcı tarafından tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f4e8-117">C# `#define` C++ gibi dillerde olduğu gibi bir değer verilmesi bir simge izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="6f4e8-118">Örneğin, `#define` bir makro veya bir sabit tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="6f4e8-119">Bir sabit tanımlamak ihtiyacınız varsa, bir `enum` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="6f4e8-120">C++ tarzı makro oluşturmak istiyorsanız, genel türler gibi Alternatiflere göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="6f4e8-121">Makrolar hataya yatkın olduğundan, C# kullanımları izin vermiyor ancak daha güvenli alternatifler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6f4e8-122">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6f4e8-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6f4e8-123">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6f4e8-124">Üzerinde **derleme** tanımlanması için Sembol yazın **koşullu derleme simgeleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="6f4e8-125">Örneğin, aşağıdaki kod örneği kullanıyorsanız, yalnızca tür `xx` metin kutusuna.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="6f4e8-126">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4e8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f4e8-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f4e8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f4e8-128">See also</span></span>

- [<span data-ttu-id="6f4e8-129">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6f4e8-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="6f4e8-130">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6f4e8-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
