---
title: Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 06bd997e6862bc1f86ad2e3b2afbbb5afac78d9c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064296"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="f9c1d-102">Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f9c1d-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="f9c1d-103">XML belge açıklamaları belge açıklaması burada başlar ve biter derleyici gösteren sınırlayıcılar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="f9c1d-104">Aşağıdaki türde sınırlayıcıları ile XML belge etiketleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9c1d-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="f9c1d-105">Tek satır sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-105">Single-line delimiter.</span></span> <span data-ttu-id="f9c1d-106">Bu belge örneklerde gösterildiği ve Visual C# proje şablonlarında tarafından kullanılan biçimidir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="f9c1d-107">Sınırlayıcının bir boşluk karakteri varsa, o karakteri XML çıktısında dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9c1d-108">Visual Studio IDE akıllı açıklama otomatik olarak ekleyen düzenlemeyi denilen bir özelliği olan \<Özet > ve \</summary > etiketleri ve yazdıktan sonra bu etiketleri içinde imlecinizi hareket `///` sınırlayıcı Kod Düzenleyicisi'nde .</span><span class="sxs-lookup"><span data-stu-id="f9c1d-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="f9c1d-109">Bu özellik açıp kapatabilirsiniz [Seçenekler iletişim kutusu](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="f9c1d-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="f9c1d-110">Çok satırlı sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="f9c1d-111">Kullandığınız izlenmesi gereken bazı biçimlendirme kuralları `/** */` sınırlayıcı.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="f9c1d-112">İçeren satırda `/**` ayırıcı, boşluk, satır satır geri kalanında ise açıklamalarına işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="f9c1d-113">İlk karakterden sonra `/**` sınırlayıcı olduğu beyaz boşluk, boşluk karakteri göz ardı edilir ve satırın geri kalanını işlenir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="f9c1d-114">Aksi takdirde, tüm metin satırının sonra `/**` sınırlayıcı açıklamayı bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="f9c1d-115">İçeren satırda `*/` varsa yalnızca boşluk kadar sınırlayıcı `*/` sınırlayıcı, o satırdaki göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="f9c1d-116">Aksi takdirde, en fazla bir satırındaki metin `*/` sınırlayıcı desen eşleştirme kuralları aşağıdaki maddede açıklandığı tabi açıklamayı bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="f9c1d-117">İle başlayan bir sonraki satırların için `/**` sınırlayıcı, derleyici her satırın başında yaygın bir düzen arar.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="f9c1d-118">Desen, isteğe bağlı beyaz boşluk ve yıldız oluşabilir (`*`) ve ardından daha fazla isteğe bağlı beyaz boşluk.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="f9c1d-119">Derleyici, ile başlamaz her satırın başında yaygın bir düzen bulursa `/**` sınırlayıcı veya `*/` sınırlayıcı, her satır için bu deseni yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="f9c1d-120">Aşağıdaki örnekler, bu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="f9c1d-121">Yalnızca işlenecek şu açıklama ile başlayan satırı parçasıdır `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="f9c1d-122">Üç etiket biçimlerini aynı açıklamaları üretir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="f9c1d-123">Derleyici ortak deseni tanımlayan "\*" ikinci ve üçüncü satır başında.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="f9c1d-124">Desen çıktısında dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="f9c1d-125">Üçüncü satır ikinci karakteri yıldız olmadığı için derleyici aşağıdaki açıklamada hiçbir ortak desenini bulur.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="f9c1d-126">Bu nedenle, tüm metin ikinci ve üçüncü satırlardaki açıklamayı bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="f9c1d-127">Derleyici, aşağıdaki açıklamada iki nedenden dolayı hiçbir desenini bulur.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="f9c1d-128">İlk olarak, yıldız işareti önce boşluk sayısını tutarlı değil.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="f9c1d-129">İkinci olarak, beşinci satır alanları eşleşmiyor bir sekme ile başlar.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="f9c1d-130">Bu nedenle, tüm beş aracılığıyla satırlarını iki metinden açıklamayı bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9c1d-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9c1d-131">See Also</span></span>

- [<span data-ttu-id="f9c1d-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9c1d-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f9c1d-133">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f9c1d-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
- [<span data-ttu-id="f9c1d-134">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f9c1d-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="f9c1d-135">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f9c1d-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
