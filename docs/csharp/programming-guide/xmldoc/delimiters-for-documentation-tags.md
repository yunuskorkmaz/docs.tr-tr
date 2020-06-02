---
title: Belge etiketleri için sınırlayıcılar-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 7e62c75fd393c4009c987830cca41e512cdb6250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287408"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="d405c-102">Belge etiketleri için sınırlayıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d405c-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="d405c-103">XML belgesi açıklamalarının kullanılması, bir belge açıklamasının başladığı ve bittiği derleyicisine işaret eden sınırlayıcıları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d405c-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="d405c-104">XML belge etiketleriyle aşağıdaki tür sınırlayıcıları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d405c-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="d405c-105">Tek satırlık sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="d405c-105">Single-line delimiter.</span></span> <span data-ttu-id="d405c-106">Bu, belge örneklerinde gösterilen ve C# proje şablonları tarafından kullanılan formdur.</span><span class="sxs-lookup"><span data-stu-id="d405c-106">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="d405c-107">Sınırlayıcıyı izleyen bir boşluk karakteri varsa, bu karakter XML çıktısına dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="d405c-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d405c-108">Visual Studio tümleşik geliştirme ortamı (IDE), ve etiketlerini otomatik olarak ekler `<summary>` `</summary>` ve kod düzenleyicisine sınırlayıcı yazdıktan sonra imlecinizi bu etiketlerin içine taşıdır `///` .</span><span class="sxs-lookup"><span data-stu-id="d405c-108">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="d405c-109">[Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)bu özelliği etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d405c-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="d405c-110">Çok satırlı sınırlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="d405c-110">Multiline delimiters.</span></span>

  <span data-ttu-id="d405c-111">Sınırlayıcıları kullandığınızda izlenecek bazı biçimlendirme kuralları vardır `/** */` :</span><span class="sxs-lookup"><span data-stu-id="d405c-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="d405c-112">Sınırlayıcısı içeren satırda `/**` , satırın geri kalanı boşluk ise, satır Yorumlar için işlenmez.</span><span class="sxs-lookup"><span data-stu-id="d405c-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="d405c-113">Sınırlayıcıdan sonraki ilk karakter boşluk `/**` ise, bu boşluk karakteri yok sayılır ve satırın geri kalanı işlenir.</span><span class="sxs-lookup"><span data-stu-id="d405c-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="d405c-114">Aksi halde, ayırıcıdan sonraki satırın metnin tamamı `/**` açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="d405c-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="d405c-115">Sınırlandırıcının bulunduğu satırda, `*/` sınırlandırıcının yalnızca beyaz alanı varsa `*/` , bu satır yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d405c-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="d405c-116">Aksi takdirde, ayırıcıya kadar olan satırdaki metin `*/` yorumun bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="d405c-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="d405c-117">Sınırlayıcı ile başlayan satırlar için `/**` , derleyici her bir satırın başlangıcında ortak bir model arar.</span><span class="sxs-lookup"><span data-stu-id="d405c-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="d405c-118">Bu kalıp, isteğe bağlı boşluk ve bir yıldız işareti ( `*` ) ve ardından daha isteğe bağlı boşluk içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d405c-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="d405c-119">Derleyici sınırlayıcı veya sınırlayıcıyla başlamayan her bir satırın başlangıcında ortak bir model bulursa `/**` `*/` , bu kalıbı her satır için yoksayar.</span><span class="sxs-lookup"><span data-stu-id="d405c-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="d405c-120">Aşağıdaki örneklerde bu kurallar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d405c-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="d405c-121">Aşağıdaki açıklamanın işlenen tek bir kısmı ile başlayan satırdır `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="d405c-121">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="d405c-122">Üç etiket biçimi aynı açıklamaları üretir.</span><span class="sxs-lookup"><span data-stu-id="d405c-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="d405c-123">Derleyici, \* ikinci ve üçüncü çizgilerin başlangıcında "" ortak bir modelini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d405c-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="d405c-124">Bu kalıp çıkışa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="d405c-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="d405c-125">Derleyici, aşağıdaki açıklamada ortak bir model bulmadığından, üçüncü satırdaki ikinci karakter bir yıldız işareti değildir.</span><span class="sxs-lookup"><span data-stu-id="d405c-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="d405c-126">Bu nedenle, ikinci ve üçüncü satırlardaki tüm metinler açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="d405c-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="d405c-127">Derleyici, aşağıdaki açıklamada iki nedenden dolayı hiçbir model bulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d405c-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="d405c-128">İlk olarak, yıldız işaretiyle önceki boşluk sayısı tutarlı değil.</span><span class="sxs-lookup"><span data-stu-id="d405c-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="d405c-129">İkincisi, beşinci satır boşluk ile eşleşmeyen bir sekme ile başlar.</span><span class="sxs-lookup"><span data-stu-id="d405c-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="d405c-130">Bu nedenle, metnin ikinci ile beş arasındaki tüm metinler, açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="d405c-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d405c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d405c-131">See also</span></span>

- [<span data-ttu-id="d405c-132">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d405c-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d405c-133">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="d405c-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="d405c-134">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d405c-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
