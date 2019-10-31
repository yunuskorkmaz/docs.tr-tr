---
title: .NET Standard nesnenin seri hale getirilebilir olup olmadığını belirleme
description: .NET Standard türünün çalışma zamanında seri hale getirilebilir olup olmadığını nasıl belirleyecağınızı gösterir.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 87bf863b158fe3b2c03c7a6d23462bc2aabf9966
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106625"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="efc6e-103">.NET Standard nesnenin seri hale getirilebilir olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="efc6e-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="efc6e-104">.NET Standard, standart bu sürümü ile uyumlu olan belirli .NET uygulamalarında bulunması gereken türleri ve üyeleri tanımlayan bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="efc6e-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="efc6e-105">Ancak .NET Standard, bir türün seri hale getirilebilir olup olmadığını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="efc6e-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="efc6e-106">.NET Standard kitaplığı 'nda tanımlanan türler <xref:System.SerializableAttribute> özniteliğiyle işaretlenmez.</span><span class="sxs-lookup"><span data-stu-id="efc6e-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="efc6e-107">Bunun yerine, .NET Framework ve .NET Core gibi belirli .NET uygulamaları, belirli bir türün serileştirilebilir olup olmadığını belirlemekte ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="efc6e-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="efc6e-108">.NET Standard hedefleyen bir kitaplık geliştirdiyseniz, kitaplığınız .NET Standard destekleyen herhangi bir .NET uygulaması tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="efc6e-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="efc6e-109">Bu, belirli bir türün serileştirilebilir olup olmadığını önceden belirleyemeyeceğiniz anlamına gelir. çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efc6e-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="efc6e-110">Nesnenin türünü temsil eden bir <xref:System.Type> nesnesinin <xref:System.Type.IsSerializable> özelliğinin değerini alarak, bir nesnenin çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efc6e-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="efc6e-111">Aşağıdaki örnek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="efc6e-111">The following example provides one implementation.</span></span> <span data-ttu-id="efc6e-112">Herhangi bir <xref:System.Object> örneğinin seri hale getirilemeyeceğini belirten bir `IsSerializable(Object)` uzantısı yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efc6e-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="efc6e-113">Daha sonra aşağıdaki örnekte gösterildiği gibi, geçerli .NET uygulamasında seri hale getirilebilir ve seri durumdan çıkarılamayacağını öğrenmek için yöntemine herhangi bir nesne geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="efc6e-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="efc6e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efc6e-114">See also</span></span>

- [<span data-ttu-id="efc6e-115">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="efc6e-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
