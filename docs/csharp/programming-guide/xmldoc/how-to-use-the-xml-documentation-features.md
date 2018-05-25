---
title: 'Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)
Aşağıdaki örnek belgelenmiştir bir tür temel bir bakış sağlar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

Örneğin, aşağıdaki içeriğe sahip bir .xml dosyası oluşturur:

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek derlemek için aşağıdaki komutu yazın:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Bu TYPE komutunu kullanarak veya tarayıcınızda görüntüleyebilirsiniz XMLsample.xml XML dosyası oluşturur.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 XML belgeleri başlatır: / / / ile. Yeni bir proje oluşturduğunuzda, sihirbazda bazı starter / / / satırları yerleştirin. Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:  
  
-   Belge doğru biçimlendirilmiş XML. Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.  
  
-   Geliştiriciler kendi etiketleri kümesi oluşturmak boş. Önerilen etiketler birtakım yoktur (bkz [etiketleri belge açıklamaları için önerilen](recommended-tags-for-documentation-comments.md)). Önerilen etiketler bazıları özel anlamlara sahiptir:  
  
    -   \<Param > etiketi parametrelerini tanımlamak için kullanılır. Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın. Doğrulama başarısız olursa derleyici bir uyarı verir.  
  
    -   `cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir. Derleyici, bu kod öğesi var olduğunu doğrular. Doğrulama başarısız olursa derleyici bir uyarı verir. Derleyici herhangi uyar `using` açıklandığı bir tür için göründüğünde deyimleri `cref` özniteliği.  
  
    -   \<Özet > etiketi IntelliSense Visual Studio içinde bir tür veya üye hakkındaki ek bilgileri görüntülemek için kullanılır.  
  
        > [!NOTE]
        >  XML dosyası türü ve üyeleri hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgi içermiyor). Bir tür veya üye hakkında tam bilgi almak için belge dosyası gerçek tür veya üye yansıma ile birlikte kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
