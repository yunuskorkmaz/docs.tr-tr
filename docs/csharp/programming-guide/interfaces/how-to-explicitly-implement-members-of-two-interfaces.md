---
title: 'Nasıl yapılır: Iki arabirimin üyelerini açıkça uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 1d4dd0485be1d859e3e9594ab1558a907b8f1f7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589200"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="1ecdb-102">Nasıl yapılır: Iki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1ecdb-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="1ecdb-103">Açık [arabirim](../../language-reference/keywords/interface.md) uygulaması Ayrıca, programcı 'nin aynı üye adlarına sahip iki arabirim uygulamasına ve her arabirime ayrı bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="1ecdb-104">Bu örnek, hem ölçüm hem de Ingilizce birimlerindeki bir kutunun boyutlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="1ecdb-105">Box [sınıfı](../../language-reference/keywords/class.md) , farklı ölçü sistemlerini temsil eden iki arabirim olan IEnglishDimensions ve IMetricDimensions uygular.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="1ecdb-106">Her iki arabirimde de aynı üye adları, uzunluğu ve genişliği vardır.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ecdb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ecdb-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1ecdb-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1ecdb-108">Robust Programming</span></span>  
 <span data-ttu-id="1ecdb-109">Varsayılan ölçümleri Ingilizce birimlerde yapmak istiyorsanız, yöntem uzunluğunu ve genişliğini normal şekilde uygulayın ve IMetricDimensions arabiriminden length ve Width yöntemlerini açık bir şekilde uygulayın:</span><span class="sxs-lookup"><span data-stu-id="1ecdb-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="1ecdb-110">Bu durumda, sınıf örneğinden Ingilizce birimlere erişebilir ve arabirim örneğinden ölçüm birimlerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ecdb-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1ecdb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-111">See also</span></span>

- [<span data-ttu-id="1ecdb-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1ecdb-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1ecdb-113">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="1ecdb-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1ecdb-114">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1ecdb-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1ecdb-115">Nasıl yapılır: Arabirim üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="1ecdb-115">How to: Explicitly Implement Interface Members</span></span>](./how-to-explicitly-implement-interface-members.md)
