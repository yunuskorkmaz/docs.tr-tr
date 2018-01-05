---
title: "Nasıl yapılır: .NET standart bir nesne seri hale getirilebilir olup olmadığını belirler"
description: "Çalışma zamanında .NET standart bir türü seri olup olmadığını belirlemek gösterilmiştir."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="bc4b6-103">Nasıl yapılır: .NET standart bir nesne seri hale getirilebilir olup olmadığını belirler</span><span class="sxs-lookup"><span data-stu-id="bc4b6-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="bc4b6-104">.NET standart türleri ve bu standart sürümüne uygun belirli .NET uygulamaları üzerinde mevcut olmalıdır üyeleri tanımlayan bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="bc4b6-105">Ancak, .NET standart bir türü seri hale getirilebilir olup olmadığını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="bc4b6-106">.NET standart Kitaplığı'nda tanımlanan türleri ile işaretlenmemiş <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="bc4b6-107">Bunun yerine, belirli .NET, .NET Framework ve .NET Core gibi belirli bir türü seri hale getirilebilir olup olmadığını belirlemek boş uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="bc4b6-108">Bir kitaplık hedefleyen .NET standart geliştirdik, kitaplığınızın .NET standardını destekleyen herhangi bir .NET uygulaması tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="bc4b6-109">Bu, önceden belirli bir türü seri hale getirilebilir olup olmadığını bilemezsiniz olduğunu anlamına gelir; yalnızca, çalışma zamanında seri hale getirilebilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="bc4b6-110">Değerini alarak nesneyi çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz <xref:System.Type.IsSerializable> özelliği bir <xref:System.Type> o nesnenin türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="bc4b6-111">Aşağıdaki örnek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-111">The following example provides one implementation.</span></span> <span data-ttu-id="bc4b6-112">Bunu tanımlayan bir `IsSerializable(Object)` gösterir genişletme yöntemi olup <xref:System.Object> örneği hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="bc4b6-113">Ardından, herhangi bir nesne, sıralanabilir ve aşağıdaki örnekte gösterildiği gibi geçerli .NET uygulaması seri olup olmadığını belirlemek amacıyla yöntemi geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bc4b6-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="bc4b6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc4b6-114">See also</span></span>

<span data-ttu-id="bc4b6-115">[İkili seri hale getirme](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="bc4b6-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="bc4b6-116"><xref:System.SerializableAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bc4b6-116"><xref:System.SerializableAttribute?displayProperty=fullName></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
