---
title: "-tanımlama (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 273437a4250a393274fa20ad4c02b61dce35ed34
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-define-c-compiler-options"></a>-tanımlama (C# Derleyici Seçenekleri)
**-Tanımlamak** seçeneği tanımlar `name` programınızın tüm kaynak kodda bir simge dosyaları olarak.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Tanımlamak istediğiniz bir veya daha fazla simgeleri adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Tanımlamak** seçeneğini kullanarak aynı etkiye sahip bir [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi derleyici seçeneği projedeki tüm dosyalar için etkin olması dışında. Bir simge, kadar kaynak dosyasında tanımlanmış kalır bir [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) kaynak dosyasını yönergesinde tanımı kaldırır. Kullandığınızda define seçeneği, bir `#undef` bir dosyada yönergesi diğer kaynak kodu dosyaları projedeki hiçbir etkisi.  
  
 Bu seçenek ile tarafından oluşturulan simgeleri kullanabilirsiniz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), ve [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) koşullu kaynak dosyalarını derlemek için.  
  
 **-d** kısa biçimi olan **-tanımlamak**.  
  
 Birden çok sembolleriyle tanımlayabilirsiniz **-tanımlamak** sembol adları ayırmak için noktalı virgül veya nokta kullanarak. Örneğin:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 C# Derleyici kendisini bir simge veya kaynak kodunuzda kullanabilirsiniz makroları tanımlar; Tüm simge tanımlarının kullanıcı tanımlı olması gerekir.  
  
> [!NOTE]
>  C# `#define` C++ gibi dilleri olduğu gibi bir değer verilmesi bir simge izin vermiyor. Örneğin, `#define` makro oluşturmak veya sabit tanımlamak için kullanılamaz. Bir sabit tanımlamanız gerekiyorsa kullanın bir `enum` değişkeni. C++ tarzı makro oluşturmak istiyorsanız, genel türler gibi Alternatiflere göz önünde bulundurun. Makrolar hataya yatkın olduğundan, C# kullanımlarını izin vermez ancak daha güvenli alternatifler sunar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Üzerinde **yapı** sekmesinde, tanımlanması için simge türü **koşullu derleme simgeleri** kutusu. Örneğin, aşağıdaki kod örneği kullanıyorsanız, yalnızca yazın `xx` metin kutusuna.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
