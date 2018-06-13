---
title: '&lt;dahil&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: a681a2fcbb874d67b82c8bda73d92dd993928bbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334515"
---
# <a name="ltincludegt-c-programming-guide"></a>&lt;dahil&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>Parametreler  
 `filename`  
 Belgeleri içeren XML dosyasının adı. Dosya adı nitelenmiş bir yol olmalıdır. İçine `filename` tek tırnak işareti (' ').  
  
 `tagpath`  
 Etiketleri yolunu `filename` etikete müşteri adayları `name`. Yolun tek tırnak işaretleri içine alın (' ').  
  
 `name`  
 Ad belirticisi açıklamaları önündeki etiketinde; `name` sahip bir `id`.  
  
 `id`  
 Açıklamaları önündeki etiket kimliği. Kimliği çift tırnak işaretleri içine alın ("").  
  
## <a name="remarks"></a>Açıklamalar  
 \<Dahil > etiketi, başka bir dosya türlerini tanımlamak açıklamaları ve kaynak kodunuzu üyelerinde bakın sağlar. Bu belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek alternatiftir. Ayrı bir dosyaya belgelere koyarak, kaynak denetimi belgelere ayrı ayrı kaynak kodundan uygulayabilirsiniz. Bir kişi kullanıma kaynak kodu dosyasına sahip olabilir ve başka birinin kullanıma belge dosyası olabilir.  
  
 \<Dahil > etiketi XML XPath sözdizimini kullanır. Özelleştirme yolları XPath belgelere bakın, \<dahil > kullanın.  
  
## <a name="example"></a>Örnek  
 Bu birden çok dosya bir örnektir. Kullanan ilk dosya \<dahil >, aşağıda listelenmiştir:  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 İkinci dosya, xml_include_tag.doc, aşağıdaki belge açıklamaları içerir:  
  
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
 Aşağıdaki komut satırı Test ve Test2 sınıflarıyla derleme yaparken aşağıdaki çıkış oluşturulur: `/doc:DocFileName.xml.` Visual Studio'da, belirttiğiniz XML belge açıklamaları seçeneği Proje Tasarımcısı'nın Yapı bölmesinde. C# Derleyici gördüğünde \<dahil > etiketi, bu da arayacaktır geçerli kaynak dosyası yerine xml_include_tag.doc belge açıklamaları için. Derleyici sonra DocFileName.xml oluşturur ve bu belgeleri araçları tarafından gibi tüketilen dosyası [Sandcastle](https://github.com/EWSoftware/SHFB) son belgeleri oluşturmak için.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
