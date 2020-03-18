---
title: <summary> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789667"
---
# <a name="summary-c-programming-guide"></a>\<özet> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<summary>description</summary>
```

## <a name="parameters"></a>Parametreler

- `description`

  Nesnenin bir özeti.

## <a name="remarks"></a>Açıklamalar

Özet \<> etiketi, bir türü veya bir tür üyesini tanımlamak için kullanılmalıdır. Tür açıklamasına ek bilgi eklemek için [ \<açıklamaları>](./remarks.md) kullanın. Kod öğeleri için dokümantasyon sayfalarına dahili köprüler oluşturmak için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi dokümantasyon araçlarını etkinleştirmek için [cref Attribute'ı](./cref-attribute.md) kullanın.

Özet> \<etiketinin metni IntelliSense'deki tür le ilgili tek bilgi kaynağıdır ve Nesne Tarayıcı Penceresinde de görüntülenir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle. Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [DocFX](https://dotnet.github.io/docfx/) veya [Sandcastle](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

Önceki örnek, aşağıdaki XML dosyasını üretir.

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, genel bir `cref` türe nasıl başvuru yapılacağını gösterir.

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

Önceki örnek, aşağıdaki XML dosyasını üretir.

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
