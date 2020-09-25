---
title: İki arabirimin üyelerini açıkça uygulama-C# Programlama Kılavuzu
description: Aynı üye adlarına sahip iki arabirimi açıkça uygulamayı ve her arabirime bu C# örneğinde ayrı bir uygulama vermenizi öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 18b1f9cfb1690d35c0bca0a3c79c1b80ae5dd44d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205093"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="85829-103">İki arabirimin üyelerini açıkça uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="85829-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="85829-104">Açık [arabirim](../../language-reference/keywords/interface.md) uygulaması Ayrıca, programcı 'nin aynı üye adlarına sahip iki arabirim uygulamasına ve her arabirime ayrı bir uygulama sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="85829-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="85829-105">Bu örnek, hem ölçüm hem de Ingilizce birimlerindeki bir kutunun boyutlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85829-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="85829-106">Box [sınıfı](../../language-reference/keywords/class.md) , farklı ölçü sistemlerini temsil eden iki arabirim olan IEnglishDimensions ve IMetricDimensions uygular.</span><span class="sxs-lookup"><span data-stu-id="85829-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="85829-107">Her iki arabirimde de aynı üye adları, uzunluğu ve genişliği vardır.</span><span class="sxs-lookup"><span data-stu-id="85829-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85829-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="85829-108">Example</span></span>  

 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="85829-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="85829-109">Robust Programming</span></span>  

 <span data-ttu-id="85829-110">Varsayılan ölçümleri Ingilizce birimlerde yapmak istiyorsanız, yöntem uzunluğunu ve genişliğini normal şekilde uygulayın ve IMetricDimensions arabiriminden length ve Width yöntemlerini açık bir şekilde uygulayın:</span><span class="sxs-lookup"><span data-stu-id="85829-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="85829-111">Bu durumda, sınıf örneğinden Ingilizce birimlere erişebilir ve arabirim örneğinden ölçüm birimlerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85829-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="85829-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85829-112">See also</span></span>

- [<span data-ttu-id="85829-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="85829-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="85829-114">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="85829-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="85829-115">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="85829-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="85829-116">Arabirim üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="85829-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
