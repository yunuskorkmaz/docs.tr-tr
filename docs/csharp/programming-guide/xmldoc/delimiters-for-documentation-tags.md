---
title: Belge etiketleri için sınırlayıcılar- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 064519e6d849736690f28c78e0efbc4067f9e6a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711798"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)
XML belgesi açıklamalarının kullanılması, bir belge açıklamasının başladığı ve bittiği derleyicisine işaret eden sınırlayıcıları gerektirir. XML belge etiketleriyle aşağıdaki tür sınırlayıcıları kullanabilirsiniz:  
  
 `///`  
 Tek satırlık sınırlayıcı. Bu, belge örneklerinde gösterilen ve görsel C# proje şablonları tarafından kullanılan formdur. Sınırlayıcıyı izleyen bir boşluk karakteri varsa, bu karakter XML çıktısına dahil edilmez.  
  
> [!NOTE]
> Visual Studio IDE, akıllı yorum düzenleme adlı bir özelliğe sahiptir. Bu, \<Özet > \<ve/Summary > etiketlerini otomatik olarak ekler ve kod düzenleyicisinde `///` ayırıcısını yazdıktan sonra imlecinizi bu etiketlerin içine taşımıştır. [Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)bu özelliği etkinleştirebilir veya devre dışı bırakabilirsiniz.  
  
 `/** */`  
 Çok satırlı sınırlayıcılar.  
  
 `/** */` sınırlayıcılarını kullanırken izlenecek bazı biçimlendirme kuralları vardır.  
  
- `/**` sınırlayıcısı içeren satırda, satırın geri kalanı boşluk ise, satır Yorumlar için işlenmez. `/**` sınırlayıcısından sonraki ilk karakter boşluk ise, bu boşluk karakteri yok sayılır ve satırın geri kalanı işlenir. Aksi takdirde, `/**` sınırlayıcısından sonra çizginin tüm metni açıklamanın bir parçası olarak işlenir.  
  
- `*/` sınırlayıcısı içeren satırda, `*/` sınırlayıcısına yalnızca beyaz boşluk varsa, bu satır yok sayılır. Aksi takdirde, `*/` sınırlayıcısı olan satırdaki metin, açıklama parçası olarak işlenir ve bu, aşağıdaki madde işaretinde açıklanan desenler ile eşleşen kurallara tabidir.  
  
- `/**` sınırlayıcısıyla başlayan satırlar için, derleyici her bir satırın başlangıcında ortak bir model arar. Bu kalıp, isteğe bağlı boşluk ve bir yıldız işareti (`*`) ve ardından daha isteğe bağlı boşluk içerebilir. Derleyici, `/**` sınırlayıcısı veya `*/` sınırlayıcısıyla başlamayan her satırın başlangıcında ortak bir model bulursa, her satır için bu kalıbı yoksayar.  
  
 Aşağıdaki örneklerde bu kurallar gösterilmektedir.  
  
- Aşağıdaki açıklamanın işlenecek tek bir kısmı `<summary>`ile başlayan satırdır. Üç etiket biçimi aynı açıklamaları üretir.  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- Derleyici, ikinci ve üçüncü çizgilerin başlangıcında "*" ortak bir modelini tanımlar. Bu kalıp çıkışa dahil değildir.  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
- Derleyici, aşağıdaki açıklamada ortak bir model bulmadığından, üçüncü satırdaki ikinci karakter bir yıldız işareti değildir. Bu nedenle, ikinci ve üçüncü satırlardaki tüm metinler açıklamanın bir parçası olarak işlenir.  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
- Derleyici, aşağıdaki açıklamada iki nedenden dolayı hiçbir model bulmamalıdır. İlk olarak, yıldız işaretiyle önceki boşluk sayısı tutarlı değil. İkincisi, beşinci satır boşluk ile eşleşmeyen bir sekme ile başlar. Bu nedenle, metnin ikinci ile beş arasındaki tüm metinler, açıklamanın bir parçası olarak işlenir.  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [XML Belge Açıklamaları](./index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](./index.md)
