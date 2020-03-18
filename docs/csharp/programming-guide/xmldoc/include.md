---
title: <include> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 22d87559766c04e53141e843ee8768c8aab89a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156980"
---
# <a name="include-c-programming-guide"></a>\<> (C# programlama kılavuzu) dahil

## <a name="syntax"></a>Sözdizimi

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametreler

- `filename`

  Belgeleri içeren XML dosyasının adı. Dosya adı, kaynak kod dosyasına göre bir yol ile nitelikli olabilir. Tek `filename` tırnak işaretleri (' ') içine ala.

- `tagpath`

  Etiketlerin etiketine `filename` yol açan `name`yolu. Yolu tek tırnak işaretlerine (' ') içine ala.

- `name`

  Yorumlardan önce etikette ad belirtici; `name` bir `id`.

- `id`

Yorumlardan önce etiketin kimliği. Kimliği çift tırnak işaretlerine (" ") ekin.

## <a name="remarks"></a>Açıklamalar

Include \<> etiketi, kaynak kodunuzdaki türleri ve üyeleri açıklayan başka bir dosyadaki yorumlara başvurmanızı sağlar. Bu, belge yorumlarını doğrudan kaynak kod dosyanıza yerleştirmek için bir alternatiftir. Belgeleri ayrı bir dosyaya koyarak, kaynak denetimi kaynak kodundan ayrı olarak belgelere uygulayabilirsiniz. Bir kişi kaynak kodu dosyasının kullanıma ait olması ve başka birinin belge dosyasının kullanıma ait olması olabilir.

Include \<> etiketi XML XPath sözdizimini kullanır. Dahil> kullanımınızı \<özelleştirmenin yolları için XPath belgelerine bakın.

## <a name="example"></a>Örnek

Bu çok dosyalı bir örnektir. Aşağıdaki,> içeren \<ilk dosyadır.

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

İkinci dosya, *xml_include_tag.doc*, aşağıdaki dokümantasyon yorumlarını içerir.

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Program çıktısı

Aşağıdaki çıktı, Test ve Test2 sınıflarını aşağıdaki komut satırıyla `-doc:DocFileName.xml.` derlediğinizde oluşturulur: Visual Studio'da, Proje Tasarımcısı'nın Yapı bölmesinde XML doc yorum seçeneğini belirtirsiniz. C# derleyicisi \<include> etiketini gördüğünde, geçerli kaynak dosyası yerine xml_include_tag.doc'da belge yorumlarını arar. Derleyici daha sonra DocFileName.xml oluşturur ve bu son belgeleri üretmek için [DocFX](https://dotnet.github.io/docfx/) ve [Sandcastle](https://github.com/EWSoftware/SHFB) gibi dokümantasyon araçları tarafından tüketilen dosyadır.  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dokümantasyon Yorumları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
