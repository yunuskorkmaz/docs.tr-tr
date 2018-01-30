---
title: "Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c72ee03ff8a2e28bec1ba83e42cd7f201b140ed
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2018
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)
XML belge açıklamaları kullanılmasını burada belgelerine yorum başlar ve biter derleyici belirtmek sınırlayıcıları gerektirir. XML belgeleri etiketlerle sınırlayıcıları şu tür kullanabilirsiniz:  
  
 `///`  
 Tek satırlı sınırlayıcısı. Bu belge örneklerde gösterilen ve Visual C# proje şablonları tarafından kullanılan formdur. Sınırlayıcı izleyen bir boşluk karakteri varsa, bu karakterin XML çıktısında dahil edilmez.  
  
> [!NOTE]
>  Visual Studio IDE akıllı açıklama otomatik olarak ekleyen düzenleme adlı bir özelliği olan \<Özet > ve \</Özet > etiketleri ve yazdıktan sonra imleci bu etiketlerde taşır `///` sınırlayıcı Kod Düzenleyicisi'nde . Bu özellik üzerinde veya kapatabilirsiniz [Seçenekler iletişim kutusu](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Çok satırlı sınırlayıcısı.  
  
 Kullandığınızda izlemek için biçimlendirme bazı kurallar vardır `/** */` sınırlayıcısı.  
  
-   İçeren satırı üzerinde `/**` kalan satırının satır boşluk ise sınırlayıcı açıklamaları için işlenmedi. Varsa sonra ilk karakter `/**` sınırlayıcısı olan beyaz boşluk karakteri göz ardı edilir ve satır kalan işlenen alan. Aksi takdirde satırından sonra tüm metnin `/**` sınırlayıcı yorum bir parçası olarak işlenir.  
  
-   İçeren satırı üzerinde `*/` varsa yalnızca boşluk kadar sınırlayıcı `*/` sınırlayıcısı, o satırdaki göz ardı edilir. Aksi takdirde kadar satırındaki metin `*/` sınırlayıcı aşağıdaki maddede açıklandığı desen eşleştirme kuralları tabi yorum bir parçası olarak işlenir.  
  
-   İle başlayan bir sonraki satırların için `/**` sınırlayıcısı, derleyicinin her satırın başındaki genel bir desen arar. Desen isteğe bağlı boşluk ve bir yıldız işareti içerebilir (`*`), ardından daha fazla isteğe bağlı boşluk. Derleyici ile başlamayan her satırın başındaki ortak bir deseni bulursa `/**` sınırlayıcı veya `*/` sınırlayıcısı, her satır için bu deseni yok sayar.  
  
 Aşağıdaki örnekler, bu kuralları gösterir.  
  
-   Yalnızca nasıl işleneceğini aşağıdaki açıklama ile başlayan satırı parçasıdır `<summary>`. Üç etiket biçimlerini aynı açıklamaları üretir.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Derleyici, genel bir desen tanımlar "*" ikinci ve üçüncü satır başında. Desen çıktıda dahil edilmez.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Üçüncü satır ikinci karakteri bir yıldız işareti olmadığından derleyici hiçbir ortak desen aşağıdaki açıklamada bulur. Bu nedenle, ikinci ve üçüncü satırlarındaki tüm metni yorum bir parçası olarak işlenir.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Derleyici hiçbir desen aşağıdaki açıklamada iki nedenden dolayı bulur. İlk olarak, yıldız işareti önce boşluk sayısını tutarlı değil. İkinci olarak, beşinci satır alanları eşleşmiyor bir sekme ile başlar. Bu nedenle, tüm metinden satırları iki beş aracılığıyla açıklama bir parçası olarak işlenir.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
