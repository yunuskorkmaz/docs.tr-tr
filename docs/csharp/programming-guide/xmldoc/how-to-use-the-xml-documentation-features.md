---
title: "Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)
Aşağıdaki örnek belgelenmiştir bir tür temel bir bakış sağlar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **Bu .xml dosyası ile Yukarıdaki örnek kod oluşturuldu.**  
**\<? xml version = "1.0"? >**  
**\<Belge >**  
 **\<derleme >**  
 **\<adı > xmlsample \< /name >**  
 **\</Assembly >**  
 **\<üyeleri >**  
 **\<üye adı "T:SomeClass" = >**  
 **\<Özet >**  
 **Sınıf düzeyinde Özet belgelerine buraya ekleyin.  \< /Özet >**  
 **\<Açıklamalar >**  
 **Bir tür veya üye uzun açıklamaları ilişkilendirilebilir.**  
 **Açıklamalar etiketi aracılığıyla \< /remarks >**  
 **\</Member >**  
 **\<üye name="F:SomeClass.m_Name" >**  
 **\<Özet >**  
 **Name özelliği için depolama \< /Özet >**  
 **\</Member >**  
 **\<üye adı "M:SomeClass. #ctor" = >**  
 **\<Özet > sınıfı oluşturucusu.  \< /Özet >**  
 **\</Member >**  
 **\<üye name="M:SomeClass.SomeMethod(System.String)" >**  
 **\<Özet >**  
 **SomeMethod açıklaması.  \< /Özet >**  
 **\<param name = "s" > s parametresi açıklamasını buraya\</param >**  
 **\<SeeAlso cref="T:System.String" >**  
 **Bir tür veya üye başvurmak için herhangi bir etiket cref özniteliği kullanabilirsiniz**  
 **ve derleyici başvurusu var olup olmadığını denetleyin. \</seealso >**  
 **\</Member >**  
 **\<üye name="M:SomeClass.SomeOtherMethod" >**  
 **\<Özet >**  
 **Diğer bir yöntem.  \< /Özet >**  
 **\<döndürür >**  
 **Dönüş sonuçları döndürür etiketi açıklanmaktadır.  \< /verir >**  
 **\<SeeAlso cref="M:SomeClass.SomeMethod(System.String)" >**  
 **Belirli bir yöntemi başvurmak için cref özniteliği kullanımına dikkat edin \</seealso >**  
 **\</Member >**  
 **\<üye name="M:SomeClass.Main(System.String[])" >**  
 **\<Özet >**  
 **Uygulama için giriş noktası.**  
 **\</ Özet >**  
 **\<param name = "bağımsız değişken" > bir komut satırı bağımsız değişkenleri listesi\</param >**  
 **\</Member >**  
 **\<üye name="P:SomeClass.Name" >**  
 **\<Özet >**  
 **Name özelliği  \< /Özet >**  
 **\<Değer >**  
 **Bir değer etiketi özellik değeri tanımlamak için kullanılan \< /value >**  
 **\</Member >**  
 **\</Members >**  
**\</ doc >**   
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek derlemek için aşağıdaki komutu yazın:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Bu TYPE komutunu kullanarak veya tarayıcınızda görüntüleyebilirsiniz XMLsample.xml XML dosyası oluşturur.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 XML belgeleri başlatır: / / / ile. Yeni bir proje oluşturduğunuzda, sihirbazda bazı starter / / / satırları yerleştirin. Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:  
  
-   Belge doğru biçimlendirilmiş XML. Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.  
  
-   Geliştiriciler kendi etiketleri kümesi oluşturmak boş. Önerilen etiketler (daha fazla bilgi bölümüne bakın) birtakım yoktur. Önerilen etiketler bazıları özel anlamlara sahiptir:  
  
    -   \<Param > etiketi parametrelerini tanımlamak için kullanılır. Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın. Doğrulama başarısız olursa derleyici bir uyarı verir.  
  
    -   `cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir. Derleyici, bu kod öğesi var olduğunu doğrular. Doğrulama başarısız olursa derleyici bir uyarı verir. Derleyici herhangi uyar `using` açıklandığı bir tür için göründüğünde deyimleri `cref` özniteliği.  
  
    -   \<Özet > etiketi IntelliSense Visual Studio içinde bir tür veya üye hakkındaki ek bilgileri görüntülemek için kullanılır.  
  
        > [!NOTE]
        >  XML dosyası türü ve üyeleri hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgi içermiyor). Bir tür veya üye hakkında tam bilgi almak için belge dosyası gerçek tür veya üye yansıma ile birlikte kullanılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML belgeleri yorumları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
