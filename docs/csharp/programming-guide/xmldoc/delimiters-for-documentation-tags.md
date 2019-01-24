---
title: -Belge etiketleri için sınırlayıcılar C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: ef1f6ceed49d728f6c9923204c0cb7e11aa3905a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627375"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)
XML belge açıklamaları belge açıklaması burada başlar ve biter derleyici gösteren sınırlayıcılar gerektirir. Aşağıdaki türde sınırlayıcıları ile XML belge etiketleri kullanabilirsiniz:  
  
 `///`  
 Tek satır sınırlayıcısı. Bu belge örneklerde gösterildiği ve Visual C# proje şablonlarında tarafından kullanılan biçimidir. Sınırlayıcının bir boşluk karakteri varsa, o karakteri XML çıktısında dahil edilmez.  
  
> [!NOTE]
>  Visual Studio IDE akıllı açıklama otomatik olarak ekleyen düzenlemeyi denilen bir özelliği olan \<Özet > ve \</summary > etiketleri ve yazdıktan sonra bu etiketleri içinde imlecinizi hareket `///` sınırlayıcı Kod Düzenleyicisi'nde . Bu özellik açıp kapatabilirsiniz [Seçenekler iletişim kutusu](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Çok satırlı sınırlayıcı.  
  
 Kullandığınız izlenmesi gereken bazı biçimlendirme kuralları `/** */` sınırlayıcı.  
  
-   İçeren satırda `/**` ayırıcı, boşluk, satır satır geri kalanında ise açıklamalarına işlenmedi. İlk karakterden sonra `/**` sınırlayıcı olduğu beyaz boşluk, boşluk karakteri göz ardı edilir ve satırın geri kalanını işlenir. Aksi takdirde, tüm metin satırının sonra `/**` sınırlayıcı açıklamayı bir parçası olarak işlenir.  
  
-   İçeren satırda `*/` varsa yalnızca boşluk kadar sınırlayıcı `*/` sınırlayıcı, o satırdaki göz ardı edilir. Aksi takdirde, en fazla bir satırındaki metin `*/` sınırlayıcı desen eşleştirme kuralları aşağıdaki maddede açıklandığı tabi açıklamayı bir parçası olarak işlenir.  
  
-   İle başlayan bir sonraki satırların için `/**` sınırlayıcı, derleyici her satırın başında yaygın bir düzen arar. Desen, isteğe bağlı beyaz boşluk ve yıldız oluşabilir (`*`) ve ardından daha fazla isteğe bağlı beyaz boşluk. Derleyici, ile başlamaz her satırın başında yaygın bir düzen bulursa `/**` sınırlayıcı veya `*/` sınırlayıcı, her satır için bu deseni yoksayar.  
  
 Aşağıdaki örnekler, bu kuralları gösterir.  
  
-   Yalnızca işlenecek şu açıklama ile başlayan satırı parçasıdır `<summary>`. Üç etiket biçimlerini aynı açıklamaları üretir.  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Derleyici ortak deseni tanımlayan "*" ikinci ve üçüncü satır başında. Desen çıktısında dahil edilmez.  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Üçüncü satır ikinci karakteri yıldız olmadığı için derleyici aşağıdaki açıklamada hiçbir ortak desenini bulur. Bu nedenle, tüm metin ikinci ve üçüncü satırlardaki açıklamayı bir parçası olarak işlenir.  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Derleyici, aşağıdaki açıklamada iki nedenden dolayı hiçbir desenini bulur. İlk olarak, yıldız işareti önce boşluk sayısını tutarlı değil. İkinci olarak, beşinci satır alanları eşleşmiyor bir sekme ile başlar. Bu nedenle, tüm beş aracılığıyla satırlarını iki metinden açıklamayı bir parçası olarak işlenir.  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
