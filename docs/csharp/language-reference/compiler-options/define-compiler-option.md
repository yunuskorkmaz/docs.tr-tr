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
# <a name="-define-c-compiler-options"></a>-define (C# Derleyici Seçenekleri)
**-tanımla** seçeneği, `name` programınızı tüm kaynak kodu dosyalarında bir sembol olarak tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `name`, `name2`  
 Tanımlamak istediğiniz bir veya daha fazla sembolün adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-define** seçeneği, derleyici seçeneğinin projedeki tüm dosyalar için etkin olması dışında [#define](../preprocessor-directives/preprocessor-define.md) bir önişlemci yönergesi kullanmakla aynı etkiye sahiptir. Kaynak dosyadaki [#undef](../preprocessor-directives/preprocessor-undef.md) bir yönerge tanımı kaldırana kadar bir sembol kaynak dosyada tanımlanmaya devam eder. -define seçeneğini kullandığınızda, `#undef` bir dosyadaki bir yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi yoktur.  
  
 Kaynak dosyalarını koşullu olarak derlemek için bu seçenek tarafından oluşturulan #if [,](../preprocessor-directives/preprocessor-if.md) [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)ve [#endif](../preprocessor-directives/preprocessor-endif.md) sembolleri kullanabilirsiniz.  
  
 **-d** **-define**kısa şeklidir.  
  
 Sembol adlarını ayırmak için bir yarı nokta nokta veya virgül kullanarak **-define** ile birden çok sembol tanımlayabilirsiniz. Örnek:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# derleyicisinin kendisi kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makro tanımlamaz; tüm sembol tanımları kullanıcı tanımlı olmalıdır.  
  
> [!NOTE]
> C#, `#define` C++gibi dillerde olduğu gibi bir sembole değer verilmesine izin vermez. Örneğin, `#define` makro oluşturmak veya bir sabit tanımlamak için kullanılamaz. Bir sabit tanımlamanız gerekiyorsa, `enum` bir değişken kullanın. C++ tarzı bir makro oluşturmak istiyorsanız, genel olarak alternatifleri göz önünde bulundurun. Makrolar hataya açık olduğu için, C# kullanımlarına izin verir ancak daha güvenli alternatifler sunar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Yapı** sekmesinde, **Koşullu derleme sembolleri** kutusunda tanımlanacak simgeyi yazın. Örneğin, aşağıdaki kod örneğini kullanıyorsanız, metin `xx` kutusuna yazmanız gereken bir yazı nız vardır.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>  
  
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

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
