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
ms.openlocfilehash: 9f7ab8a824b9687f68382a5edc342536289c5d09
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282331"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="9839f-103">.NET Standard nesnenin seri hale getirilebilir olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="9839f-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="9839f-104">.NET Standard, standart bu sürümü ile uyumlu olan belirli .NET uygulamalarında bulunması gereken türleri ve üyeleri tanımlayan bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="9839f-104">.NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="9839f-105">Ancak, .NET Standard bir türün seri hale getirilebilir olup olmadığını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9839f-105">However, .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="9839f-106">.NET Standard kitaplığı 'nda tanımlanan türler <xref:System.SerializableAttribute> özniteliğiyle işaretlenmez.</span><span class="sxs-lookup"><span data-stu-id="9839f-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="9839f-107">Bunun yerine, .NET Framework ve .NET Core gibi belirli .NET uygulamaları, belirli bir türün serileştirilebilir olup olmadığını belirlemede ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="9839f-107">Instead, specific .NET implementations, such as .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="9839f-108">.NET Standard hedefleyen bir kitaplık geliştirdiyseniz, kitaplığınız .NET Standard destekleyen herhangi bir .NET uygulaması tarafından tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="9839f-108">If you've developed a library that targets .NET Standard, your library can be consumed by any .NET implementation that supports .NET Standard.</span></span> <span data-ttu-id="9839f-109">Bu, belirli bir türün serileştirilebilir olup olmadığını önceden belirleyemeyeceğiniz anlamına gelir. çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9839f-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="9839f-110">Nesnenin <xref:System.Type.IsSerializable> <xref:System.Type> türünü temsil eden nesnenin özelliğinin değerini alarak, bir nesnenin çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9839f-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="9839f-111">Aşağıdaki örnek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="9839f-111">The following example provides one implementation.</span></span> <span data-ttu-id="9839f-112">`IsSerializable(Object)`Herhangi bir örneğin seri hale getirilemeyeceğini belirten bir genişletme yöntemi tanımlar <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="9839f-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="9839f-113">Daha sonra aşağıdaki örnekte gösterildiği gibi, geçerli .NET uygulamasında seri hale getirilebilir ve seri durumdan çıkarılamayacağını öğrenmek için yöntemine herhangi bir nesne geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9839f-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9839f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9839f-114">See also</span></span>

- [<span data-ttu-id="9839f-115">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="9839f-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
