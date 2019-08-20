---
title: Belge etiketleri için sınırlayıcılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 88ad2519382c06aec2c8b1488c380fac47d5f1a2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588136"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)
XML belgesi açıklamalarının kullanılması, bir belge açıklamasının başladığı ve bittiği derleyicisine işaret eden sınırlayıcıları gerektirir. XML belge etiketleriyle aşağıdaki tür sınırlayıcıları kullanabilirsiniz:  
  
 `///`  
 Tek satırlık sınırlayıcı. Bu, belge örneklerinde gösterilen ve görsel C# proje şablonları tarafından kullanılan formdur. Sınırlayıcıyı izleyen bir boşluk karakteri varsa, bu karakter XML çıktısına dahil edilmez.  
  
> [!NOTE]
>  Visual Studio IDE, \<Özet > ve \</Summary > etiketlerini otomatik olarak ekleyen akıllı yorum düzenleme adlı bir özelliğe sahiptir ve kod düzenleyicisine `///` sınırlayıcı yazdıktan sonra imlecinizi bu etiketlerin içine taşımıştır . [Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)bu özelliği etkinleştirebilir veya devre dışı bırakabilirsiniz.  
  
 `/** */`  
 Çok satırlı sınırlayıcılar.  
  
 `/** */` Sınırlandırıcıları kullandığınızda izlenecek bazı biçimlendirme kuralları vardır.  
  
- `/**` Sınırlayıcısı içeren satırda, satırın geri kalanı boşluk ise, satır Yorumlar için işlenmez. `/**` Sınırlayıcıdan sonraki ilk karakter boşluk ise, bu boşluk karakteri yok sayılır ve satırın geri kalanı işlenir. Aksi halde, `/**` ayırıcıdan sonraki satırın metnin tamamı açıklamanın bir parçası olarak işlenir.  
  
- Sınırlandırıcının bulunduğu `*/` satırda, `*/` sınırlandırıcının yalnızca beyaz alanı varsa, bu satır yok sayılır. Aksi takdirde, `*/` ayırıcıya kadar olan satırdaki metin, açıklamanın bir parçası olarak işlenir ve bu, aşağıdaki madde işaretinde açıklanan desenler ile eşleşen kurallara tabidir.  
  
- `/**` Sınırlayıcı ile başlayan satırlar için, derleyici her bir satırın başlangıcında ortak bir model arar. Bu kalıp, isteğe bağlı boşluk ve bir yıldız işareti (`*`) ve ardından daha isteğe bağlı boşluk içerebilir. Derleyici `/**` sınırlayıcı`*/` veya sınırlayıcıyla başlamayan her bir satırın başlangıcında ortak bir model bulursa, bu kalıbı her satır için yoksayar.  
  
 Aşağıdaki örneklerde bu kurallar gösterilmektedir.  
  
- Aşağıdaki açıklamanın işlenecek tek bir bölümü, ile `<summary>`başlayan satırdır. Üç etiket biçimi aynı açıklamaları üretir.  
  
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
- [/Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](./index.md)
