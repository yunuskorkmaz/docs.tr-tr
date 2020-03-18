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
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="6b27b-102">Belge etiketleri için sınır layıcılar (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6b27b-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="6b27b-103">XML doküman açıklamalarının kullanımı, belge leme yorumunun başladığı ve bittiği derleyiciye işaret eden sınırlayıcılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="6b27b-104">Aşağıdaki tür delimiterleri XML belge etiketleri ile kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b27b-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="6b27b-105">Tek satırlı sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="6b27b-105">Single-line delimiter.</span></span> <span data-ttu-id="6b27b-106">Bu, dokümantasyon örneklerinde gösterilen ve Visual C# proje şablonları tarafından kullanılan formdur.</span><span class="sxs-lookup"><span data-stu-id="6b27b-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="6b27b-107">Delimiter'ı izleyen bir beyaz boşluk karakteri varsa, bu karakter XML çıkışına dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="6b27b-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6b27b-108">Visual Studio IDE, Kod Düzenleyicisi'nde \< \< `///` sınır çözücüyazdıktan sonra özet> ve/özet> etiketleri otomatik olarak ekleyen ve imlecinizi bu etiketlere sokan Smart Comment Editing adlı bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="6b27b-109">Bu özelliği [Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)açabilir veya kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b27b-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="6b27b-110">Çok hatlı sınırlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="6b27b-110">Multiline delimiters.</span></span>

  <span data-ttu-id="6b27b-111">`/** */` Sınır aşanları kullandığınızda uymanız gereken bazı biçimlendirme kuralları vardır:</span><span class="sxs-lookup"><span data-stu-id="6b27b-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="6b27b-112">`/**` Sınır dışılayıcıyı içeren satırda, satırın geri kalanı beyaz boşluksa, satır açıklamalar için işlenmez.</span><span class="sxs-lookup"><span data-stu-id="6b27b-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="6b27b-113">`/**` Delimiter'dan sonraki ilk karakter beyaz boşluksa, bu beyaz boşluk karakteri yoksayılır ve satırın geri kalanı işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="6b27b-114">Aksi takdirde, `/**` delimiter sonra satırın tüm metin açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="6b27b-115">`*/` Delimiter içeren satırda, `*/` delimiter kadar yalnızca beyaz boşluk varsa, bu satır yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6b27b-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="6b27b-116">Aksi takdirde, satırdaki delimiter'a `*/` kadar olan metin, aşağıdaki madde işaretinde açıklanan desen eşleştirme kurallarına tabi olarak yorumun bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>
  
  - <span data-ttu-id="6b27b-117">`/**` Delimiter ile başlayan satırlardan sonraki satırlar için derleyici, her satırın başında ortak bir desen arar.</span><span class="sxs-lookup"><span data-stu-id="6b27b-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="6b27b-118">Desen isteğe bağlı beyaz alan ve yıldız`*`(), daha isteğe bağlı beyaz alan takip oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="6b27b-119">Derleyici, her satırın başında `/**` delimiter veya `*/` delimiter ile başlamayan ortak bir desen bulursa, her satır için bu deseni yok sayar.</span><span class="sxs-lookup"><span data-stu-id="6b27b-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="6b27b-120">Aşağıdaki örneklerde bu kurallar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="6b27b-121">Aşağıdaki yorumun işlenecek tek bölümü `<summary>`ile başlayan satırdır.</span><span class="sxs-lookup"><span data-stu-id="6b27b-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="6b27b-122">Üç etiket biçimi aynı yorumları üretir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="6b27b-123">Derleyici, ikinci ve üçüncü \* satırbaşında " " ortak bir desen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b27b-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="6b27b-124">Desen çıktıya dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="6b27b-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="6b27b-125">Üçüncü satırdaki ikinci karakter bir yıldız işareti olmadığından derleyici aşağıdaki yorumda ortak bir desen bulamayın.</span><span class="sxs-lookup"><span data-stu-id="6b27b-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="6b27b-126">Bu nedenle, ikinci ve üçüncü satırdaki tüm metin yorumun bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="6b27b-127">Derleyici iki nedenden dolayı aşağıdaki yorumda desen bulaçalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6b27b-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="6b27b-128">İlk olarak, yıldız işaretinden önceki boşluk sayısı tutarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="6b27b-129">İkinci olarak, beşinci satır boşluklarla eşleşmeyen bir sekmeyle başlar.</span><span class="sxs-lookup"><span data-stu-id="6b27b-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="6b27b-130">Bu nedenle, ikinci satırdan beşe kadar olan tüm metin, yorumun bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b27b-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b27b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b27b-131">See also</span></span>

- [<span data-ttu-id="6b27b-132">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6b27b-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6b27b-133">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="6b27b-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="6b27b-134">-doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6b27b-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
