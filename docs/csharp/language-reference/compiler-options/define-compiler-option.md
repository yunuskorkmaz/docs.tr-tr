---
title: -define (C# derleyici seçenekleri)
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
ms.openlocfilehash: cb9de387b319ff4b81dcd1ccc37f04d8b6b3123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924794"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="1d2b5-102">-define (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1d2b5-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="1d2b5-103">**-Define** seçeneği, programınızın `name` tüm kaynak kodu dosyalarında sembol olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d2b5-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d2b5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1d2b5-105">Arguments</span></span>  
 <span data-ttu-id="1d2b5-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="1d2b5-106">`name`, `name2`</span></span>  
 <span data-ttu-id="1d2b5-107">Tanımlamak istediğiniz bir veya daha fazla sembolün adı.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2b5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d2b5-108">Remarks</span></span>  
 <span data-ttu-id="1d2b5-109">**-Define** seçeneği, derleme seçeneğinin projedeki tüm dosyalar için geçerli olması dışında, [#define](../preprocessor-directives/preprocessor-define.md) Önişlemci yönergesinin kullanılmasıyla aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="1d2b5-110">Kaynak dosyadaki bir [#undef](../preprocessor-directives/preprocessor-undef.md) yönergesi tanımı kaldırana kadar bir sembol kaynak dosyasında tanımlı kalır.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="1d2b5-111">-Define seçeneğini kullandığınızda, bir dosyadaki bir `#undef` yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="1d2b5-112">Kaynak dosyaları koşullu olarak derlemek için bu seçenek tarafından oluşturulan sembolleri [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)ve [#endif](../preprocessor-directives/preprocessor-endif.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="1d2b5-113">**-d** , **-define**öğesinin kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="1d2b5-114">Sembol adlarını ayırmak için noktalı virgül veya virgül kullanarak, **-define** ile birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="1d2b5-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1d2b5-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="1d2b5-116">Derleyici C# , kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makroyu tanımlar; Tüm sembol tanımlarının Kullanıcı tanımlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d2b5-117">C# ,`#define` Bir simgeye, gibi dillerde bir değer verilmesini izin vermez C++.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="1d2b5-118">Örneğin, `#define` bir makro oluşturmak veya bir sabit tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="1d2b5-119">Bir sabit tanımlamanız gerekiyorsa, bir `enum` değişken kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="1d2b5-120">Bir C++ stil makrosu oluşturmak isterseniz, genel türler gibi alternatifleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="1d2b5-121">Makrolar önemli bir hataya açık olmadığından, kullanmalarına izin vermez C# , ancak daha güvenli alternatifler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1d2b5-122">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1d2b5-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1d2b5-123">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1d2b5-124">**Derleme** sekmesinde, **koşullu derleme sembolleri** kutusunda tanımlanacak simgeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="1d2b5-125">Örneğin, aşağıdaki kod örneğini kullanıyorsanız, metin kutusuna yazmanız `xx` yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="1d2b5-126">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2b5-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d2b5-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d2b5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d2b5-128">See also</span></span>

- [<span data-ttu-id="1d2b5-129">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1d2b5-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1d2b5-130">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1d2b5-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
