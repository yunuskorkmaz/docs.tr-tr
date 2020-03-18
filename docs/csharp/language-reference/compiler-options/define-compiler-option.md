---
title: -define (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173750"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="46364-102">-define (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="46364-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="46364-103">**-tanımla** seçeneği, `name` programınızı tüm kaynak kodu dosyalarında bir sembol olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46364-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46364-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46364-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="46364-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="46364-105">Arguments</span></span>  
 <span data-ttu-id="46364-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="46364-106">`name`, `name2`</span></span>  
 <span data-ttu-id="46364-107">Tanımlamak istediğiniz bir veya daha fazla sembolün adı.</span><span class="sxs-lookup"><span data-stu-id="46364-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46364-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46364-108">Remarks</span></span>  
 <span data-ttu-id="46364-109">**-define** seçeneği, derleyici seçeneğinin projedeki tüm dosyalar için etkin olması dışında [#define](../preprocessor-directives/preprocessor-define.md) bir önişlemci yönergesi kullanmakla aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="46364-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="46364-110">Kaynak dosyadaki [#undef](../preprocessor-directives/preprocessor-undef.md) bir yönerge tanımı kaldırana kadar bir sembol kaynak dosyada tanımlanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="46364-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="46364-111">-define seçeneğini kullandığınızda, `#undef` bir dosyadaki bir yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="46364-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="46364-112">Kaynak dosyalarını koşullu olarak derlemek için bu seçenek tarafından oluşturulan #if [,](../preprocessor-directives/preprocessor-if.md) [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)ve [#endif](../preprocessor-directives/preprocessor-endif.md) sembolleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46364-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="46364-113">**-d** **-define**kısa şeklidir.</span><span class="sxs-lookup"><span data-stu-id="46364-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="46364-114">Sembol adlarını ayırmak için bir yarı nokta nokta veya virgül kullanarak **-define** ile birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46364-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="46364-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="46364-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="46364-116">C# derleyicisinin kendisi kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makro tanımlamaz; tüm sembol tanımları kullanıcı tanımlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46364-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46364-117">C#, `#define` C++gibi dillerde olduğu gibi bir sembole değer verilmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="46364-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="46364-118">Örneğin, `#define` makro oluşturmak veya bir sabit tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="46364-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="46364-119">Bir sabit tanımlamanız gerekiyorsa, `enum` bir değişken kullanın.</span><span class="sxs-lookup"><span data-stu-id="46364-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="46364-120">C++ tarzı bir makro oluşturmak istiyorsanız, genel olarak alternatifleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="46364-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="46364-121">Makrolar hataya açık olduğu için, C# kullanımlarına izin verir ancak daha güvenli alternatifler sunar.</span><span class="sxs-lookup"><span data-stu-id="46364-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="46364-122">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="46364-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="46364-123">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="46364-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="46364-124">**Yapı** sekmesinde, **Koşullu derleme sembolleri** kutusunda tanımlanacak simgeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="46364-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="46364-125">Örneğin, aşağıdaki kod örneğini kullanıyorsanız, metin `xx` kutusuna yazmanız gereken bir yazı nız vardır.</span><span class="sxs-lookup"><span data-stu-id="46364-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="46364-126">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A></span><span class="sxs-lookup"><span data-stu-id="46364-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46364-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="46364-127">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46364-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46364-128">See also</span></span>

- [<span data-ttu-id="46364-129">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="46364-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="46364-130">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="46364-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
