---
title: -XML dosyasını işleme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1015e5b69f7701f772bc853bba53873fd065a996
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967938"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>XML Dosyasını İşleme (C# Programlama Kılavuzu)
Derleyici, kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) Kimlik dizesi yapısını benzersiz olarak tanımlar. XML dosyasını işleme programları kimliği dizesi belgeleri uygulandığı karşılık gelen .NET Framework meta verileri/yansıma öğeyi tanımlamak için kullanabilirsiniz.  
  
 XML dosyası kodunuzu hiyerarşik bir gösterimini değil; her öğe için oluşturulan bir Kimliğine sahip bir sabit listesidir.  
  
 Kimlik dizeleri oluşturduğunda, derleyici aşağıdaki kurallar gözlemler:  
  
-   Hiçbir boşluk dizesinde ' dir.  
  
-   Kimlik dizesi ilk bölümünü izleyen iki nokta ile tek bir karakter yoluyla tanımlanmakta üye türünü tanımlar. Aşağıdaki üye türleri kullanılır:  
  
    |Karakter|Açıklama|  
    |---------------|-----------------|  
    |N|ad alanı<br /><br /> Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları cref başvuruları yapabileceğiniz desteklenen durumlarda.|  
    |T|Tür: sınıf, arabirim, yapı, enum, temsilci|  
    |F|alan|  
    |P|özellik (dizin oluşturucular veya diğer dizin oluşturulmuş özellikleri dahil)|  
    |M|(tür özel yöntemler olarak Oluşturucular, işleçler ve diğerleri dahil) yöntemi|  
    |E|olay|  
    |!|Hata dizesi<br /><br /> Dizenin geri kalanı, hata hakkında bilgi sağlar. C# derleyicisi, çözümlenemeyen bağlantılar için hata bilgisi oluşturur.|  
  
-   İkinci dize ad alanı kökünde başlangıç öğesi tam olarak nitelenmiş adını parçasıdır. Öğe, kapsayan türleri ve ad alanı adı noktalarla ayrılmış. Öğenin adını nokta varsa, karma-işaretiyle ('#')'ya değiştirilir. Öğe adını doğrudan karma işareti olduğunu kabul edilir. Örneğin, dize Oluşturucusu tam adı "System.String.#ctor" olacaktır.  
  
-   Yöntemi için bağımsız değişken varsa özellikleri ve yöntemleri, parantez içindeki bağımsız değişken listesini takip eder. Hiçbir bağımsız değişken varsa, hiçbir parantez yok. Bağımsız değişkenlerin virgülle ayrılır. Her bağımsız değişken kodlama, doğrudan bir .NET Framework imzada nasıl kodlandığını izler:  
  
    -   Temel türler. Normal türleri (ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE), türün tam adı temsil edilir.  
  
    -   İç türleri (örneğin, ELEMENT_TYPE_I4 ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. ve ELEMENT_TYPE_VOID) karşılık gelen tam tür adı tam olarak temsil edilir. Örneğin, System.Int32 veya System.TypedReference.  
  
    -   ELEMENT_TYPE_PTR olarak temsil edilir bir '\*' aşağıdaki değiştirilen türü.  
  
    -   ELEMENT_TYPE_BYREF olarak temsil edilir bir '\@' aşağıdaki değiştirilen türü.  
  
    -   ELEMENT_TYPE_PINNED olarak temsil edilir bir ' ^' aşağıdaki değiştirilen türü. C# derleyicisi, hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_CMOD_REQ olarak temsil edilir bir '&#124;' ve değiştirilen türü aşağıdaki değiştiricisi sınıfının tam adı. C# derleyicisi, hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_CMOD_OPT olarak temsil edilir bir '!' ve değiştirilen türü aşağıdaki değiştiricisi sınıfının tam adı.  
  
    -   ELEMENT_TYPE_SZARRAY "dizinin öğe türü aşağıdaki []" temsil edilir.  
  
    -   "[?]" ELEMENT_TYPE_GENERICARRAY temsil edilen aşağıdaki dizinin öğe türü. C# derleyicisi, hiçbir zaman bu oluşturur.  
  
    -   ELEMENT_TYPE_ARRAY olarak temsil edilir [*lowerbound*:`size`,*lowerbound*:`size`] Burada virgül sayısını ise boyut - 1 ve alt sınırı boyutunu ve her boyut bilinen ondalık biçimde temsil edilir. Alt sınır veya boyutu belirtilmezse, yalnızca atlanır. Belirli bir boyut için boyut ve alt sınır atlanırsa, ':' de atlanır. Örneğin, belirtilmeyen boyutları ve alt sınırı 1 ile 2 boyutlu bir dizi olan [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR olarak temsil edilir "FUNC =:`type`(*imza*)", burada `type` dönüş türü ve *imza* yöntem bağımsız değişkenleri olan. Hiçbir bağımsız değişken varsa, parantezler göz ardı edilir. C# derleyicisi, hiçbir zaman bu oluşturur.  
  
     Ayırt edici aşırı yüklenmiş yöntemler için hiçbir zaman kullanılmaz, çünkü aşağıdaki imza bileşenleri temsil edilmez:  
  
    -   Çağırma kuralı  
  
    -   Dönüş türü  
  
    -   ELEMENT_TYPE_SENTINEL  
  
-   Dönüştürme işleçleri yalnızca (op_Implicit ve op_Explicit), yöntemin dönüş değeri olarak kodlanmış bir ' ~' dönüş türü tarafından ardından yukarıda kodlanmış gibi.  
  
-   Genel türler için tür adını bir vurgulamasını belirtir ve ardından genel tür parametre sayısını belirten bir sayı tarafından izlenir. Örneğin:
  
     ``<member name="T:SampleClass`2">`` etiketi olarak tanımlanan bir tür için `public class SampleClass<T, U>`.  
  
     As numaralarını tik başında belirtilen genel türleri parametre olarak alan yöntemleri için genel tür parametreleri (örneğin \`0\`1). Her bir sayının temsil eden bir türün genel parametreleri için sıfır tabanlı bir dizi gösterimi.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnekler nasıl kimliği için bir sınıf dizeleri ve üyelerini oluşturulacak:  
  
 [!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
