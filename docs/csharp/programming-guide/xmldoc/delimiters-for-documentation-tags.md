---
title: Dokümantasyon etiketleri için sınır dışı layıcılar - C# programlama kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789827"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Belge etiketleri için sınır layıcılar (C# programlama kılavuzu)

XML doküman açıklamalarının kullanımı, belge leme yorumunun başladığı ve bittiği derleyiciye işaret eden sınırlayıcılar gerektirir. Aşağıdaki tür delimiterleri XML belge etiketleri ile kullanabilirsiniz:

- `///`

  Tek satırlı sınırlayıcı. Bu, dokümantasyon örneklerinde gösterilen ve Visual C# proje şablonları tarafından kullanılan formdur. Delimiter'ı izleyen bir beyaz boşluk karakteri varsa, bu karakter XML çıkışına dahil edilmez.

  > [!NOTE]
  > Visual Studio IDE, Kod Düzenleyicisi'nde \< \< `///` sınır çözücüyazdıktan sonra özet> ve/özet> etiketleri otomatik olarak ekleyen ve imlecinizi bu etiketlere sokan Smart Comment Editing adlı bir özelliğe sahiptir. Bu özelliği [Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)açabilir veya kapatabilirsiniz.
  
- `/** */`

  Çok hatlı sınırlayıcılar.

  `/** */` Sınır aşanları kullandığınızda uymanız gereken bazı biçimlendirme kuralları vardır:
  
  - `/**` Sınır dışılayıcıyı içeren satırda, satırın geri kalanı beyaz boşluksa, satır açıklamalar için işlenmez. `/**` Delimiter'dan sonraki ilk karakter beyaz boşluksa, bu beyaz boşluk karakteri yoksayılır ve satırın geri kalanı işlenir. Aksi takdirde, `/**` delimiter sonra satırın tüm metin açıklamanın bir parçası olarak işlenir.

  - `*/` Delimiter içeren satırda, `*/` delimiter kadar yalnızca beyaz boşluk varsa, bu satır yoksayılır. Aksi takdirde, satırdaki delimiter'a `*/` kadar olan metin, aşağıdaki madde işaretinde açıklanan desen eşleştirme kurallarına tabi olarak yorumun bir parçası olarak işlenir.
  
  - `/**` Delimiter ile başlayan satırlardan sonraki satırlar için derleyici, her satırın başında ortak bir desen arar. Desen isteğe bağlı beyaz alan ve yıldız`*`(), daha isteğe bağlı beyaz alan takip oluşabilir. Derleyici, her satırın başında `/**` delimiter veya `*/` delimiter ile başlamayan ortak bir desen bulursa, her satır için bu deseni yok sayar.

  Aşağıdaki örneklerde bu kurallar gösterilmektedir.

  - Aşağıdaki yorumun işlenecek tek bölümü `<summary>`ile başlayan satırdır. Üç etiket biçimi aynı yorumları üretir.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Derleyici, ikinci ve üçüncü \* satırbaşında " " ortak bir desen tanımlar. Desen çıktıya dahil edilmez.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Üçüncü satırdaki ikinci karakter bir yıldız işareti olmadığından derleyici aşağıdaki yorumda ortak bir desen bulamayın. Bu nedenle, ikinci ve üçüncü satırdaki tüm metin yorumun bir parçası olarak işlenir.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Derleyici iki nedenden dolayı aşağıdaki yorumda desen bulaçalışmaz. İlk olarak, yıldız işaretinden önceki boşluk sayısı tutarlı değildir. İkinci olarak, beşinci satır boşluklarla eşleşmeyen bir sekmeyle başlar. Bu nedenle, ikinci satırdan beşe kadar olan tüm metin, yorumun bir parçası olarak işlenir.

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [XML belgeleri yorumları](./index.md)
- [-doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
