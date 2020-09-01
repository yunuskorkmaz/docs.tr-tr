---
description: -define (C# derleyici seçenekleri)
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
ms.openlocfilehash: 3b7a1c6e92d2c60ce289f29044774c3aa42ca84f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125884"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="33e2a-103">-define (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="33e2a-103">-define (C# Compiler Options)</span></span>
<span data-ttu-id="33e2a-104">**-Define** seçeneği, `name` programınızın tüm kaynak kodu dosyalarında sembol olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33e2a-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e2a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="33e2a-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="33e2a-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="33e2a-106">Arguments</span></span>  
 <span data-ttu-id="33e2a-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="33e2a-107">`name`, `name2`</span></span>  
 <span data-ttu-id="33e2a-108">Tanımlamak istediğiniz bir veya daha fazla sembolün adı.</span><span class="sxs-lookup"><span data-stu-id="33e2a-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33e2a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33e2a-109">Remarks</span></span>  
 <span data-ttu-id="33e2a-110">**-Define** seçeneği, derleme seçeneğinin projedeki tüm dosyalar için geçerli olması dışında, [#define](../preprocessor-directives/preprocessor-define.md) Önişlemci yönergesinin kullanılmasıyla aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="33e2a-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="33e2a-111">Kaynak dosyadaki bir [#undef](../preprocessor-directives/preprocessor-undef.md) yönergesi tanımı kaldırana kadar bir sembol kaynak dosyasında tanımlı kalır.</span><span class="sxs-lookup"><span data-stu-id="33e2a-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="33e2a-112">-Define seçeneğini kullandığınızda, `#undef` bir dosyadaki bir yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="33e2a-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="33e2a-113">Kaynak dosyaları koşullu olarak derlemek için bu seçenek tarafından oluşturulan sembolleri [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)ve [#endif](../preprocessor-directives/preprocessor-endif.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e2a-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="33e2a-114">**-d** , **-define**öğesinin kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="33e2a-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="33e2a-115">Sembol adlarını ayırmak için noktalı virgül veya virgül kullanarak, **-define** ile birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e2a-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="33e2a-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="33e2a-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="33e2a-117">C# derleyicisi, kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makroyu tanımlar; Tüm sembol tanımlarının Kullanıcı tanımlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e2a-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33e2a-118">C#, `#define` C++ gibi dillerde bir simgeye değer verilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33e2a-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="33e2a-119">Örneğin, `#define` bir makro oluşturmak veya bir sabit tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33e2a-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="33e2a-120">Bir sabit tanımlamanız gerekiyorsa, bir `enum` değişken kullanın.</span><span class="sxs-lookup"><span data-stu-id="33e2a-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="33e2a-121">C++ stili makro oluşturmak isterseniz, genel türler gibi alternatifleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="33e2a-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="33e2a-122">Makrolar dikkatle hataya açık olduğundan, C# kullanılmasına Izin vermez, ancak daha güvenli alternatifler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33e2a-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="33e2a-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="33e2a-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="33e2a-124">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="33e2a-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="33e2a-125">**Derleme** sekmesinde, **koşullu derleme sembolleri** kutusunda tanımlanacak simgeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="33e2a-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="33e2a-126">Örneğin, aşağıdaki kod örneğini kullanıyorsanız, `xx` metin kutusuna yazmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="33e2a-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="33e2a-127">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A> ..</span><span class="sxs-lookup"><span data-stu-id="33e2a-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33e2a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="33e2a-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33e2a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33e2a-129">See also</span></span>

- [<span data-ttu-id="33e2a-130">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="33e2a-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="33e2a-131">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="33e2a-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
