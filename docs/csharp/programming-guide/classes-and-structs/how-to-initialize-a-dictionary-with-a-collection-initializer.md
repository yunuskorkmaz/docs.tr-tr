---
title: "Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="30f0f-102">Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="30f0f-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="30f0f-103">A <xref:System.Collections.Generic.Dictionary`2> anahtar/değer çiftleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="30f0f-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs.</span></span> <span data-ttu-id="30f0f-104">Kendi <xref:System.Collections.Generic.Dictionary`2.Add*> yöntemi iki parametre, bir anahtar ve değer için bir alır.</span><span class="sxs-lookup"><span data-stu-id="30f0f-104">Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="30f0f-105">Başlatmak için bir <xref:System.Collections.Generic.Dictionary`2>, ya da herhangi bir koleksiyonu olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametrelerinin ayraçlar içinde alın.</span><span class="sxs-lookup"><span data-stu-id="30f0f-105">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f0f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="30f0f-106">Example</span></span>  
 <span data-ttu-id="30f0f-107">Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary`2> türü örnekleri ile başlatılmış `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="30f0f-107">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="30f0f-108">Her öğe koleksiyonunun ayraç iki çiftlerini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="30f0f-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="30f0f-109">Nesne Başlatıcısı en içteki köşeli parantez içine `StudentName`, ve Başlatıcı eklenecek anahtar/değer çifti için en dıştaki köşeli parantez içine `students` <xref:System.Collections.Generic.Dictionary`2>.</span><span class="sxs-lookup"><span data-stu-id="30f0f-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="30f0f-110">Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için ayraç içine alınır.</span><span class="sxs-lookup"><span data-stu-id="30f0f-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="30f0f-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="30f0f-111">Compiling the Code</span></span>  
 <span data-ttu-id="30f0f-112">Bu kodu çalıştırmak için kopyalayıp sınıfı içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30f0f-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="30f0f-113">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll ve kullanarak bir başvuru içeriyor System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="30f0f-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="30f0f-114">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30f0f-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f0f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30f0f-115">See Also</span></span>  
 [<span data-ttu-id="30f0f-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="30f0f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30f0f-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="30f0f-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
