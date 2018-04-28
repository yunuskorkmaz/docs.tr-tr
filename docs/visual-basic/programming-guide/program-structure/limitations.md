---
title: Visual Basic Sınırlamaları
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d06b743996969dcd7fc022bbb8ab625f3a151137
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="65ee7-102">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="65ee7-102">Visual Basic Limitations</span></span>
<span data-ttu-id="65ee7-103">Önceki sürümleri, Visual Basic değişken adları, modüller ve modül boyutu izin verilen değişken sayısı uzunluğu gibi kodda sınırları zorunlu.</span><span class="sxs-lookup"><span data-stu-id="65ee7-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="65ee7-104">Visual Basic .NET içinde bu kısıtlamalar, yazma ve düzenleme kodunuzu büyük özgürlüğünü rahat.</span><span class="sxs-lookup"><span data-stu-id="65ee7-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="65ee7-105">Fiziksel sınırları, çalışma zamanı bellek fazla derleme zamanı etmenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65ee7-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="65ee7-106">Akıllıca programlama uygulamalarını kullanırsanız ve büyük uygulamaların birden fazla sınıfları ve modülleri bölmek, dahili bir Visual Basic sınırlaması karşılaşmadan çok az ihtimalini yoktur.</span><span class="sxs-lookup"><span data-stu-id="65ee7-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="65ee7-107">Olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="65ee7-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="65ee7-108">**Ad uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="65ee7-108">**Name Length.**</span></span> <span data-ttu-id="65ee7-109">Bildirilen her programlama öğe adı için karakter sayısı üst yoktur.</span><span class="sxs-lookup"><span data-stu-id="65ee7-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="65ee7-110">Bu üst öğe adı tam tüm nitelik dizisi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="65ee7-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="65ee7-111">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="65ee7-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="65ee7-112">**Satır uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="65ee7-112">**Line Length.**</span></span> <span data-ttu-id="65ee7-113">En fazla kaynak kodunun fiziksel bir satırda 65535 karakterden yoktur.</span><span class="sxs-lookup"><span data-stu-id="65ee7-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="65ee7-114">Mantıksal kaynak kodu satır satır devamlılığı karakterleri kullanırsanız, daha uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="65ee7-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="65ee7-115">Bkz: [nasıl yapılır: kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="65ee7-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="65ee7-116">**Dizi boyutları.**</span><span class="sxs-lookup"><span data-stu-id="65ee7-116">**Array Dimensions.**</span></span> <span data-ttu-id="65ee7-117">Boyutlar için bir dizi bildirebilir sayısı üst yoktur.</span><span class="sxs-lookup"><span data-stu-id="65ee7-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="65ee7-118">Bu, bir dizi öğesine belirtmek için kullanabileceğiniz kaç dizinleri sınırlar.</span><span class="sxs-lookup"><span data-stu-id="65ee7-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="65ee7-119">Bkz: [dizi boyutları Visual Basic'te](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="65ee7-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="65ee7-120">**Dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="65ee7-120">**String Length.**</span></span> <span data-ttu-id="65ee7-121">Tek bir dize depolayabilir Unicode karakter sayısı üst yoktur.</span><span class="sxs-lookup"><span data-stu-id="65ee7-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="65ee7-122">Bkz: [dize veri türü](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="65ee7-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="65ee7-123">**Ortam dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="65ee7-123">**Environment String Length.**</span></span> <span data-ttu-id="65ee7-124">En çok bir komut satırı bağımsız değişken olarak kullanılan herhangi bir ortam dize için 32768 karakter var.</span><span class="sxs-lookup"><span data-stu-id="65ee7-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="65ee7-125">Bu tüm platformlarda kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="65ee7-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ee7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65ee7-126">See Also</span></span>  
 [<span data-ttu-id="65ee7-127">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="65ee7-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="65ee7-128">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="65ee7-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
