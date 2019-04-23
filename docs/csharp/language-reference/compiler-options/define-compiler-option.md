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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305266"
---
# <a name="-define-c-compiler-options"></a>-tanımlama (C# Derleyici Seçenekleri)
**-Tanımlama** seçeneği tanımlar `name` programınızı tüm kaynak kodu sembol dosyaları olarak.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Tanımlamak istediğiniz bir veya daha fazla sembol adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Tanımlama** seçeneğini kullanmakla aynı etkiye sahip bir [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi dışında derleyici seçeneği etkin projedeki tüm dosyalar içindir. Bir sembol kadar kaynak dosyada kalacağı bir [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) yönergesi kaynak dosyadaki tanımı kaldırır. Kullandığınızda, define seçeneği, bir `#undef` yönergesi tek bir dosyada proje diğer kaynak kodu dosyaları üzerinde hiçbir etkisi.  
  
 Bu seçenekle tarafından oluşturulan simgeleri kullanabilirsiniz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), ve [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) kaynak dosyaları koşullu olarak derleyebilirsiniz.  
  
 **-d** öğesinin kısa biçimidir **-tanımlama**.  
  
 Birden çok sembolleriyle tanımlayabilirsiniz **-tanımlama** sembol adını ayırmak için noktalı virgül veya virgülle kullanarak. Örneğin:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# derleyicisi kendisine hiçbir sembol veya kaynak kodunuzda kullanabileceğiniz makroları tanımlar; Tüm sembol tanımlarını, kullanıcı tarafından tanımlanmış olması gerekir.  
  
> [!NOTE]
>  C# `#define` C++ gibi dillerde olduğu gibi bir değer verilmesi bir simge izin vermiyor. Örneğin, `#define` bir makro veya bir sabit tanımlamak için kullanılamaz. Bir sabit tanımlamak ihtiyacınız varsa, bir `enum` değişkeni. C++ tarzı makro oluşturmak istiyorsanız, genel türler gibi Alternatiflere göz önünde bulundurun. Makrolar hataya yatkın olduğundan, C# kullanımları izin vermiyor ancak daha güvenli alternatifler sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin açın **özellikleri** sayfası.  
  
2. Üzerinde **derleme** tanımlanması için Sembol yazın **koşullu derleme simgeleri** kutusu. Örneğin, aşağıdaki kod örneği kullanıyorsanız, yalnızca tür `xx` metin kutusuna.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Örnek  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
