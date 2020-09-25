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
ms.openlocfilehash: 74c9a23cd1b3a691063c2976a593c9b3a63ca618
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173275"
---
# <a name="-define-c-compiler-options"></a>-define (C# derleyici seçenekleri)

**-Define** seçeneği, `name` programınızın tüm kaynak kodu dosyalarında sembol olarak tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `name`, `name2`  
 Tanımlamak istediğiniz bir veya daha fazla sembolün adı.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Define** seçeneği, derleme seçeneğinin projedeki tüm dosyalar için geçerli olması dışında, [#define](../preprocessor-directives/preprocessor-define.md) Önişlemci yönergesinin kullanılmasıyla aynı etkiye sahiptir. Kaynak dosyadaki bir [#undef](../preprocessor-directives/preprocessor-undef.md) yönergesi tanımı kaldırana kadar bir sembol kaynak dosyasında tanımlı kalır. -Define seçeneğini kullandığınızda, `#undef` bir dosyadaki bir yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi olmaz.  
  
 Kaynak dosyaları koşullu olarak derlemek için bu seçenek tarafından oluşturulan sembolleri [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)ve [#endif](../preprocessor-directives/preprocessor-endif.md) kullanabilirsiniz.  
  
 **-d** , **-define**öğesinin kısa biçimidir.  
  
 Sembol adlarını ayırmak için noktalı virgül veya virgül kullanarak, **-define** ile birden çok sembol tanımlayabilirsiniz. Örneğin:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# derleyicisi, kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makroyu tanımlar; Tüm sembol tanımlarının Kullanıcı tanımlı olması gerekir.  
  
> [!NOTE]
> C#, `#define` C++ gibi dillerde bir simgeye değer verilmesini sağlar. Örneğin, `#define` bir makro oluşturmak veya bir sabit tanımlamak için kullanılamaz. Bir sabit tanımlamanız gerekiyorsa, bir `enum` değişken kullanın. C++ stili makro oluşturmak isterseniz, genel türler gibi alternatifleri göz önünde bulundurun. Makrolar dikkatle hataya açık olduğundan, C# kullanılmasına Izin vermez, ancak daha güvenli alternatifler sağlar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Derleme** sekmesinde, **koşullu derleme sembolleri** kutusunda tanımlanacak simgeyi yazın. Örneğin, aşağıdaki kod örneğini kullanıyorsanız, `xx` metin kutusuna yazmanız yeterlidir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A> ..  
  
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

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
