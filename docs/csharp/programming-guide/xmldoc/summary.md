---
title: '&lt;Özet&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 5415603142afaeb5df3f6c2d270a8f895196a207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359636"
---
# <a name="ltsummarygt-c-programming-guide"></a>&lt;Özet&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `description`  
 Nesne özeti.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Özet > etiketi, bir tür veya bir tür üyesi açıklamak için kullanılmalıdır. Kullanım [ \<açıklamalar >](../../../csharp/programming-guide/xmldoc/remarks.md) türü açıklaması için ek bilgiler eklemek için. Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) belgelerine araçları gibi etkinleştirmek için [Sandcastle](https://github.com/EWSoftware/SHFB) kod öğeleri için belgeleri sayfalara iç köprüler oluşturmak için.  
  
 Metni \<Özet > etiketi IntelliSense türüyle ilgili bilgiler yalnızca kaynağı ve ayrıca nesne tarayıcı penceresinde görüntülenir.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için. Derleyicinin ürettiği dosyasını temel alarak son belgeleri oluşturmak için özel bir araç oluşturabilir, veya gibi bir araç kullanın [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 Önceki örnekte şu XML dosyası oluşturur.  
  
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
 Aşağıdaki örnekte nasıl yapılacağını gösteren bir `cref` genel bir tür referansı.  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 Önceki örnekte şu XML dosyası oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
