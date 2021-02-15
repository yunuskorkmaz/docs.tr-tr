---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic sınırlamaları'
title: Sınırlamalar
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 9182c5fe475e4350cb17ed3e4b734e3924bb9f7b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432851"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="a9941-103">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="a9941-103">Visual Basic Limitations</span></span>

<span data-ttu-id="a9941-104">Kodda, değişken adlarının uzunluğu, modüllerde izin verilen değişkenlerin sayısı ve modül boyutu gibi Visual Basic Zorlanmış sınırların daha eski sürümleri.</span><span class="sxs-lookup"><span data-stu-id="a9941-104">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="a9941-105">Visual Basic .NET sürümünde, bu kısıtlamalar gevşek bir şekilde, kodunuzu yazarken ve düzenleme konusunda daha fazla serbestlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9941-105">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="a9941-106">Fiziksel sınırlar, derleme zamanı önemli noktaları ile daha fazla çalışma zamanı belleğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a9941-106">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="a9941-107">Akıllıca programlama uygulamalarını kullanır ve büyük uygulamaları birden çok sınıfa ve modüle bölebilir, bir iç Visual Basic sınırlamasından kaçınmanın çok kısa bir olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-107">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="a9941-108">Aşağıda, olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a9941-108">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="a9941-109">**Ad uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="a9941-109">**Name Length.**</span></span> <span data-ttu-id="a9941-110">Her bir bildirilmeyen programlama öğesinin adı için en fazla karakter sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-110">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="a9941-111">Öğe adı nitelikli ise, bu en büyük bir nitelik dizesinin tamamına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a9941-111">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="a9941-112">Bkz. [tanımlanmış öğe adları](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a9941-112">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="a9941-113">**Satır uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="a9941-113">**Line Length.**</span></span> <span data-ttu-id="a9941-114">Kaynak kodunun fiziksel satırında en fazla 65535 karakter vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-114">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="a9941-115">Satır devamlılık karakterleri kullanırsanız mantıksal kaynak kodu satırı daha uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9941-115">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="a9941-116">Bkz. [nasıl yapılır: koddaki deyimleri kesme ve birleştirme](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="a9941-116">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="a9941-117">**Dizi boyutları.**</span><span class="sxs-lookup"><span data-stu-id="a9941-117">**Array Dimensions.**</span></span> <span data-ttu-id="a9941-118">Bir dizi için bildirebilen en fazla boyut sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-118">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="a9941-119">Bu, bir dizi öğesi belirtmek için kullanabileceğiniz dizin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="a9941-119">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="a9941-120">[Visual Basic 'de dizi boyutlarına](../language-features/arrays/array-dimensions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a9941-120">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="a9941-121">**Dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="a9941-121">**String Length.**</span></span> <span data-ttu-id="a9941-122">Tek bir dizede depolayabileceğiniz en fazla Unicode karakter sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-122">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="a9941-123">Bkz. [dize veri türü](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a9941-123">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="a9941-124">**Ortam dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="a9941-124">**Environment String Length.**</span></span> <span data-ttu-id="a9941-125">Komut satırı bağımsız değişkeni olarak kullanılan herhangi bir ortam dizesi için en fazla 32768 karakter vardır.</span><span class="sxs-lookup"><span data-stu-id="a9941-125">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="a9941-126">Bu, Tüm platformlardaki bir kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="a9941-126">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9941-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9941-127">See also</span></span>

- [<span data-ttu-id="a9941-128">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="a9941-128">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="a9941-129">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="a9941-129">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
