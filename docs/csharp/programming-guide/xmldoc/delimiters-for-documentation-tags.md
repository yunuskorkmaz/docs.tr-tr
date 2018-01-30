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
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="f0957-102">Belge Etiketleri için Sınırlayıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f0957-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="f0957-103">XML belge açıklamaları kullanılmasını burada belgelerine yorum başlar ve biter derleyici belirtmek sınırlayıcıları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f0957-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="f0957-104">XML belgeleri etiketlerle sınırlayıcıları şu tür kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f0957-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="f0957-105">Tek satırlı sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0957-105">Single-line delimiter.</span></span> <span data-ttu-id="f0957-106">Bu belge örneklerde gösterilen ve Visual C# proje şablonları tarafından kullanılan formdur.</span><span class="sxs-lookup"><span data-stu-id="f0957-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="f0957-107">Sınırlayıcı izleyen bir boşluk karakteri varsa, bu karakterin XML çıktısında dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f0957-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0957-108">Visual Studio IDE akıllı açıklama otomatik olarak ekleyen düzenleme adlı bir özelliği olan \<Özet > ve \</Özet > etiketleri ve yazdıktan sonra imleci bu etiketlerde taşır `///` sınırlayıcı Kod Düzenleyicisi'nde .</span><span class="sxs-lookup"><span data-stu-id="f0957-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="f0957-109">Bu özellik üzerinde veya kapatabilirsiniz [Seçenekler iletişim kutusu](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="f0957-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="f0957-110">Çok satırlı sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0957-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="f0957-111">Kullandığınızda izlemek için biçimlendirme bazı kurallar vardır `/** */` sınırlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0957-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="f0957-112">İçeren satırı üzerinde `/**` kalan satırının satır boşluk ise sınırlayıcı açıklamaları için işlenmedi.</span><span class="sxs-lookup"><span data-stu-id="f0957-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="f0957-113">Varsa sonra ilk karakter `/**` sınırlayıcısı olan beyaz boşluk karakteri göz ardı edilir ve satır kalan işlenen alan.</span><span class="sxs-lookup"><span data-stu-id="f0957-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="f0957-114">Aksi takdirde satırından sonra tüm metnin `/**` sınırlayıcı yorum bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f0957-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="f0957-115">İçeren satırı üzerinde `*/` varsa yalnızca boşluk kadar sınırlayıcı `*/` sınırlayıcısı, o satırdaki göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f0957-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="f0957-116">Aksi takdirde kadar satırındaki metin `*/` sınırlayıcı aşağıdaki maddede açıklandığı desen eşleştirme kuralları tabi yorum bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f0957-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="f0957-117">İle başlayan bir sonraki satırların için `/**` sınırlayıcısı, derleyicinin her satırın başındaki genel bir desen arar.</span><span class="sxs-lookup"><span data-stu-id="f0957-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="f0957-118">Desen isteğe bağlı boşluk ve bir yıldız işareti içerebilir (`*`), ardından daha fazla isteğe bağlı boşluk.</span><span class="sxs-lookup"><span data-stu-id="f0957-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="f0957-119">Derleyici ile başlamayan her satırın başındaki ortak bir deseni bulursa `/**` sınırlayıcı veya `*/` sınırlayıcısı, her satır için bu deseni yok sayar.</span><span class="sxs-lookup"><span data-stu-id="f0957-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="f0957-120">Aşağıdaki örnekler, bu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0957-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="f0957-121">Yalnızca nasıl işleneceğini aşağıdaki açıklama ile başlayan satırı parçasıdır `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="f0957-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="f0957-122">Üç etiket biçimlerini aynı açıklamaları üretir.</span><span class="sxs-lookup"><span data-stu-id="f0957-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="f0957-123">Derleyici, genel bir desen tanımlar "\*" ikinci ve üçüncü satır başında.</span><span class="sxs-lookup"><span data-stu-id="f0957-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="f0957-124">Desen çıktıda dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f0957-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="f0957-125">Üçüncü satır ikinci karakteri bir yıldız işareti olmadığından derleyici hiçbir ortak desen aşağıdaki açıklamada bulur.</span><span class="sxs-lookup"><span data-stu-id="f0957-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="f0957-126">Bu nedenle, ikinci ve üçüncü satırlarındaki tüm metni yorum bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f0957-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="f0957-127">Derleyici hiçbir desen aşağıdaki açıklamada iki nedenden dolayı bulur.</span><span class="sxs-lookup"><span data-stu-id="f0957-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="f0957-128">İlk olarak, yıldız işareti önce boşluk sayısını tutarlı değil.</span><span class="sxs-lookup"><span data-stu-id="f0957-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="f0957-129">İkinci olarak, beşinci satır alanları eşleşmiyor bir sekme ile başlar.</span><span class="sxs-lookup"><span data-stu-id="f0957-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="f0957-130">Bu nedenle, tüm metinden satırları iki beş aracılığıyla açıklama bir parçası olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f0957-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f0957-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0957-131">See Also</span></span>  
 [<span data-ttu-id="f0957-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f0957-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f0957-133">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f0957-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="f0957-134">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f0957-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="f0957-135">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="f0957-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
