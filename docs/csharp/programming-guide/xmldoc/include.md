---
title: <include> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 26241dab70a3b6a0cf80b374868fa759647cd8d9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588000"
---
# <a name="include-c-programming-guide"></a>\<> dahil etC# (Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a>Parametreler  
 `filename`  
 Belgeleri içeren XML dosyasının adı. Dosya adı, kaynak kodu dosyası ile ilişkili bir yol ile nitelenme yapılabilir. Tek `filename` tırnak işaretleri (' ') içine alın.  
  
 `tagpath`  
 İçindeki `filename` etiketlerin yolu, etikete `name`yol açar. Yolu tek tırnak işaretleri (' ') içine alın.  
  
 `name`  
 Yorumlarla önce gelen etiketteki ad Belirleyicisi; `name` ,`id`olur.  
  
 `id`  
 Açıklamaların önündeki etiketin KIMLIĞI. KIMLIĞI çift tırnak işareti ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 \<İçerme > etiketi, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar. Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir. Belgeler ayrı bir dosyaya yerleştirilerek, kaynak denetimini belgelere kaynak koddan ayrı olarak uygulayabilirsiniz. Bir kişinin kaynak kodu dosyası kullanıma alınmış olabilir ve başka birisinin belge dosyası kullanıma alınmış olabilir.  
  
 \<İçerme > etiketi XML XPath söz dizimini kullanır. \<İçerme > kullanımını özelleştirmenin yolları için XPath belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Bu çok dosyalı bir örnektir. > \<İçeren ilk dosya aşağıda listelenmiştir:  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 İkinci dosya olan xml_include_tag. doc, aşağıdaki belge açıklamalarını içerir:  
  
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
 Aşağıdaki komut satırı ile test ve test2 sınıflarını derlerken aşağıdaki çıktı oluşturulur: `/doc:DocFileName.xml.`Visual Studio 'da, proje Tasarımcısı ' nın Yapı bölmesinde XML belgesi açıklamaları seçeneğini belirtirsiniz. C# Derleyici \<içerme > etiketini gördüğünde, geçerli kaynak dosya yerine xml_include_tag. doc içinde belge açıklamalarını arar. Daha sonra derleyici DocFileName. xml oluşturur ve bu, son belgeleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları tarafından tüketilen dosyadır.  
  
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
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
