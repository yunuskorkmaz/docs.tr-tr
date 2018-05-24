---
title: XML Dosyasını İşleme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 659562864ad323162f15351aa960c2a54164c77d
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="processing-the-xml-file-c-programming-guide"></a>XML Dosyasını İşleme (C# Programlama Kılavuzu)
Derleyici kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur. (Kodunuzu etiketi hakkında daha fazla bilgi için bkz: [belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) Kimlik dizesi, yapı benzersiz olarak tanımlar. XML dosyasını işleme programları kimlik dizesi belgelere uygulandığı karşılık gelen .NET Framework meta verileri/yansıma öğe tanımlamak için kullanabilirsiniz.  
  
 XML dosyası kodunuzu hiyerarşik bir gösterimini değil; her öğe için oluşturulan bir kimliği var düz bir listesidir.  
  
 Kimlik dizeleri oluşturduğunda derleyici aşağıdaki kurallara uyan:  
  
-   Hiçbir boşluk dizesi içinde ' dir.  
  
-   Kimlik dizesi ilk bölümü, izleyen iki nokta ile tek bir karakter yapmamanız tanımlanmasını üye türünü tanımlar. Aşağıdaki üye türleri kullanılır:  
  
    |Karakter|Açıklama|  
    |---------------|-----------------|  
    |N|ad alanı<br /><br /> Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları cref başvurular yapabilirsiniz desteklendiği yerlerde.|  
    |T|Tür: sınıf, arabirim, yapı, enum, temsilci|  
    |F|alan|  
    |P|özellik (dizin oluşturucular veya diğer Dizinli Özellikler dahil)|  
    |M|(Bu tür özel yöntemleri Oluşturucular, işleçler ve diğerleri dahil) yöntemi|  
    |E|olay|  
    |!|Hata dizesi<br /><br /> Dizenin geri kalanı hata hakkında bilgi sağlar. C# Derleyici çözümlenemiyor bağlantılar için hata bilgilerini oluşturur.|  
  
-   İkinci dize ad alanı kökünde başlayan öğesi, tam adını parçasıdır. Öğe, kapsayan türlerini ve ad alanı adını noktalarla ayrılmış. Öğesinin adı nokta varsa, karma-işareti ('#') yerini alır. Öğe adını doğrudan karma oturum olduğunu varsayılır. Örneğin, dize Oluşturucusu tam adı "System.String.#ctor" olur.  
  
-   Yöntemi için bağımsız değişkeni varsa özellikleri ve yöntemleri için ayraç içinde bağımsız değişken listesi aşağıdadır. Bağımsız değişkenler varsa, hiçbir parantez yok. Bağımsız değişkenler virgülle ayrılır. Her bağımsız değişkeni kodlama doğrudan bir .NET Framework imzada nasıl kodlanmış aşağıdaki gibidir:  
  
    -   Taban türleri. Normal türleri (ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE) türünün tam adını temsil edilir.  
  
    -   İç türleri (örneğin, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF dizisi. ve ELEMENT_TYPE_VOID) karşılık gelen tam tür tam adı olarak temsil edilir. Örneğin, System.Int32 veya System.TypedReference.  
  
    -   ELEMENT_TYPE_PTR olarak temsil edilir bir '\*' değiştirilmiş türü aşağıdaki.  
  
    -   ELEMENT_TYPE_BYREF olarak temsil edilir bir '\@' değiştirilmiş türü aşağıdaki.  
  
    -   ELEMENT_TYPE_PINNED olarak temsil edilir bir ' ^' değiştirilmiş türü aşağıdaki. C# Derleyici hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_CMOD_REQ olarak temsil edilir bir '&#124;' ve değiştirilen türü aşağıdaki değiştiricisi sınıfın tam adı. C# Derleyici hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_CMOD_OPT olarak temsil edilir bir '!' ve değiştirilen türü aşağıdaki değiştiricisi sınıfın tam adı.  
  
    -   ELEMENT_TYPE_SZARRAY "dizi öğesi türü aşağıdaki []" gösterilir.  
  
    -   ELEMENT_TYPE_GENERICARRAY "[?]" temsil edilir dizi öğesi türü aşağıdaki. C# Derleyici hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_ARRAY olarak temsil edilir [*lowerbound*:`size`,*lowerbound*:`size`] Burada virgül sayısı ise derecesini - 1 ve alt sınırlarını ve her boyut boyutu bilinen ondalık olarak temsil edilir. Alt sınır veya boyutu belirtilmezse, yalnızca atlanır. Belirli bir boyut için boyut ve alt sınır atlanırsa, ':' de atlanır. Örneğin, 1 belirtilmeyen boyutları ve alt sınırlarını olarak 2 boyutlu bir dizi olduğundan [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR olarak temsil edilir "FUNC =:`type`(*imza*)", burada `type` dönüş türü ve *imza* olan yöntemi değişkendir. Bağımsız değişkenler varsa, parantez göz ardı edilir. C# Derleyici hiçbir zaman bu oluşturur.  
  
     Hiçbir zaman farklılaştırıcı aşırı yüklenmiş yöntemler için kullanılan çünkü aşağıdaki imza bileşenleri temsil edilmez:  
  
    -   Çağırma kuralı  
  
    -   Dönüş türü  
  
    -   ELEMENT_TYPE_SENTINEL  
  
-   Dönüştürme işleçleri yalnızca (op_Implicit ve op_Explicit), yönteminin dönüş değeri olarak kodlanmış bir ' ~' dönüş türü, yukarıda kodlanmış olarak izlemelidir.  
  
-   Genel türler için türünün adı bir backtick ve ardından genel tür parametre sayısını belirten bir sayı tarafından izlenir. Örneğin:
  
     ``<member name="T:SampleClass`2">`` etiket olarak tanımlanan bir tür için `public class SampleClass<T, U>`.  
  
     Backticks ile başlayan sayılar olarak belirtilen parametre olarak genel türler alma yöntemlerinin için genel tür parametreleri (örneğin \`0,\`1). Genel tür parametreleri için sıfır tabanlı bir dizi gösterimi gösteren her bir sayı.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnekler nasıl kimliği için bir sınıf dizeleri ve üyeleri oluşturulur:  
  
 [!code-csharp[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/processing-the-xml-file_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
