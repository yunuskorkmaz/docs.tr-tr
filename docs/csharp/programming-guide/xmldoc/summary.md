---
title: <summary> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 12898d5cd10d9ecca4ec0fd1f7d06be0761b57b8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978559"
---
# <a name="summary-c-programming-guide"></a>\<Özet > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `description`  
 Nesne bir özeti.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Özet > etiketi, bir tür veya tür üye tanımlamak için kullanılmalıdır. Kullanım [ \<remarks >](../../../csharp/programming-guide/xmldoc/remarks.md) ek bilgiler bir tür tanımı eklemek için. Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) belgeleri araçları gibi etkinleştirmek üzere [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) iç kod öğeleri için belge sayfalarına köprüler oluşturmak için.  
  
 Metni \<Özet > etiketi yalnızca kaynak ıntellisense'te tür hakkında bilgilerin ve bir nesne tarayıcı penceresinde de görüntülenir.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için. Son belgeleri derleyici tarafından üretilen dosyaya dayalı oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 Önceki örnekte, aşağıdaki XML dosyası oluşturur.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl yapılacağını gösteren bir `cref` genel bir tür referansı.  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 Önceki örnekte, aşağıdaki XML dosyası oluşturur.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
