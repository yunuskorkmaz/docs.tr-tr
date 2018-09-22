---
title: .NET Standard nesnesinin serileştirilebilir olup olmadığını belirleme
description: Çalışma zamanında bir .NET Standard türü seri olup olmadığını belirlemek nasıl gösterir.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580466"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="42e19-103">.NET Standard nesnesinin serileştirilebilir olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="42e19-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="42e19-104">.NET Standard türleri ve bu standart sürümüne uygun belirli .NET uygulamaları üzerinde bulunması gereken üyeleri tanımlayan bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="42e19-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="42e19-105">Ancak, .NET Standard seri hale getirilebilir bir tür olup olmadığını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="42e19-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="42e19-106">.NET Standard Kitaplığı'nda tanımlanan türleri ile işaretlenmemiş <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="42e19-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="42e19-107">Bunun yerine, belirli .NET uygulamaları, .NET Framework ve .NET Core gibi belirli bir tür serileştirilebilir olup olmadığını belirlemek ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="42e19-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="42e19-108">Hedefleyen .NET Standard kitaplığı geliştirdiyseniz kitaplığınızı .NET Standard destekleyen herhangi bir .NET uygulaması tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42e19-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="42e19-109">Başka bir deyişle, önceden belirli bir türü seri hale getirilebilir olduğunu bildiğiniz olamaz; yalnızca, çalışma zamanında serileştirilebilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="42e19-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="42e19-110">Bir nesnenin değerini alarak çalışma zamanında serileştirilebilir olup olmadığını belirlemek <xref:System.Type.IsSerializable> özelliği bir <xref:System.Type> nesnenin türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="42e19-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="42e19-111">Aşağıdaki örnek, bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="42e19-111">The following example provides one implementation.</span></span> <span data-ttu-id="42e19-112">Tanımladığı bir `IsSerializable(Object)` gösteren bir genişletme yöntemi olmadığını <xref:System.Object> örneği seri hale getirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="42e19-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="42e19-113">Ardından, sıralanabilir ve geçerli .NET uygulaması aşağıdaki örnekte gösterildiği gibi seri durumdan olup olmadığını belirlemek için yöntemin herhangi bir nesne geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42e19-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="42e19-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42e19-114">See also</span></span>

- [<span data-ttu-id="42e19-115">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="42e19-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
