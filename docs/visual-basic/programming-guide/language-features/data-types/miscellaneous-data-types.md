---
description: 'Hakkında daha fazla bilgi edinin: çeşitli veri türleri (Visual Basic)'
title: Çeşitli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 3875a3fc3027d573013470cb96c9482a0be6cbbf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462002"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="a3894-103">Çeşitli Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3894-103">Miscellaneous Data Types (Visual Basic)</span></span>

<span data-ttu-id="a3894-104">Visual Basic, sayı veya karakterlere yönelik olmayan çeşitli veri türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3894-104">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="a3894-105">Bunun yerine, Evet/Hayır değerleri, tarih/saat değerleri ve nesne adresleri gibi özelleşmiş verilerle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="a3894-105">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="a3894-106">Visual Basic veri türlerinin yan yana karşılaştırmasını gösteren bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3894-106">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="a3894-107">Boole türü</span><span class="sxs-lookup"><span data-stu-id="a3894-107">Boolean Type</span></span>  

 <span data-ttu-id="a3894-108">[Boolean veri türü](../../../language-reference/data-types/boolean-data-type.md) veya olarak yorumlanan işaretsiz bir değerdir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="a3894-108">The [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="a3894-109">Veri genişliği, uygulama platformuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a3894-109">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="a3894-110">Bir değişken yalnızca doğru/yanlış, Evet/Hayır veya açık/kapalı gibi yalnızca iki durumlu değerler içeriyorsa, olarak bildirin `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a3894-110">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="a3894-111">Tarih türü</span><span class="sxs-lookup"><span data-stu-id="a3894-111">Date Type</span></span>  

 <span data-ttu-id="a3894-112">[Tarih veri türü](../../../language-reference/data-types/date-data-type.md) , hem tarih hem de saat bilgilerini tutan 64 bitlik bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="a3894-112">The [Date Data Type](../../../language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="a3894-113">Her artış, Gregoryen takvimdeki 1 Ocak 100 ' den (12:00) itibaren geçen sürenin nanosaniye süresini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3894-113">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="a3894-114">Bir değişken bir tarih değeri, saat değeri veya her ikisi de içeriyorsa, olarak bildirin `Date` .</span><span class="sxs-lookup"><span data-stu-id="a3894-114">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="a3894-115">Nesne Türü</span><span class="sxs-lookup"><span data-stu-id="a3894-115">Object Type</span></span>  

 <span data-ttu-id="a3894-116">[Nesne veri türü](../../../language-reference/data-types/object-data-type.md) , uygulamanızdaki bir nesne örneğine veya başka bir uygulamaya işaret eden 32 bitlik bir adrestir.</span><span class="sxs-lookup"><span data-stu-id="a3894-116">The [Object Data Type](../../../language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="a3894-117">Bir `Object` değişken, uygulamanızın tanıdığı herhangi bir nesneye veya herhangi bir veri türünün verilerine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="a3894-117">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="a3894-118">Bu,, ve yapı örnekleri gibi *değer türlerini* ve, ve `Integer` `Boolean` dizi örnekleri gibi sınıflardan oluşturulan nesne örnekleri olan *başvuru türlerini* içerir `String` <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="a3894-118">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="a3894-119">Bir değişken, derleme zamanında tanımadığınız bir sınıfın örneğine bir işaretçi depolarsa veya çeşitli veri türlerindeki verileri işaret edebilir, olarak bildirin `Object` .</span><span class="sxs-lookup"><span data-stu-id="a3894-119">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="a3894-120">Veri türünün avantajı, `Object` herhangi bir veri türünün verilerini depolamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3894-120">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="a3894-121">Dezavantajı, daha fazla yürütme süresi alan ve uygulamanızı daha yavaş hale getirebilmeniz için ek işlemlere neden olur.</span><span class="sxs-lookup"><span data-stu-id="a3894-121">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="a3894-122">`Object`Değer türleri için bir değişken kullanırsanız, *kutulama* ve *kutudan* çıkarma uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a3894-122">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="a3894-123">Bunu başvuru türleri için kullanıyorsanız, *geç bağlamaya* tabi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a3894-123">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3894-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3894-124">See also</span></span>

- [<span data-ttu-id="a3894-125">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="a3894-125">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="a3894-126">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a3894-126">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="a3894-127">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a3894-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="a3894-128">Karakter Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a3894-128">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="a3894-129">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="a3894-129">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a3894-130">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="a3894-130">Early and Late Binding</span></span>](../early-late-binding/index.md)
