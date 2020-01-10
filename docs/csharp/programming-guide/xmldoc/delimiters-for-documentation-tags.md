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
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="0a4c2-102">Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0a4c2-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="0a4c2-103">XML belgesi açıklamalarının kullanılması, bir belge açıklamasının başladığı ve bittiği derleyicisine işaret eden sınırlayıcıları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="0a4c2-104">XML belge etiketleriyle aşağıdaki tür sınırlayıcıları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0a4c2-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="0a4c2-105">Tek satırlık sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-105">Single-line delimiter.</span></span> <span data-ttu-id="0a4c2-106">Bu, belge örneklerinde gösterilen ve görsel C# proje şablonları tarafından kullanılan formdur.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="0a4c2-107">Sınırlayıcıyı izleyen bir boşluk karakteri varsa, bu karakter XML çıktısına dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a4c2-108">Visual Studio IDE, akıllı yorum düzenleme adlı bir özelliğe sahiptir. Bu, \<Özet > \<ve/Summary > etiketlerini otomatik olarak ekler ve kod düzenleyicisinde `///` ayırıcısını yazdıktan sonra imlecinizi bu etiketlerin içine taşımıştır.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="0a4c2-109">[Seçenekler iletişim kutusunda](/visualstudio/ide/reference/options-text-editor-csharp-advanced)bu özelliği etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="0a4c2-110">Çok satırlı sınırlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="0a4c2-111">`/** */` sınırlayıcılarını kullanırken izlenecek bazı biçimlendirme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
- <span data-ttu-id="0a4c2-112">`/**` sınırlayıcısı içeren satırda, satırın geri kalanı boşluk ise, satır Yorumlar için işlenmez.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="0a4c2-113">`/**` sınırlayıcısından sonraki ilk karakter boşluk ise, bu boşluk karakteri yok sayılır ve satırın geri kalanı işlenir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="0a4c2-114">Aksi takdirde, `/**` sınırlayıcısından sonra çizginin tüm metni açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
- <span data-ttu-id="0a4c2-115">`*/` sınırlayıcısı içeren satırda, `*/` sınırlayıcısına yalnızca beyaz boşluk varsa, bu satır yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="0a4c2-116">Aksi takdirde, `*/` sınırlayıcısı olan satırdaki metin, açıklama parçası olarak işlenir ve bu, aşağıdaki madde işaretinde açıklanan desenler ile eşleşen kurallara tabidir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
- <span data-ttu-id="0a4c2-117">`/**` sınırlayıcısıyla başlayan satırlar için, derleyici her bir satırın başlangıcında ortak bir model arar.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="0a4c2-118">Bu kalıp, isteğe bağlı boşluk ve bir yıldız işareti (`*`) ve ardından daha isteğe bağlı boşluk içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="0a4c2-119">Derleyici, `/**` sınırlayıcısı veya `*/` sınırlayıcısıyla başlamayan her satırın başlangıcında ortak bir model bulursa, her satır için bu kalıbı yoksayar.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="0a4c2-120">Aşağıdaki örneklerde bu kurallar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-120">The following examples illustrate these rules.</span></span>  
  
- <span data-ttu-id="0a4c2-121">Aşağıdaki açıklamanın işlenecek tek bir kısmı `<summary>`ile başlayan satırdır.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="0a4c2-122">Üç etiket biçimi aynı açıklamaları üretir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-122">The three tag formats produce the same comments.</span></span>  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- <span data-ttu-id="0a4c2-123">Derleyici, ikinci ve üçüncü çizgilerin başlangıcında "\*" ortak bir modelini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="0a4c2-124">Bu kalıp çıkışa dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-124">The pattern is not included in the output.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
- <span data-ttu-id="0a4c2-125">Derleyici, aşağıdaki açıklamada ortak bir model bulmadığından, üçüncü satırdaki ikinci karakter bir yıldız işareti değildir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="0a4c2-126">Bu nedenle, ikinci ve üçüncü satırlardaki tüm metinler açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
- <span data-ttu-id="0a4c2-127">Derleyici, aşağıdaki açıklamada iki nedenden dolayı hiçbir model bulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="0a4c2-128">İlk olarak, yıldız işaretiyle önceki boşluk sayısı tutarlı değil.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="0a4c2-129">İkincisi, beşinci satır boşluk ile eşleşmeyen bir sekme ile başlar.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="0a4c2-130">Bu nedenle, metnin ikinci ile beş arasındaki tüm metinler, açıklamanın bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0a4c2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a4c2-131">See also</span></span>

- [<span data-ttu-id="0a4c2-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a4c2-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a4c2-133">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="0a4c2-133">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="0a4c2-134">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0a4c2-134">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="0a4c2-135">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="0a4c2-135">XML Documentation Comments</span></span>](./index.md)
