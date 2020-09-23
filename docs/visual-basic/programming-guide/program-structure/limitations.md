---
title: Sınırlamalar
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: abe4acd5850aa6065bf4f6fd41bc610ede7ad13f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097962"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="56e35-102">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="56e35-102">Visual Basic Limitations</span></span>

<span data-ttu-id="56e35-103">Kodda, değişken adlarının uzunluğu, modüllerde izin verilen değişkenlerin sayısı ve modül boyutu gibi Visual Basic Zorlanmış sınırların daha eski sürümleri.</span><span class="sxs-lookup"><span data-stu-id="56e35-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="56e35-104">Visual Basic .NET sürümünde, bu kısıtlamalar gevşek bir şekilde, kodunuzu yazarken ve düzenleme konusunda daha fazla serbestlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="56e35-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="56e35-105">Fiziksel sınırlar, derleme zamanı önemli noktaları ile daha fazla çalışma zamanı belleğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="56e35-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="56e35-106">Akıllıca programlama uygulamalarını kullanır ve büyük uygulamaları birden çok sınıfa ve modüle bölebilir, bir iç Visual Basic sınırlamasından kaçınmanın çok kısa bir olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="56e35-107">Aşağıda, olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="56e35-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="56e35-108">**Ad uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="56e35-108">**Name Length.**</span></span> <span data-ttu-id="56e35-109">Her bir bildirilmeyen programlama öğesinin adı için en fazla karakter sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="56e35-110">Öğe adı nitelikli ise, bu en büyük bir nitelik dizesinin tamamına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="56e35-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="56e35-111">Bkz. [tanımlanmış öğe adları](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="56e35-111">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="56e35-112">**Satır uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="56e35-112">**Line Length.**</span></span> <span data-ttu-id="56e35-113">Kaynak kodunun fiziksel satırında en fazla 65535 karakter vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="56e35-114">Satır devamlılık karakterleri kullanırsanız mantıksal kaynak kodu satırı daha uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="56e35-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="56e35-115">Bkz. [nasıl yapılır: koddaki deyimleri kesme ve birleştirme](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="56e35-115">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="56e35-116">**Dizi boyutları.**</span><span class="sxs-lookup"><span data-stu-id="56e35-116">**Array Dimensions.**</span></span> <span data-ttu-id="56e35-117">Bir dizi için bildirebilen en fazla boyut sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="56e35-118">Bu, bir dizi öğesi belirtmek için kullanabileceğiniz dizin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="56e35-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="56e35-119">[Visual Basic 'de dizi boyutlarına](../language-features/arrays/array-dimensions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="56e35-119">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="56e35-120">**Dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="56e35-120">**String Length.**</span></span> <span data-ttu-id="56e35-121">Tek bir dizede depolayabileceğiniz en fazla Unicode karakter sayısı vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="56e35-122">Bkz. [dize veri türü](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="56e35-122">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="56e35-123">**Ortam dize uzunluğu.**</span><span class="sxs-lookup"><span data-stu-id="56e35-123">**Environment String Length.**</span></span> <span data-ttu-id="56e35-124">Komut satırı bağımsız değişkeni olarak kullanılan herhangi bir ortam dizesi için en fazla 32768 karakter vardır.</span><span class="sxs-lookup"><span data-stu-id="56e35-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="56e35-125">Bu, Tüm platformlardaki bir kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="56e35-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e35-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56e35-126">See also</span></span>

- [<span data-ttu-id="56e35-127">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="56e35-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="56e35-128">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="56e35-128">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
