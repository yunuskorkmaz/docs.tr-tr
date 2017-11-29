---
title: "Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="d1e3b-102">Nasıl yapılır: Koleksiyon Başlatıcısı ile bir Sözlük Başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d1e3b-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="d1e3b-103">Bir < xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add* > yöntemi iki parametre, bir anahtar ve değer için bir alır.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="d1e3b-104">Başlatmak için bir < xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Ekle ' yöntemi, birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametrelerinin ayraçlar içinde alın.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e3b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1e3b-105">Example</span></span>  
 <span data-ttu-id="d1e3b-106">Aşağıdaki kod örneğinde, bir < xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName'.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="d1e3b-107">Her öğe koleksiyonunun ayraç iki çiftlerini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="d1e3b-108">Nesne Başlatıcısı en içteki köşeli parantez içine `StudentName`, ve Başlatıcı eklenecek anahtar/değer çifti için en dıştaki köşeli parantez içine `students` <xref:System.Collections.Generic.Dictionary\`2>.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="d1e3b-109">Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için ayraç içine alınır.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1e3b-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d1e3b-110">Compiling the Code</span></span>  
 <span data-ttu-id="d1e3b-111">Bu kodu çalıştırmak için kopyalayıp sınıfı içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1e3b-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="d1e3b-112">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll ve kullanarak bir başvuru içeriyor System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="d1e3b-113">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e3b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e3b-114">See Also</span></span>  
 [<span data-ttu-id="d1e3b-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d1e3b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d1e3b-116">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="d1e3b-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
